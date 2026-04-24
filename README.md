<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://systemprompt.io/files/images/logo.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://systemprompt.io/files/images/logo-dark.svg">
  <img src="https://systemprompt.io/files/images/logo-dark.svg" alt="systemprompt.io" width="320">
</picture>

# systempromptio/charts

**Helm chart repository for the systemprompt AI governance gateway.**

Served at [`charts.systemprompt.io`](https://charts.systemprompt.io). Indexed on [Artifact Hub](https://artifacthub.io/packages/search?repo=systemprompt).

The governance layer for AI agents — a single compiled Rust binary that authenticates, authorises, rate-limits, logs, and costs every AI interaction. Self-hosted, air-gap capable, provider-agnostic.

[**systemprompt.io**](https://systemprompt.io) · [**Documentation**](https://systemprompt.io/documentation/) · [**Main repo**](https://github.com/systempromptio/systemprompt-template) · [**Discord**](https://discord.gg/wkAbSuPWpr)

[![Template · MIT](https://img.shields.io/badge/template-MIT-16a34a?style=flat-square)](https://github.com/systempromptio/systemprompt-template/blob/main/LICENSE)
[![Core · BSL--1.1](https://img.shields.io/badge/core-BSL--1.1-2b6cb0?style=flat-square)](https://github.com/systempromptio/systemprompt-core/blob/main/LICENSE)

</div>

---

## Install

```bash
helm repo add systemprompt https://charts.systemprompt.io
helm repo update

helm install gateway systemprompt/gateway \
  --set secrets.anthropicApiKey=sk-ant-... \
  --set postgresql.auth.password=<strong-pw>
```

Full install + HA configuration: [systemprompt-template/docs/install/helm.md](https://github.com/systempromptio/systemprompt-template/blob/main/docs/install/helm.md).

## Charts

| Chart | Description |
|---|---|
| [`gateway`](https://github.com/systempromptio/systemprompt-template/tree/main/helm/gateway) | systemprompt AI governance gateway + optional Postgres |

Chart source lives in the main repo at `helm/gateway/`. This repo just serves the packaged `.tgz` releases.

## Signed charts

Every chart release is signed via Sigstore cosign. Verify before install:

```bash
cosign verify-blob \
  --certificate-identity-regexp='https://github.com/systempromptio/charts/' \
  --certificate-oidc-issuer='https://token.actions.githubusercontent.com' \
  --signature gateway-<version>.tgz.sig \
  gateway-<version>.tgz
```

## Licence

Chart source: MIT. Compiled image: `MIT AND BUSL-1.1` — template code is [MIT](https://github.com/systempromptio/systemprompt-template/blob/main/LICENSE); the compiled binary links `systemprompt-core` which is [BSL-1.1](https://github.com/systempromptio/systemprompt-core/blob/main/LICENSE).
