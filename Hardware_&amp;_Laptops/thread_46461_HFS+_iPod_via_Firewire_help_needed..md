---
title: "HFS+ iPod via Firewire help needed."
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by papabean on 2005-07-04
Has anyone got any tips for using a Mac-formatted iPod via Firewire? I don't have access to Windows machines to restore the iPod to Windows format, so I'd rather it work in Linux than go back to using my iMac G4. 
 
 I've followed the [steps]("http://www.gtkpod.org/README") on the GTKPod site and the only problem I have is trying to unmount the iPod. When I run:```
rmmod sbp2
```it causes the terminal/console/command to hang and the module remains loaded.
 
After that, I have to ignore the "Do not Disconnect" on the iPod and disconnect it. Then, I can't mount it again unless I reboot. 
 Whatever information might help out, don't hesitate to ask.  I'll gladly provide it.
 
For what it's worth, I did have this working in Gentoo just before I switched to Ubuntu, so I know it's possible, but I'm not going back to compilation hell if I can avoid it.

---

### Post by scoon on 2005-07-05
Hey there, 

Also look here: [http://www.linux1394.org/](http://www.linux1394.org/)

I have found that when mine hangs, open up another shell and rmmod ohci1394 && rmmod iee1394 willl free up the frozen console. 

regards, 

scoon

---

### Post by papabean on 2005-07-05
Thanks for the tip. I'm going to have to try this tomorrow.  I'm too tired, but if that works, I'll write up a script to take care of that for me.  

Will those modules be loaded back in the next time I connect the iPod or would I need to modprobe them prior?

---

### Post by scoon on 2005-07-05
Hey there, 

read over the link i posted, and you will need to reload ohci1394 and it will auto load ieee1394

regards, 
scoon

---

### Post by papabean on 2005-07-06
Thanks for the tip, but that made it worse, actually.  It caused the entire system to freeze.

But reading through the link you provided, I DID read two things that may help:

#1. Under the section about /proc for the sbp2 protocol:> To manually remove a SBP-2 device after it's been unplugged
      echo "scsi remove-single-device 0 0 0 0" > /proc/scsi/scsi
To check to see which SBP-2/SCSI devices are currently registered
      cat /proc/scsi/scsi#2. Under the FAQ:> **What is required to safely unplug an iPod?**
Use the command "eject /mnt/ipod" or "eject /dev/sdx". (Check for the correct path with "mount".)I've not tried simply "eject"ing the device. I've always unmounted or allowed Nautilus to do it. I'm going to try #2 first (it's the simpler of the two) and let you know how it goes.

---

### Post by papabean on 2005-07-06
Ok.  Here's the situation thus far:

The iPod automagically mounts and a Nautilus window opens for it. I am at last able to disconnect it safely by issuing: ```
eject /dev/sda
```However, it only mounts as owned by root:root (755 permissions) and I have to eject as root. The last is a minor quibble as I don't mind having to sudo to eject it.

The first part of that is a problem.  I cannot get it to mount with either the proper permissions or the proper owner.

What process automagically mounts the iPod and where should I be looking to modify permissions/ownership correctly?

From fstab:```
/dev/sda	 /media/Quizoc hfsplus rw,uid=1000,gid=1000,user,noauto,noexec,umask=0
```

---

### Post by scoon on 2005-07-07
Hey there, 

Open up a terminal and type: man udev

udev is what manages mount/unmounting. 

regards, 

scoon

---

### Post by papabean on 2005-07-07
Thanks to my experience with gentoo and my iPod, I'm familiar with rewriting the udev rules.  I'll add the one from the GTKPod readme and see if that fixes it or I can just chmod it after it's mounted. 

Thanks for all of your help, scoon.  I probably wouldn't have even gotten this far in Ubuntu without the pointers.

---

