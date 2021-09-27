# Ansible Role: SonarQube

An Ansible Role that installs [SonarQube](http://www.sonarqube.org/) 7.2.1 on RedHat/CentOS and Debian/Ubuntu Linux servers. This is a fork of [geerlingguy sonar role](https://github.com/geerlingguy/ansible-role-sonar)

## Requirements

Requires the `unzip` utility to be installed on the server. Also, different SonarQube versions require different minimum versions of Java:

  - SonarQube 5.0-5.5 requires Java 1.7+
  - SonarQube 5.6+ requires Java 1.8+

Finally, recent versions of SonarQube also require MySQL 5.6 or later.

## Role Variables  

Available variables are listed below, along with default values:

```yaml
workspace: /root 
#Directory where downloaded files will be temporarily stored.

sonar_install_directory: /opt/sonar
#Final directory where sonar will be installed

sonar_download_validate_certs: yes
#Controls whether to validate certificates when downloading SonarQube.

sonar_service_user: sonar
sonar_service_group: sonar
#User and group name that will be used to CHOWN sonar_install_directory
#sonar_service_user will also be injected into the sonar.sh for RUN_AS_USER parameter

sonar_download_url: https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-7.2.1.zip"
sonar_version_directory: sonarqube-7.2.1
#The URL from which SonarQube will be downloaded, and the resulting directory name (should match the download archive, without the archive extension).

sonar_web_context: ''
#The value of `sonar.web.context`. Setting this to something like `/sonar` allows you to set the context where Sonar can be accessed (e.g. `hostname/sonar` instead of `hostname`).

sonar_mysql_username: sonar
sonar_mysql_password: sonar

sonar_mysql_host: localhost
sonar_mysql_port: "3306"
sonar_mysql_database: sonar

sonar_mysql_allowed_hosts:
    - 127.0.0.1
    - ::1
    - localhost
#JDBC settings for a connection to a MySQL database. Defaults presume the database resides on localhost and is only accessible on the SonarQube server itself.
```

## Dependencies

  - geerlingguy.java
  - geerlingguy.mysql

## Example Playbook

    - hosts: all
      roles:
        - geerlingguy.sonar

Using the defaults, you can view the SonarQube home at `http://localhost:9000/` (default System administrator credentials are `admin`/`admin`).

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
