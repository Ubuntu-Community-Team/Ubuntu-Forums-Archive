---
title: "dpkg broken:("
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by rbalage on 2009-04-17
Hi,
my dpkg is broken after a failed upgrade.
[email]root@balagesv:/var/lib/dpkg/info.backup[/email]# apt-get install libapache2-mod-xmlrpc2
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
[email]root@balagesv:/var/lib/dpkg/info.backup[/email]# dpkg --configure -a
dpkg: failed in buffer_read(fd): `/var/lib/dpkg/updates/0014' copy info file: Input/output error

the file `/var/lib/dpkg/updates/0014' is realy unreadable.
i googled a lot but couldnt find any solution

Thanks

---

### Post by Kevbert on 2009-04-17
Please go to Applications-Accessories-Terminal and enter
```
sudo dpkg --configure -a
```
Enter you login password when prompted.
If that fails please try
```
sudo apt-get remove --purge libapache2-mod-xmlrpc2
```
to completely remove this package. Now try
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kforum on 2009-04-17
kevbert beat me to it, be mindful of the usefulness of apt-get clean, and also occasionally you /var folder may have corrupt files, so look into 'cleaning' the /var folder, or simply rotating your logs.
 
cheers.

---

### Post by iponeverything on 2009-04-17
try

```
mv /var/lib/dpkg/updates/0014 /tmp/

```

---

### Post by rbalage on 2009-04-17
I can't read or write the file, thats the  point. I tried cleaning everything, still not working. Basicly the question is how to delete an undeletable file:)

---

### Post by rbalage on 2009-04-17
kevbert:
dpkg --configure -a
dpkg: failed in buffer_read(fd): `/var/lib/dpkg/updates/0014' copy info file: Input/output error
thats the problem.

---

### Post by Kevbert on 2009-04-18
It looks like your best bet in trying to resolve this is to either raise a question or bug report in [COLOR="Red"][Launchpad]("https://launchpad.net/")[/COLOR]. There are similar bugs there, waiting to be looked at.

---

