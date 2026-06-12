---
title: "Install over CentOS?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by meburke on 2009-03-30
A few months back I installed CentOS on one of my systems because I thought I had a need for Red Hat compatibility. Now I've got months worth of work on it and I'm just tired of dealing with CentOS. All my other Linux systems are running Kubuntu and I'd like to over-install Kubuntu, replacing the CentOS installation, yet keeping my file system, applications and KDE configuration.

CAn it be done? Can anyone point me to instructions and discussions on doing this?

Thank you.

---

### Post by Simian Man on 2009-03-30
If you didn't create a separate partition for home, then you will need to back that up to an external drive.

---

### Post by xaos on 2009-03-30
What Simian Man said, if your /home is a separate partition just use the manual partition option when setting up ubuntu, mount that partition as /home and DO NOT format it. If it is not a separate parttion, backup all the contents of /home and put it back after installing ubuntu. It will contain all files and (most of the) configuration files. 

Programs I think you will need to reinstall AFAIK.

---

### Post by justaguy168 on 2009-11-11
I have a similar situation.  I have a pc with an old version of CentOS.  (CentOS is variant of Red Hat Enterprise Linux or RHEL.)  I want to convert it to Ubuntu.  It will be a single-boot machine.  It doesn't have any other OS on it except CentOS.  I have other PCs with WinXp connected via router.  I own Paragon Drive Backup [http://www.paragon-software.com/home/db-personal/](http://www.paragon-software.com/home/db-personal/) which has a boot CD with a small version of Linux on it.  Will this help me?  Can I just "rm *" ?  Is there any special boot sector which needs to be removed?  Do I need to use Grub for this?  I'm not exactly sure what Grub is but I know it is for configuring dual boot machines which is not my situation.
 
I am new to Linux but will be happy to RTFM.  Please point me in the right direction.  Whatever detail you can provide me would be appreciated.
 
Thanks in advance.

---

