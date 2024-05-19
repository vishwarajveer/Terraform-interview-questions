# Terraform-Architecture
1. Terraform Core:
• The Brain: Terraform core is the engine driving the entire infrastructure provisioning process. It's responsible for:
• Configuration Parsing: Reads and interprets your Terraform configuration files (written in HashiCorp Configuration Language - HCL).
• Dependency Graph: Analyzes your resources and builds a dependency graph to determine the order in which resources should be created, updated, or destroyed.
• Execution Plan: Generates an execution plan outlining what actions Terraform will take based on your configuration and the current state.
• Provider Communication: Interfaces with providers to send resource creation, modification, and deletion requests.
• State Management: Stores and manages the current state of your infrastructure in a state file.

2. Terraform Providers:
• The Executors: Providers are plugins that act as a bridge between Terraform core and specific infrastructure platforms (e.g., AWS, Azure, GCP, Kubernetes, Datadog). Their key functions include:
• API Interaction: They communicate with the APIs of their respective platforms to carry out resource management tasks.
• Resource CRUD Operations: Providers perform Create, Read, Update, and Delete operations on resources based on instructions from Terraform core.
• Data Source Retrieval: They fetch data from platforms, which can be used as input for other Terraform configurations.

3. Terraform State File:
• The Memory: The state file is a crucial component that stores the current state of your managed infrastructure.
• Resource Mappings: It maps your Terraform resources to the actual resources provisioned on the infrastructure platform.
• Resource Attributes: It records the attributes (properties, configurations) of your resources.
• Synchronization: The state file helps Terraform understand what has changed since the last run, ensuring that it only applies necessary modifications.
Simplified Architecture Diagram:
                               +---------------------+
                               |  Terraform Core     |
                               +---------------------+
                                       |  ^
  Configuration Files (HCL) ----->  Parsing, Planning
                                       |  v
                               +---------------------+
                               |   Terraform State   | <---- State of Resources
                               +---------------------+
                                       |  ^
                                       |  |
                                       |  v
                         +---------+  +---------+  +---------+ 
                         | Provider|  | Provider|  | Provider|  ...
                         | (AWS)  |  | (Azure)|  | (GCP) |  ...
                         +---------+  +---------+  +---------+ 
                                       |
                                       v
                             +----------------------+
                             | Infrastructure Platform|
                             +----------------------+ 
Key Points:
• Modularity: Terraform's architecture is modular. You can add providers for any platform you need to manage.
• State as the Source of Truth: The state file is the single source of truth about your deployed resources. Keep it secure and consistent.
• Declarative Approach: You declare the desired state of your infrastructure in your configuration files, and Terraform figures out how to achieve that state.
• Idempotence: Terraform strives to make its operations idempotent. Running the same configuration multiple times should ideally produce the same end state.
Let me know if you have any other questions or want to delve deeper into specific aspects of Terraform!

![image](https://github.com/vishwarajveer/Terraform-interview-questions/assets/156794114/b85d2d13-add3-4249-b321-d7aed0f8d1bc)


