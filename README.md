# Ansible Project - Ollama Deployment

This Ansible project is designed to automate the deployment and configuration of the Ollama application across your infrastructure. The project is structured to follow best practices, making it easy to manage and extend.

## Project Structure

```plaintext
.
├── ansible.cfg
├── group_vars
│   └── all.yml
├── inventory
│   └── hosts
├── ollama.yml
└── roles
    └── ollama
        ├── defaults
        │   └── main.yml
        ├── handlers
        │   └── main.yml
        ├── meta
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        └── vars
            └── main.yml
```

### File and Directory Descriptions

- **`ansible.cfg`**: Configuration file for Ansible. This file defines the behavior of Ansible, such as inventory location, roles path, and other configuration parameters.
  
- **`group_vars/`**: This directory contains variable files that are applied to all hosts or specific groups of hosts. The `all.yml` file defines variables that are common across all hosts.

- **`inventory/hosts`**: The inventory file that lists all the hosts where the playbooks will be executed. You can define hosts or groups of hosts here.

- **`ollama.yml`**: The main playbook that includes all the tasks to deploy and configure Ollama. This playbook calls the necessary roles and tasks defined in the `roles/ollama` directory.

- **`roles/ollama/`**: This directory contains the role for deploying and configuring Ollama. Roles in Ansible are self-contained units of automation that can be easily reused.

  - **`defaults/main.yml`**: Default variables for the Ollama role. These variables can be overridden by variables defined in `vars/main.yml` or other variable files.
  
  - **`handlers/main.yml`**: Handlers are used to trigger actions based on task results, such as restarting a service after a configuration change.
  
  - **`meta/main.yml`**: Metadata about the Ollama role, such as its dependencies on other roles.
  
  - **`tasks/main.yml`**: The main list of tasks to be executed for the Ollama role. This file defines the sequence of operations needed to deploy and configure Ollama.
  
  - **`vars/main.yml`**: Variables specific to the Ollama role. These variables are used to configure the tasks within the role.

## Usage

### Prerequisites

- Ensure you have Ansible installed on your control machine.
- Update the `inventory/hosts` file with the appropriate hostnames or IP addresses of the target machines.

### Running the Playbook

To run the main playbook and deploy Ollama, use the following command:

```bash
ansible-playbook ollama.yml
```

This command will execute the tasks defined in the `ollama.yml` playbook on the hosts specified in the inventory.

### Customization

- **Variables**: You can customize the deployment by modifying the variables in `group_vars/all.yml` or `roles/ollama/vars/main.yml`.
- **Tasks**: If you need to extend or modify the deployment process, edit the `roles/ollama/tasks/main.yml` file.

### Handlers

Handlers are used to trigger specific actions, such as restarting a service. The handlers are defined in `roles/ollama/handlers/main.yml`.

### Extending the Project

If you need to add more roles or playbooks, you can create new directories under `roles/` and add new playbooks in the root directory.
