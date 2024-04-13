# spin-o11y
Spin Observability experiment

```sh
spin --version
spin 2.4.2 (340378e 2024-04-03)
```

## With .NET Aspire

```sh
> docker run --rm -it -p 18888:18888 -p 4317:18889 --name aspire-dashboard -e DOTNET_DASHBOARD_UNSECURED_ALLOW_ANONYMOUS='true' mcr.microsoft.com/dotnet/nightly/aspire-dashboard:8.0.0-preview.5
```

```sh
> $env:OTEL_EXPORTER_OTLP_ENDPOINT= 'http://localhost:4317'; $env:DOTNET_RESOURCE_SERVICE_ENDPOINT_URL = "service-a"; spin up
```

Not worked: https://github.com/dotnet/aspire/issues/3674

## With Jeager

```sh
> docker run -d -p16686:16686 -p4317:4317 -p4318:4318 -e COLLECTOR_OTLP_ENABLED=true jaegertracing/all-in-one:latest
```

```sh
> $env:OTEL_EXPORTER_OTLP_ENDPOINT= 'http://localhost:4318'; $env:DOTNET_RESOURCE_SERVICE_ENDPOINT_URL = "service-a"; spin up 
```

## Refs:
- https://developer.fermyon.com/spin/v2/observing-apps#opentelemetry-otel
- https://github.com/christophwille/OTel-de-Wille
- https://anthonysimmon.com/dotnet-aspire-dashboard-best-tool-visualize-opentelemetry-local-dev/
