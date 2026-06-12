---
title: "How can I find the date I installed Ubuntu Linux?"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2009-10-12
Hi. How can I find the date I installed Ubuntu Linux?

---

### Post by Rytron on 2009-10-14
I'm very surprised that there doesn't seem to be a definitive way of doing this.

---

### Post by Jose Catre-Vandis on 2009-10-14
If you used synaptic to install stuff on the day you installed ubuntu, check history in synaptic.

You will also find earliest install date (and initial install) in the oldest dpkg.log file
```
ls -l /var/log/dpkg*
```
This is gunzipped so you will have to unzip it and view the file.

Perhaps a little script can do this work for us :)

---

### Post by gali98 on 2009-10-14
Find a file created by the installation that has not been modified since.
For example, I used /etc/adduser.conf.
if you use ```
ls -l
``` it will list the date modified.
The date should be the date/time you installed ubuntu.
Kory

---

### Post by Rytron on 2009-10-15
> **Jose Catre-Vandis said:**
> If you used synaptic to install stuff on the day you installed ubuntu, check history in synaptic.

You will also find earliest install date (and initial install) in the oldest dpkg.log file
```
ls -l /var/log/dpkg*
```
This is gunzipped so you will have to unzip it and view the file.

Perhaps a little script can do this work for us :)

```
~$ ls -l /var/log/dpkg*
-rw-r----- 1 root adm 206773 2009-10-14 13:01 /var/log/dpkg.log
-rw-r----- 1 root adm 236335 2009-09-30 21:51 /var/log/dpkg.log.1
-rw-r----- 1 root adm  33672 2009-08-30 20:32 /var/log/dpkg.log.2.gz
-rw-r----- 1 root adm  44425 2009-07-31 11:10 /var/log/dpkg.log.3.gz
-rw-r----- 1 root adm  35217 2009-07-01 00:47 /var/log/dpkg.log.4.gz
-rw-r----- 1 root adm  20637 2009-05-31 23:21 /var/log/dpkg.log.5.gz
-rw-r----- 1 root adm  93578 2009-04-28 23:53 /var/log/dpkg.log.6.gz
```

I reckon I installed Ubuntu on 24-4-09.

---

### Post by Rytron on 2009-10-15
> **gali98 said:**
> Find a file created by the installation that has not been modified since.
For example, I used /etc/adduser.conf.
if you use ```
ls -l
``` it will list the date modified.
The date should be the date/time you installed ubuntu.
Kory

```
:/etc$ ls -l
total 2768
drwxr-xr-x   8 root root     4096 2009-05-06 14:15 acpi
-rw-r--r--   1 root root     2986 2009-04-20 14:59 adduser.conf
```

I reckon I installed Ubuntu on 24-4-09.

---

### Post by chiwi on 2009-10-15
> **Rytron said:**
> ```
~$ ls -l /var/log/dpkg*
-rw-r----- 1 root adm 206773 2009-10-14 13:01 /var/log/dpkg.log
-rw-r----- 1 root adm 236335 2009-09-30 21:51 /var/log/dpkg.log.1
-rw-r----- 1 root adm  33672 2009-08-30 20:32 /var/log/dpkg.log.2.gz
-rw-r----- 1 root adm  44425 2009-07-31 11:10 /var/log/dpkg.log.3.gz
-rw-r----- 1 root adm  35217 2009-07-01 00:47 /var/log/dpkg.log.4.gz
-rw-r----- 1 root adm  20637 2009-05-31 23:21 /var/log/dpkg.log.5.gz
-rw-r----- 1 root adm  93578 2009-04-28 23:53 /var/log/dpkg.log.6.gz
```

I reckon I installed Ubuntu on 24-4-09.

The dates you are seeing there are the dates those files were created. You'd have to unzip the oldest one, open it and there should be a log file with the timestamp. That should answer your question.

Ubuntu writes logs to (in this case) /var/log/dpkg.log, and monthly, it rolls the logs, gzipping the older ones. That's why the date you are seeing there, it's the date the zip file was done (almost the end of the month), and not the date ubuntu was installed.

---

### Post by Rytron on 2009-10-15
Thank you Jose Catre-Vandis & gali98 & chiwi.

I wonder will Ubuntu in time, contain a simple command/feature for checking the install date?

:)

---

### Post by chiwi on 2009-10-15
you are welcome.

I'm just curious, why would you want that ?

does Windows, OS X or other *nix distribution have that feature..?

---

### Post by Rytron on 2009-10-15
> **chiwi said:**
> you are welcome.

I'm just curious, why would you want that ?

does Windows, OS X or other *nix distribution have that feature..?

I just like to know as much as possible about Ubuntu Linux.

Windows has the feature. I don't know about Mac. I don't know either if other Linux distros have a feature to show your install date.

If anyone else knows, please make a post.

---

