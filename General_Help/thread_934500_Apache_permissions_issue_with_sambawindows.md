---
title: "Apache permissions issue with samba/windows"
date: 2008-09-30
forum: General Help
---

### Post by joshcoady on 2008-09-30
I'm running Ubuntu 8.04 JeOS as a guest OS running in VirtualBox with Windows Vista as the host OS. This ubuntu server is primarily used to test php sites during development. The files for the web site are on the Windows host and the server has access to them through samba.

Everything works great except apache has problems writing to files it has previously created if they are on the Windows share (i.e. file I/O to /tmp/ works exactly as expected).

Specific problems and other details:

[LIST]
[*]The apache user and group is www-data
[*]the root of the site and down are on the windows share and owned by www-data
[*]During a single request apache can create a file and successfully write to it
[*]During subsequent requests apache fails to append to the same file
[*]This seems to be because when the file is created by apache, it's owner/group is set to root instead of www-data (if I manually chown the file to www-data then apache can use the file normally)
[/LIST]

Any ideas on how to get apache to create files owned by itself instead of root?

TIA!

---

### Post by spiderbatdad on 2008-09-30
seems like your instance of apache is running as root, in this case. You may have multiple instances of apache running.

---

### Post by joshcoady on 2008-09-30
How do I tell what it is running as and how do I change it (if needed)?

/etc/apache2/apache2.conf contains:

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

/etc/apache2/envvars contains:

export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

---

### Post by joshcoady on 2008-11-10
Any other suggestions? .. I still have this issue .. Thanks!

---

