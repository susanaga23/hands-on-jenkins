FROM alpine:3.19

WORKDIR /usr/src/app

# Python + pip + venv
RUN apk add --no-cache python3 py3-pip py3-virtualenv

# Crea venv e instala deps ahí
COPY requirements.txt .
RUN python3 -m venv /opt/venv \
 && /opt/venv/bin/pip install --upgrade pip setuptools wheel \
 && /opt/venv/bin/pip install --no-cache-dir -r requirements.txt

# Usa el venv por defecto
ENV PATH="/opt/venv/bin:$PATH"

COPY app.py .
COPY templates/index.html ./templates/

EXPOSE 5000
CMD ["python", "app.py"]

