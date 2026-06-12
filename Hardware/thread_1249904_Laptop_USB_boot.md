---
title: "Laptop USB boot"
date: 2009-08-25
forum: Hardware
---

### Post by Chasville on 2009-08-25
My Lenova laptop has become sort of hosed.
I am wanting to boot Ubuntu Linux on a USB flash drive.
It is not working.
I expect I am doing something wrong.
 
Help?
 
IBM Lenova Z60m
brand new HP 8 GB thumbdrive
Downloaded and wrote UNR 9.04
Can see the files and directories when the stick is in my PC.
But the laptop reports a "boot error".

---

### Post by karamu on 2009-08-25
I know it's an obvious one but you did use the create USB boot drive from the Administration menu (rather than just copy the files across)?

Alternatively you can try using Unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

which will create a bootable USB drive from an ISO.

Also, have you checked the settings in your BIOS so in the boot order USB comes first?

---

### Post by Chasville on 2009-08-27
I followed the directions from the Ubuntu Website.
I downloaded the "writer" and did the "write" as directed.
The only deviation was using an 8 GB USB stick instead of a 1 GB stick.
 
Pressing F12 on the laptop brings up a "boot menu" from which I selected the USB device.
 
I'll double check the process tonight.

---

### Post by karamu on 2009-08-31
That sounds like it should be OK- when you say "writer" do you mean the entry "USB startup disk creator"? Are you using an ISO or IMG file?

What actually happens when you try to boot? Again it sounds like you are doing the right thing by selecting the USB boot option.

Let me know how you get on- good luck.

---

### Post by karamu on 2009-08-31
I just found a program called usb-imagewriter (you'll find it in Synaptic package manager) that might also help you.

---

### Post by karamu on 2009-08-31
OK, didn't think that he might have a Windows installation just now and wants to replace it with Ubuntu- was assuming Ubuntu was in already and it was a re-install we were talking about.

However, unetbootin is available for Windows too and is really easy to use.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Chasville on 2009-10-02
Gave up on booting from the USB stick.
Followed other Ubuntu directions for creating a CD from a downloaded .iso file.
That worked -- allowed me to boot from CD and run Ubuntu without affecting the local hard drive.  Successfully saw the folders and files I wanted to retrieve, successfully networked with my NAS and transfered the files.  Then used the same CD image to install Ubuntu, trashing the Windows installations (found there were two flavors on the box).  Now the laptop is purely Ubuntu Linux, and I don't have to worry about futzing with the 'puter.  I've even successfully connected to my silent/covert wireless network, more reliably than the IBM Connection manager, so I'm always at 54 Mbps now and not accidentally connecting to other stray unprotected networks.  Wooo Hoo.

Next step -- new thread(s) -- is to install Eclipse and a Java SDK.

---

