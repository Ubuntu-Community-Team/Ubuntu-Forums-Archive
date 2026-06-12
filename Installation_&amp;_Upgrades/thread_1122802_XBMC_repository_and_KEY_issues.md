---
title: "XBMC repository and KEY issues"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by mcneilly on 2009-04-11
i've been trying to install XBMC onto my newly installed intrepid machine, but i've been running into some difficulties installing the repositories, first when I added the repository 

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
W: You may want to run apt-get update to correct these problems

```

I have since found out that they key is 0x6d975c4791e7ee5e

to try and install said key I entered 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x6d975c4791e7ee5e
```

and in response received
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0x6d975c4791e7ee5e
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

any help as to how to actually update the key?

---

### Post by Partyboi2 on 2009-04-11
Open a terminal and type or paste[FONT=monospace]
[/FONT]```
gpg --keyserver keyserver.ubuntu.com --recv 43C0AFF0D7FAE680
gpg --export --armor  43C0AFF0D7FAE680 | sudo apt-key add -

```
then
```
sudo apt-get update
```

---

### Post by iluciv on 2009-04-19
Hi when running the above I get the following error 

```

~$ sudo gpg --keyserver keyserver.ubuntu.com --recv 43C0AFF0D7FAE680
gpg: WARNING: unsafe ownership on configuration file `/home/iluciv/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

Also tired to add the text file key following this direction 
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

It adds the file into the section with out issue but apt-get update still gives the public key error. 

This is a brand new install of Ubuntu intrepid is it a permission issue?

---

### Post by Partyboi2 on 2009-04-19
Try without using sudo so the command would be[FONT=monospace]
[/FONT]```
gpg --keyserver keyserver.ubuntu.com --recv 43C0AFF0D7FAE680
```
then
```
gpg --export --armor  43C0AFF0D7FAE680 | sudo apt-key add -
```

---

### Post by iluciv on 2009-04-19
Your a Gentleman and a scholar! my thanks to you :D

---

