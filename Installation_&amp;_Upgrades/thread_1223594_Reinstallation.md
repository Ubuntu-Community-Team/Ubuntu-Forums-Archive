---
title: "Reinstallation"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by kapad on 2009-07-26
I have a ubuntu system which has just been recently installed with all my settings the way i want them and no personal data. 

I am getting a new hard drive and wanted to transfer the installation to this drive.

Is their any way in which I can transfer my installation to this hard drive and not lose any of my settings.

I am using ubuntu 8.10 and the hard drive is an external 80 GB hard drive.

PS: any suggestions on how to configure the hard drive are also welcome

---

### Post by merlinus on 2009-07-26
/home is where most application settings and configurations, passwords, bookmarks, email, etc. live, so you can back it up to a dvd or usb flashdrive and copy it your new install.

---

### Post by running_rabbit07 on 2009-07-26
You can use [APTonCD]("http://aptoncd.sourceforge.net/") to make an install disk with all of your favorite programs set up to install during re-installation. You don't have to download it, it is in your Synaptic Package Manager.

---

### Post by kapad on 2009-07-27
> **running_rabbit07 said:**
> You can use [APTonCD]("http://aptoncd.sourceforge.net/") to make an install disk with all of your favorite programs set up to install during re-installation. You don't have to download it, it is in your Synaptic Package Manager.
thanx...
AptonCD sounds like just the thing i need, but would it also work for a reinstallation on the same hard drive?

---

### Post by running_rabbit07 on 2009-07-27
I would recommend using the APTonCD as a way of backing up you installed program and updates faster should you have to reinstall, which I think you may have to do. You should be able to set up the partitions on your new hard drive and copy your home folder to a /home partition so that you don't lose your files and settings. If you were to copy all the files over to the new hard drive, grub may not know to look there during boot to find the system files. Search[ this site]("http://www.psychocats.net/ubuntu/separatehome") to see if you can find more about setting p the home folder and how to tell grub to do what you want.

---

