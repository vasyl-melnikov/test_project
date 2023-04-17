FROM python:3.9.13-alpine

RUN addgroup app

RUN adduser -S -G app -H app

RUN apk add --no-cache --update python3-dev gcc build-base

RUN /usr/local/bin/python -m pip install --upgrade pip

COPY .. /app

WORKDIR /app

RUN pip install -r requirements.txt

RUN chown -R app:app /app

USER app

CMD ["/usr/local/bin/gunicorn", "-w", "1", "-b", ":3000", "main:app"]
