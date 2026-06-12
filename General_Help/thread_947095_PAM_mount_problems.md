---
title: "PAM mount problems"
date: 2008-10-13
forum: General Help
---

### Post by whollycow on 2008-10-13
I'm in the process of setting up a relatively small network of client desktops with server-based authentication and home directories.  Using PAM and ldap I have been able to get the authentication stuff working but I can't figure out how to mount the user's home folder on login.

My research leads me to the PAM-mount module but the documentation isn't too helpful and I can't get it working on my own.  Is anyone aware of a really good how-to?  I've looked everywhere and haven't found an easy-to-understand walkthrough.  Does someone have some experience that they would like to share?

FYI: Home folders are being shared via Samba.  Clients are running CentOS 5.2 (although the PAM configuration shouldn't differ much between distributions) and the server is Mac OSX.

Thanks a million!

---

### Post by [woodstock] on 2009-01-07
Hi,

I experience the same problem:
There is a LDAP server with server based home directories. The authentification works (using pam_ldap.so), but I cannot mount the home folders with pam_mount.
Did you succeed or have you foud a workaround for your problem, yet?

---

### Post by whollycow on 2009-02-17
I successfully got pam_mount to work but I had to configure things via pam_mount.conf.  What sort of problems are you having?  I can post part of my pam_mount.conf if you think it would help.  I'll have to do it at work when I have access to everything.

---

### Post by steelsteel! on 2010-11-23
> **whollycow said:**
> I successfully got pam_mount to work but I had to configure things via pam_mount.conf.  What sort of problems are you having?  I can post part of my pam_mount.conf if you think it would help.  I'll have to do it at work when I have access to everything.

Hello! I would badly need a HowTo for the pam_mount.conf.xml for the following setting:

A HowTo for Ubuntu 10.04 (!)

GDM + PAM + OpenLDAP Users + SMB Usershares

I only get empty local user folders mounted...
see here: [http://forum.ubuntuusers.de/topic/pam-mount-mit-gdm-gnome-problem-beim-einlogge/#post-704384](http://forum.ubuntuusers.de/topic/pam-mount-mit-gdm-gnome-problem-beim-einlogge/#post-704384)

---

