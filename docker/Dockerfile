FROM python:3.6-alpine

RUN apk add --update --no-cache \
    gcc g++ postgresql-dev && \
    pip install dumb-init

ENV PY_ENV=production

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
RUN python manage.py collectstatic
VOLUME /app/collected-static
ENTRYPOINT ["/usr/local/bin/dumb-init", "--"]