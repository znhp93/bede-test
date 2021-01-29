ansible-role-bede-test
=========

This role has been created for the Bede Games tech test. This role has been designed to be run on a linux server. 
I created a bash script which checks the m date of the log files in /logs and removes any that are older than 7 days in order to preserve disk space. Within tasks/main.yml, first the group is created, then the user and then the 
directory where the log files will be stored. The bede_user and group has write permissions on this folder. Then the cleanfiles script is copied from /files to the /etc/cron.daily folder where the script will be ran once a day.

Requirements
------------

n/a

Role Variables
--------------

vars/main.yml

```yaml
group: bede_group - Group created which the bede_user is assigned to
user: bede_user - User created for the application to be run as
log_path: /logs - Directory owned by bede_user, this is where the log files for the application will be created
script_source: files/cleanlogs - This is the location of the cleanlogs bash script
script_destination: /etc/cron.daily - This is where the bash script will be copied to
clean_logs_script: cleanlogs - The name of the script which cleans the log directory
```

group: bede_group - Group created which the bede_user is assigned to
user: bede_user - User created for the application to be run as
log_path: /logs - Directory owned by bede_user, this is where the log files for the application will be created
script_source: files/cleanlogs - This is the location of the cleanlogs bash script
script_destination: /etc/cron.daily - This is where the bash script will be copied to


Dependencies
------------

n/a

Example Playbook
----------------


    - name: Bede tech test
    - hosts: localhost
      roles:
         - ansible-role-bede-test

License
-------

BSD

Author Information
------------------

Zoe Hamilton-Potter
