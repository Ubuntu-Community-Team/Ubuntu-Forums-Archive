---
title: "Need help with backup script."
date: 2008-10-01
forum: General Help
---

### Post by terryit3 on 2008-10-01
I am running a Dell PowerEdge 2950 with VMWare ESXi 3.5.
I have 4 virtual machines set up. Three of the VMs are running Ubuntu, the other is running Red Hat 9 and has the tape drive installed to it.

I have NFS shares setup and sharing the content of the var and home directories on the Ubuntu server to the Red Hat server.

The problem I am running into is that, although the Red Hat server is running the backup script as root, once it tries to backup some of the secured files on the Ubuntu server, it is not running as root or a user with sudo permission.

Is there a way to have the backup script on the Red Hat server assume sudo privileges on the Ubuntu servers?

An example of my backup script is below:

```

cd /
tar -cvf /dev/st0 var          #var directory on local RH server
tar -rvf /dev/st0 mnt/webvar   #var directory on web server - Ubuntu
tar -rvf /dev/st0 mnt/mailhome #home server mail directory - Ubuntu
mt -f /dev/st0 rewoffl

```

The script fails when trying to backup the /mnt/webvar/spool/mqueue folder which has 770 permissions.

Any help would be appreciated.
T

---

### Post by terryit3 on 2008-10-01
Adding no_root_squash to the NFS share config fixed the problem.
Dumb!

---

