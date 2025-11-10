````markdown
# Monitoring Automation with Ansible (Prometheus + Grafana)

Automate the deployment of a complete **Prometheus** and **Grafana** monitoring stack using **Ansible**.  
This project simplifies the setup of system monitoring and visualization across multiple servers.

---

## 📘 Overview

This repository contains Ansible playbooks and roles to:

- Deploy and configure **Prometheus** for metrics collection  
- Deploy and configure **Grafana** for data visualization  
- Automate service installation, configuration, and startup  
- Simplify monitoring setup on Debian/RedHat-based systems

---

## ⚙️ Features

- 🔹 Fully automated installation of Prometheus and Grafana  
- 🔹 Role-based structure (reusable and modular)  
- 🔹 Inventory file for defining target hosts  
- 🔹 Easy customization via variables  
- 🔹 Works on major Linux distributions (Ubuntu, Debian, CentOS, RHEL)

---

## 🧰 Prerequisites

Before running the playbooks, make sure you have:

- A **control node** with Ansible installed  
- **Target hosts** (Linux servers) accessible via SSH  
- `sudo` privileges on the managed hosts  
- Python installed on all target machines  

To install Ansible on the control node:

```bash
sudo apt update -y
sudo apt install ansible -y
````

---

## 📁 Directory Structure

```
monitoring-ansible/
├── hosts.ini            # Inventory file (define your servers)
├── playbook.yml         # Main playbook for Prometheus + Grafana
├── roles/
│   ├── prometheus/      # Prometheus installation and configuration
│   └── grafana/         # Grafana installation and configuration
└── README.md
```

---

## 🧾 Inventory Example

Edit the `hosts.ini` file and define your servers:

```ini
[prometheus]
prometheus-server ansible_host=192.168.1.10 ansible_user=ubuntu

[grafana]
grafana-server ansible_host=192.168.1.11 ansible_user=ubuntu
```

---

## 🚀 How to Run

Run the Ansible playbook to deploy both services:

```bash
ansible-playbook -i hosts.ini playbook.yml
```

If you want to deploy only Prometheus or Grafana:

```bash
ansible-playbook -i hosts.ini playbook.yml --tags prometheus
ansible-playbook -i hosts.ini playbook.yml --tags grafana
```

---

## 📊 Access the Monitoring Stack

After the playbook completes:

* **Prometheus:** http://<your-prometheus-server-ip>:9090
* **Grafana:** http://<your-grafana-server-ip>:3000

  * Default Login:

    * **Username:** `admin`
    * **Password:** `admin`

---

## ⚡ Customization

You can modify variables inside each role (under `roles/prometheus/vars` or `roles/grafana/vars`) to:

* Change installation paths
* Define data directories
* Configure Grafana dashboards and Prometheus scrape targets

Example (`roles/prometheus/vars/main.yml`):

```yaml
prometheus_version: "2.55.0"
prometheus_port: 9090
```

Example (`roles/grafana/vars/main.yml`):

```yaml
grafana_version: "11.0.0"
grafana_port: 3000
```

---

## 🧪 Testing the Deployment

Use the `--check` flag for a dry run:

```bash
ansible-playbook -i hosts.ini playbook.yml --check
```

To limit execution to a single host:

```bash
ansible-playbook -i hosts.ini playbook.yml --limit grafana-server
```

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-change`)
3. Commit your changes
4. Push and open a pull request

---

## 🪪 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

### 💡 Author

**Rohit Boghara**
📦 [GitHub Repository](https://github.com/rohitboghara/monitoring-ansible)

---

```

---

Would you like me to include **installation steps for Prometheus and Grafana** (the exact shell/Ansible tasks your playbook runs) in the README too — e.g., to show what commands are automated under the hood?  
That can make your README more educational for others using your repo.
```
