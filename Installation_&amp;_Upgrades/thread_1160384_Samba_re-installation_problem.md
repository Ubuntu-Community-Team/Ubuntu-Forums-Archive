---
title: "Samba re-installation problem"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by AlmoG on 2009-05-15
I was trying to re-install samba due to some changes i did that messed up my smb.conf file and some other files.

This is the output i got from synaptic package manager:
> Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 120893 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.3.2-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba-common (2:3.3.2-1ubuntu3) ...
Not replacing deleted config file /etc/samba/smb.conf
Install/upgrade will fail. To recover, please try:
  sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
  sudo dpkg --configure -a
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.3.2-1ubuntu3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 samba-common
 smbclient
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba-common (2:3.3.2-1ubuntu3) ...
Not replacing deleted config file /etc/samba/smb.conf
Install/upgrade will fail. To recover, please try:
  sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
  sudo dpkg --configure -a
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.3.2-1ubuntu3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
 samba

Can anyone help me with this?

---

### Post by Partyboi2 on 2009-05-16
Hi, have you tried doing what it suggests? Open a terminal and
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a
```

---

