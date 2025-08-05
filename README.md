# 🚀 Enterprise OpenSSL Certification Authority

A sovereign, modern, and developer-friendly Certificate Authority (CA) stack inspired by OpenSSL, maintained by **Sky Genesis Enterprise**.

> ⚠️ This project is **not affiliated** with the official [OpenSSL Project](https://www.openssl.org).  
> It is an **internal and open-source initiative** to provide a secure, controllable, and extensible PKI platform for enterprise environments.

---

## 🌐 About

**Enterprise OpenSSL CA** is a trusted PKI infrastructure developed and maintained by Sky Genesis Enterprise.  
It provides a modern CLI and server-side CA for issuing, managing, and revoking X.509 certificates, backed by cryptographic best practices.

This project is the foundation for securing:

- Internal services and APIs
- Artemis agents and dashboard
- Client mutual TLS (mTLS) authentication
- Software artifacts (Docker, mobile apps, etc.)
- Secure VPNs and SSH certificate-based auth

---

## 🛠️ Features

- ✅ Root & Intermediate CA generation
- 🔐 Certificate issuance & revocation
- 🔄 Auto-renewal support
- 🧩 Policy control for expiration, usage, SAN, etc.
- 📜 ACME-like and OIDC provisioning (optional)
- 🖥️ CLI `openssl` tool (custom binary)
- 📦 Docker-ready, DevOps-compatible
- 📈 Certificate lifecycle monitoring (integrates with Artemis)

---

## 📦 Installation

We strongly recommend installing only from our **official endpoint**:

```bash
wget -qO- https://ssl.skygenesisenterprise.com/install.sh | bash
```

This script:

* Downloads and verifies the official `openssl` CLI binary
* Configures your system with trusted defaults
* Optionally bootstraps a local Root CA

> Do **not** install this binary from unofficial mirrors. Use only the trusted source.

---

## 🚀 Quickstart

```bash
# Initialize a local CA (root + intermediate)
openssl gen-ca --name "SGE Root CA" --out ./ca/

# Issue a TLS certificate
openssl gen-cert --cn "api.mycompany.cloud" --days 365 --out ./certs/

# Revoke a certificate
openssl revoke --serial 01ABC3F --reason "compromised"

# View active certs
openssl list --status valid
```

---

## 🧪 Development

This CLI is built in Go and inspired by [Smallstep](https://github.com/smallstep/certificates).
We maintain a fork of the original Smallstep CA, with internal enhancements and integration into the **Sky Genesis infrastructure**.

> Contributions are welcome for compatible tooling, wrappers, and deployment modules.

---

## 🔐 Security Notes

* All binaries are signed and versioned
* Certificate authority policies are configurable via `policy.yaml`
* Integration with HSM, Vault or TPM is available
* CLI includes a self-check to ensure it was installed from a trusted source

---

## 🙋 FAQ

### > Is this a fork of OpenSSL?

No. This project does not use or redistribute OpenSSL C libraries. It is a **modern Go-based PKI stack**, conceptually inspired by OpenSSL’s tooling and CLI patterns.

### > Can I use this in production?

Yes – but only after reviewing the CA policies and performing your own security audits. The system is designed for **enterprise-grade deployments**, including on-prem, air-gapped, and cloud-native setups.

### > Can I replace Let's Encrypt or my internal CA with this?

Absolutely. The system supports issuing server, client, and code-signing certificates. You can also integrate it with DevOps pipelines via REST API, CLI, or Terraform modules.

---

## 📫 Contact

For commercial inquiries, integration requests, or enterprise support, contact:

```
Sky Genesis Enterprise  
security@skygenesisenterprise.com  
https://skygenesisenterprise.com
```

## 📝 License

This project is licensed under the **MIT License**.

© Sky Genesis Enterprise. All rights reserved.