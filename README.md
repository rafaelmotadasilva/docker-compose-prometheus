<h1>
    <img align="center" width="40px" src="./docker-mark-blue.svg" alt="Docker logo">
    <span>Criando um Docker Compose do Prometheus e o Grafana</span>
</h1>

Repositório desenvolvido para fins educativos.

## Objetivo

Criar um Docker Compose para executar o Prometheus e o Grafana para realizar as seguintes tarefas:

- Mapear um volume para o banco de dados

- Expor a porta da interface web do Prometheus

- Expor a porta do Grafana

### A configuração devera ter os seguintes contêineres:

- Prometheus

- grafana

## Exemplo de Docker Compose

```
version: '3.8'

services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    ports:
      - "9090:9090"
    volumes:
      - prometheus_data:/prometheus
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    restart: unless-stopped

  grafana:
    image: grafana/grafana:latest
    container_name: grafana
    ports:
      - "3000:3000"
    restart: unless-stopped

volumes:
  prometheus_data:
```

## Estrutura do projeto

Certifique-se de que o projeto tenha a seguinte estrutura:

```
.
├── docker-compose.yml
├── prometheus.yml
```

## Instruções do Docker Compose

### Execute o contêiner

No diretório onde estão os arquivos prometheus.yml e o docker-compose.yml, execute:

```
sudo docker-compose up -d
```