---
title: "ssh authentication problems"
date: 2008-09-15
forum: General Help
---

### Post by starkes on 2008-09-15
Hi.

I'm attempting to have a bash script which is called from the user www-data (called through a php exec command, triggered by a web interface) connect to a remote machine to run another script. However, I can't seem to get ssh to automatically authenticate on the remote server under the user www-data.

Even when I try to change the home directory of www-data on the remote server, it ALWAYS looks for the .ssh folder in the same place when i ssh in:

Could not create directory '/var/www/.ssh'

does anyone know how to change the .ssh folder that a particular user will use when they log in?


also, i have been able to give root automatic access to the remote server by running ssh-keygen as root on the local machine and coping the contents of /root/.ssh/id_rsa.pub into /root/.ssh/authorized_users on the remote machine. I tried having the script run by the web interface (automatically run by www-data) connect by issuing ssh root@remoteserver. However, unlike when I log into the local machine as root and do 'ssh remoteserver', when i start as another user and do 'ssh root@remoteserver' it wont authenticate automatically, as if im connecting under the name i'm locally logged in as. but i specified to connect as root?

any ideas?

---

### Post by Peter09 on 2008-09-15
I believe that the ssh configuration file defaults to not allowing root to login, which is a good idea. You will need to modify the configuration in /etc/ssh/ssh.config

---

