---
title: "iPod on Ubuntu ?"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by lavitz on 2004-12-26
Well im very fresh to linux so i don't know nothing :( But could someone please tell me step by step how to get my iPod to work under Ubuntu or a good guide? Im using  a firewire connection on my iPod.

---

### Post by dgantony on 2004-12-26
Try [gtkPod](http://gtkpod.sourceforge.net/) . I have the 4th gen (click wheel) ipod and it works great.

---

### Post by lavitz on 2004-12-28
Well this is what i have in my etc/fstab:
"/dev/sda2	/mnt/ipod	vfat	defaults,user,noauto,sync,umask=000	0	0"

and when i try to mount mnt/ipod i only get this message:
"mount: special device /dev/sda2 does not exist"

edit: I just had a littel look i /dev/ and i don't have a file called sda1 or sda2 I only have some files called sda, sdb, sdc

---

### Post by grim1234 on 2004-12-28
Hi, 

I think sda denotes a usb device, you may need something else if you use firewire. The number refers to the partition on the device. ie - hda1 is the first partition on the hard drive. sda1 is the first partition on the first usb device. 

You can use the command dmesg to see where your ipod can be found. plug the device in then run dmesg.

Regards,

G.

---

### Post by dave_euser on 2004-12-30
[QUOTE=lavitz]Well this is what i have in my etc/fstab:
"/dev/sda2	/mnt/ipod	vfat	defaults,user,noauto,sync,umask=000	0	0"

and when i try to mount mnt/ipod i only get this message:
"mount: special device /dev/sda2 does not exist"

edit: I just had a littel look i /dev/ and i don't have a file called sda1 or sda2 I only have some files called sda, sdb, sdc[/QUOTE]
 Whether you plug your ipod in using firewire or USB, it will use the SCSI transport driver to communicate with your PC.

If you post your dmesg output after you plug in your ipod, someone else here can take a look at it.

The big thing is to confirm that the ipod's drive is showing up as sda, sdb, etc.... also, to make sure that you have the proper drivers loaded to talk to the ipod.

So, a step by step (starting with a fresh boot, no ipod plugged in)
1) type "sudo modprobe sbp2" from a terminal to load the SCSI drive transport on top of firewire
2) plug in your ipod. run "dmesg", the output at the end should have a bunch of messages about connecting and registering your ipod....
3) #2 will show sda, or sdb, etc....update /etc/fstab accordingly
4) the reason that you see sda1, sda2, etc. is that the "a" or "b" is the device number, and the "1", "2" ,etc it the partition number....on an ipod, from my experience (can't confirm this 100%), your music resides on sd[x]2.
5) unplug and reattach your ipod....check out /mnt/ipod and see if it has been mounted...if things don't work, then there is one more thing to try - there are problems with ipods and the ieee1394 (firewire) driver....try unplugging your ipod, running 'rmmod ieee1394 ohci1394 sbp2', then 'modprobe ieee1394 ohci1394 sbp2'

Also, make sure that fstab matches the type of format on your ipod - windows = smb, mac=hpfs.

good luck....

---

