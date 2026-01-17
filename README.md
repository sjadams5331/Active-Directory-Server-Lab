# Active Directory Home Lab

## Overview
This project is a fully functional Active Directory home lab designed to simulate a real-world corporate IT environment. The goal of this lab was to gain hands-on experience with Windows Server administration, identity and access management, Group Policy, file services, networking fundamentals, and remote desktop support operations.

The environment includes a domain controller providing Active Directory, DNS, and DHCP services, multiple domain-joined Windows workstations, and a dedicated file server. Access is managed using role-based security groups following the principle of least privilege. Group Policy is used to enforce security settings, map network drives, control Remote Desktop access, and standardize workstation behavior.

A remote support workflow was implemented to mirror real desktop support operations. Support users can securely connect to workstations using Remote Desktop, review system and application logs via delegated Event Viewer access, and troubleshoot common user issues without requiring administrative privileges or server access.

## Lab Environment
- **Hypervisor:** Oracle VirtualBox  
- **Servers:** Windows Server 2025 (Active Directory, DNS, DHCP, File Server)  
- **Workstations:** Windows 11 Pro  
- **Scale:** 2 servers, 5 domain-joined workstations  

## Core Components
- Active Directory, DNS, and DHCP services  
- Group Policy design and enforcement  
- File server with NTFS permissions  
- Role-based access control (RBAC)  
- Secure Remote Desktop support workflow  

## Security & Access Model

Access within the environment is designed around the principle of **least privilege** and enforced using **role-based access control (RBAC)**. Permissions are never assigned directly to individual users. Instead, access is granted through Active Directory security groups to ensure consistency, scalability, and ease of management.

### Identity and Role Separation
- Users are organized into department-based Organizational Units (OUs)
- Security groups represent job roles rather than individual users
- Users inherit access through group membership, not direct permissions

### File Access Control
- Departmental file shares are hosted on a dedicated file server
- NTFS permissions are applied exclusively to Active Directory security groups
- Each department has access only to its respective file share
- IT administrators retain full access for management and recovery purposes

### Group Policy Enforcement
- Group Policy Objects (GPOs) are scoped to Organizational Units
- Policies are separated by function to improve clarity and troubleshooting
- Default Domain Policy is reserved for authentication-related settings only

### Remote Desktop Access Control
- Remote Desktop access is controlled using User Rights Assignment via Group Policy
- Support users are permitted to access workstations only
- Server access is restricted to IT administrators
- Explicit deny policies prevent unauthorized RDP access

### Delegated Troubleshooting Access
- Support users are granted read-only access to Event Viewer logs
- Access is delegated using the built-in **Event Log Readers** group
- Troubleshooting capabilities are provided without granting administrative privileges

This access model ensures users and support staff have only the permissions required to perform their roles while maintaining clear separation between user, support, and administrative responsibilities.

## Remote Support Workflow

The lab includes a structured remote desktop support workflow designed to mirror real-world desktop support operations. Support access is intentionally limited and controlled to allow troubleshooting while maintaining security and least-privilege principles.

### Remote Desktop Access
- Remote Desktop is enabled on workstations via Group Policy
- Access is restricted to members of a designated support security group
- Support users are permitted to connect to workstations only
- Servers (Domain Controller and File Server) are restricted to IT administrators

### Support User Capabilities
- Securely connect to user workstations using Remote Desktop
- Review system and application logs using Event Viewer
- Troubleshoot common user issues such as:
  - Network connectivity problems
  - Drive mapping failures
  - Authentication and login issues
  - Application and service errors

### Delegated Access Model
- Support users are not local administrators on workstations
- Read-only access to Event Viewer logs is delegated using Group Policy
- Administrative privileges are reserved for IT roles only
- All access is centrally managed using Active Directory groups and policies

### Operational Design
- Remote support access is enforced consistently across all workstations
- Group Policy ensures changes are applied automatically and uniformly
- The workflow supports troubleshooting without exposing servers or sensitive administrative controls

This workflow demonstrates how support staff can effectively diagnose and resolve issues remotely while maintaining strong access controls and minimizing security risk.


## Documentation
Detailed design and configuration notes are available in the `/docs` and `/screenshots` directory.

## Skills Demonstrated
- Active Directory domain administration and user management  
- Organizational Unit (OU) design and delegation  
- Role-Based Access Control (RBAC) using security groups  
- Group Policy Object (GPO) creation, scoping, and troubleshooting  
- Domain password and account lockout policy configuration  
- Centralized drive mapping using Group Policy Preferences  
- NTFS permissions and SMB file share management  
- Windows File Server deployment and administration  
- DNS configuration and domain name resolution  
- DHCP server configuration and scope management  
- Windows Server domain joining and role installation  
- Secure Remote Desktop (RDP) access configuration via Group Policy  
- Delegated Event Viewer log access using least-privilege principles  
- Workstation and server access separation (support vs admin roles)  
- Network connectivity troubleshooting (DNS, SMB, authentication)  
- Remote desktop support workflows and user troubleshooting  
- Enterprise-style security hardening and policy enforcement  
- Documentation and technical communication of system design  
