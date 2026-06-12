---
title: "Unable to mount Transcend USB flash drive!!! HELP"
date: 2009-07-14
forum: Hardware
---

### Post by ranjith.ts on 2009-07-14
Hi guys,,  I am new to ubuntu so plz help me out.  I have a laptop running on vista sp2/ubuntu 9.04.  I also have a transcend usb 4 gb drive which has some viruses in it which i want to delete and format the complete USB device. I don wan to plug it on vista side since i am sure it might affect my computer so i don wa to take risk  Since the virus in my pendrive is an .exe file so i thought of pluggin it in ubuntu side so the virus files cannot do anything  But the problem is it wont mount on the screen and when i click on place>computer i have an USB icon and when i try to open it says "Unable to Mount location" can't mount file  Can anyone help? ANY HELP IS APPRECIATED...

---

### Post by ktat on 2009-08-11
I have a very similar problem.

I have two usb sticks that were, until recently working fine with all linux OS I tried (mint, ubuntu, fedora) then, all of a sudden I can't mount them any more.  When pugged in to pc they don't show up on the desktop, if I open "computer" folder usb is listed but double clicking on it brings up error message Unable to "**mount location**" "**Can't mount file**".

I am not 100% certain, but I believe I may have used both on a Vista or XP machine prior to this problem occuring.

---

### Post by paulisdead on 2009-08-11
what do see when you plugin the drive and run "dmesg" from the command line?  Have you tried manually mounting the device with something like

sudo mount /dev/sdb /media/disk

Of course replacing sdb for the correct device, and /media/disk for wherever you want to mount it.

---

### Post by GeorgeVita on 2009-08-13
Hi **ktat**,
check also that you have a valid **Label**. I faced a similar problem with my Transcend JF V30 and fixed when placed a plain text label (ex. JetFlash) via GParted (you can do it also from other O.S.).

Regards,
George

---

### Post by fennec_fox on 2009-08-13
> **ranjith.ts said:**
> Hi guys,,  I am new to ubuntu so plz help me out.  I have a laptop running on vista sp2/ubuntu 9.04.  I also have a transcend usb 4 gb drive which has some viruses in it which i want to delete and format the complete USB device. I don wan to plug it on vista side since i am sure it might affect my computer so i don wa to take risk  Since the virus in my pendrive is an .exe file so i thought of pluggin it in ubuntu side so the virus files cannot do anything  But the problem is it wont mount on the screen and when i click on place>computer i have an USB icon and when i try to open it says "Unable to Mount location" can't mount file  Can anyone help? ANY HELP IS APPRECIATED...

This may not be too helpful considering your situation but, this happens to me and a bunch of people I know after using windows machines when the usb drive doesn't unmount properly. 

Typically, I plug it back into a windows machine and then do a "safely remove". Then it seems to work in ubuntu again. This has worked for my like 80% of the time. The rest of the times it's been problems with incorrect mounts in mtab or fstab. That said, it's still a rare problem for me.

---

