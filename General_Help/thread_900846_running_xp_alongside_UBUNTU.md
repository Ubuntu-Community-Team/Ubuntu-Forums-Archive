---
title: "running xp alongside UBUNTU"
date: 2008-08-25
forum: General Help
---

### Post by bradpurvis on 2008-08-25
i need to know how ASAP

---

### Post by S1xp4ck on 2008-08-25
There are a few methods.  Do you want to run XP within Ubuntu or as a dual boot?

---

### Post by bradpurvis on 2008-08-25
i would like to dual boot it but it is not really an option right now. so inside ubuntu

---

### Post by tuxxy on 2008-08-25
Install virtual box and run it on a virtual drive, displayed in a window from in Ubuntu.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by tramir on 2008-08-25
Have a look at [Virtualbox]("http://www.virtualbox.org/") (worked better for me, more responsive) or [Vmware]("http://www.vmware.com/"). Just two quick options. Virtualbox has packages for Ubuntu on their website. For Vmware, you need to use their installer.

---

### Post by bradpurvis on 2008-08-25
it says i need a kernal driver

this is the exact message after attempting to power up


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by tuxxy on 2008-08-25
Thats strange, how did you install virtualbox? if its from the repos maybe try a reinstall

---

### Post by bradpurvis on 2008-08-25
i installed it from the website you gave me.

---

### Post by bradpurvis on 2008-08-25
you know the terminal code?

---

### Post by bradpurvis on 2008-08-25
could anyone give me a tutorial on how to set up windows xp on it.

---

### Post by bradpurvis on 2008-08-25
this is the complete oppisite of ASAP

---

### Post by bradpurvis on 2008-08-25
this is the total oppisite of ASAP

---

### Post by bradpurvis on 2008-08-25
someone please help!

---

### Post by mssever on 2008-08-25
> **bradpurvis said:**
> this is the complete oppisite of ASAP

> **bradpurvis said:**
> this is the total oppisite of ASAP

> **bradpurvis said:**
> someone please help!
Being impatient doesn't motivate volunteers to help you (this isn't paid technical support). If you can't handle waiting several hours, then you'd be better off asking on the #ubuntu freenode IRC channel.

Also, remember that when you get no response, it might be that no one who's read your message knows the answer. I don't. So give it time.

---

### Post by Mgiacchetti on 2008-08-25
uninstall the OSE and go to [this page]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")  and download your distro's installation package 

then... save [this file]("http://virtualbox.org/download/1.6.0/VBoxGuestAdditions_1.6.0.iso") to your desktop, open terminal and do the following.
back up your current guest additions
```

sudo cp /usr/share/virtualbox/VBoxGuestAdditions.iso /usr/share/virtualbox/VBoxGuestAdditions.iso.bak 
```Change working directory to your Desktop
```

cd Desktop 

```Overwrite your current guest additions ( >1.6.0 ) with the version you just downloaded (1.6.0)
```

sudo cp VBoxGuestAdditions_1.6.0.iso /usr/share/virtualbox/VBoxGuestAdditions.iso 

```The reason for this is because Guest Additions 1.6.2-1.6.4 has a problem with Windows XP and shared folders/network stuff.

Also.  If you happen to get a Kernel update in ubuntu you will need to open Synaptic Package Manager, find your installed VirtualBox and highlight it, click on the package menu and select configure.  

There should be a window that pops up, continue clicking next until you have passed a window that asks you whether or not you wish to compile the kernel module to which you should have selected either next or yes, whichever is available.

This is needed every time you receive a new kernel update, yes it is kind of tedious, however it seems easier than dealing with the Open Source Edition.

---

### Post by bradpurvis on 2008-08-26
thank you. i was being impatient because i was trying to get my uncle to help me and i had a set amount of time to work on it but i never fixed it because of slow response. don't worry about it now though.

---

### Post by bradpurvis on 2008-08-26
please don't think of me as a jerk though i just didn't have time to wait.

---

### Post by bradpurvis on 2008-08-26
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

 if i (we) can't fix this problem i will have to get a new hard drive and install windows.

---

### Post by Comzee on 2008-08-27
You have to run Virtualbox as root.

The command is ```
sudo virtualbox
```

Then you have to have a windows installation CD. Just go to create new, and from there it's pretty self explanatory, just create the virtual partition and RAM allocation and install Windows via Virtualbox.


Just as a side note, I don't know why you want to get windows running so bad, but running any virtual machine (including windows in virutalbox) will have much more limited applications then if you would install the OS normally.

---

### Post by bradpurvis on 2008-08-27
purvis@purvis-desktop:~$ sudo virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

how could i fix this?

---

### Post by mssever on 2008-08-27
If you use the closed source version, installation is simply a matter of installing the .deb and rebooting. No configuration or additional steps required.

---

### Post by bradpurvis on 2008-08-27
ok the first problem is resolved now for the other and hopefully last one.

it says everytime i turn it on

FATAL ERROR! NO BOOT MEDIUM FOUND SYSTEM HALTED. 

does anyone know what to do about this?

---

### Post by mssever on 2008-08-27
> **bradpurvis said:**
> ok the first problem is resolved now for the other and hopefully last one.

it says everytime i turn it on

FATAL ERROR! NO BOOT MEDIUM FOUND SYSTEM HALTED. 

does anyone know what to do about this?
I'm assuming you haven't installed an OS yet. If that's the case, then go to the menubar and you'll find an option to mount a CD (or an ISO). Mount it, then reset the VM. If it still doesn't boot off the CD, reset the VM again and hit F12 at the BIOS screen. Hit c to explicitly boot from the CD.

---

### Post by Xarver on 2008-08-27
I suggest you try [Wubi](http://www.wubi-installer.org/)
It's free and it installs a Windows and Ubuntu 8.04 dual boot.
If you don't like Ubuntu,(impossible), or you want to remove it
for some odd reason, you can uninstall it through the Windows
Add and Remove Programs... Go Wubi!!! ~~~

---

### Post by bradpurvis on 2008-08-27
lol that only works if you are using windows at all i'm not.

---

