---
title: "There won't be any Wubi for me today!"
date: 2008-07-16
forum: General Help
---

### Post by onederer on 2008-07-16
I use WinXP Pro. ver.3.0
I downloaded the Wubi installer directly (the *.exe version).  Kept on getting error message, and the download was interrupted. I shut down the AVG virus detector, and Zone Alarm.  Still no joy!

I read to use the command prompt instead, with the command not to use the MD5checksum.  That only added to my frustration! Same installation woes.

I wanted to use WUBI because I have telephone adapter, MagicJack, plugged into one of the USB ports. It has an incoming telephone number, and the MagicJack doesn't support Linux.  I need Windows to be running all the time, and it would be quite a boon if Linux would be running at the same time.  This way I could get my very inexpensive long distance telephone calls ($20.00 per year), and be using Kubuntu at the same time.

But in order to be able to achieve this, a dedicated guru would have to figure out what is wrong with the installer.  I can see that I'm not the only one, so there should be something done about this, or WUBI is just a useless product, unless there is some other way of installing it.

Any ideas?  :confused:

---

### Post by ago on 2008-07-16
Can you be more specific about the error messages?

---

### Post by mlentink on 2008-07-16
> **onederer said:**
> I need Windows to be running all the time, and it would be quite a boon if Linux would be running at the same time.  This way I could get my very inexpensive long distance telephone calls ($20.00 per year), and be using Kubuntu at the same time.

Wubi, even if installed correctly, will not allow you to run Windows and (K)Ubuntu at the same time. You will need to use some kind of virtualization software to be able to do that, preferably VMWare or VirtualBox. 
Wubi allows you to install Ubuntu in a virtual drive on your system, but it will not allow you to run both operating systems at the same time.

I hope I'm not dissappointing you, but that's the way it is.

Edit: please download the Live-CD. It includes the Wubi installer. Burn it at a slow speed. Check the MD5 checksum.

---

