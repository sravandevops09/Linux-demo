# Linux-demo

## Level-01
-  Setting up Users & Groups for Dev Team

- Create a New Group
```bash
sudo groupadd devteam

#Explanation:
Creates a new group named devteam. Groups help manage permissions for multiple users at once.
```
- Create a New User
```bash
sudo useradd john

#Explanation:
Creates a user named john.
This will NOT create a home directory by default.

```

- Create a User with Home Directory, Shell, and Add to Group
```bash
sudo useradd -m -s /bin/bash -G devteam john


#Explanation of flags:

-m → creates a home directory /home/john

-s /bin/bash → assigns Bash shell to the user

-G devteam → adds user to the devteam group

This is the proper way to create dev users.
```
- Add an Existing User to a Group
```bash
sudo usermod -aG devteam john


#Explanation:

usermod → modify an existing user

-aG → append user to a group without removing existing groups
Adds john to devteam.
```

- Switch to User
```bash
su - john

#Explanation:
Switches to john’s account and loads their environment (- loads .bashrc, PATH, etc.)
```

## 2. Manage Permissions for Project Directories

- Create Project Directory

```bash
sudo mkdir /opt/projectA

#Explanation:
Creates a directory named projectA under /opt, commonly used for application files.
```
- Change Ownership to Specific User & Group

```bash
sudo chown john:devteam /opt/projectA

#Explanation:
Makes:

john the owner

devteam the group owner

Only they can control the directory.
```
 - Give Group Read/Write/Execute Permissions
 ```bash
 sudo chmod 770 /opt/projectA

 #Explanation of permission 770:

Owner: full access (7)

Group: full access (7)

Others: no access (0)

Use when only dev team should access the folder.
```

- Give Read-Only Access to Others
```bash
sudo chmod 755 /opt/projectA

#Explanation:

Owner & group: full access

Others: read + execute (can view, not edit)

Used for public web content, scripts, etc.
```

## 3. Install Required Packages (Git, Nginx, Java)

- Update Package Index
```bash
sudo apt update -y     # Ubuntu/Debian
sudo yum update -y     # RHEL/CentOS/Amazon Linux

#Explanation:
Refreshes the list of available packages so the latest versions can be installed.
```

- Install Git
```bash
sudo apt install -y git

#Explanation:
Installs Git version control.
-y answers “yes” automatically.
```

- Install Nginx
```bash
sudo apt install -y nginx

#Explanation:
Installs the Nginx web server.
```

- Install Java
```bash
sudo apt install -y openjdk-11-jdk

#Explanation:
Installs Java Development Kit (JDK) version 11.

## 4. Check System Info (Memory, CPU, Disk)
- Check CPU Info
```bash
lscpu


#Explanation:
Shows CPU model, cores, threads, architecture — important for sizing servers.
```

- Check Memory Usage
```bash
free -h


#Explanation:
Shows total, used, and free RAM.
-h = human readable (MB/GB).
```


- Check Disk Usage
```bash
df -h


#Explanation:
Shows usage of all mounted disks and partitions.
Helps identify full disks.
```

- List Block Devices
```bash
lsblk


#Explanation:
Shows all storage devices like disks, partitions, volumes in a tree format.
```

- Check OS Version
```bash
cat /etc/os-release


#Explanation:
Displays Linux distribution name, version, and other details — useful for troubleshooting.
```





