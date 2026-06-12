---
title: "[SOLVED] Grub Error 17"
date: 2008-07-28
forum: General Help
---

### Post by Kg001 on 2008-07-28
Hi I am looking for some help 

Some months ago I decided to try 8.04 while it was in it's pre release version so I loaded it on my WinDozeZP  box using a spare 120G USB2 drive (Remember it was only a trial) I became an instant convert & have only been back into windoze twice since installing Ubuntu. 
My problem is that having shifted house in the interim I am now unable to boot into Ubuntu. Initially I was bombing out with a Grub error 21 After some research on the forums I tried reloading Grub to no avail. I then shifted the linux drive into the main computer as the slave to the windows master disk & tried to get linux to boot using super grub. & am now getting grub error 17 (unable to mount drive) right through this exercise I have been able to access the linux drive if I boot using the Ubuntu Live CD & it all appears to be intact. 

Theoretically I know I should just bite the bullet & reload Ubuntu but after several months I have a big investment of time in the new OS & having always been able to fix my windoze instalation rather than reload I would hate to have to admit that there is one thing windoze does better.. :confused:

---

### Post by Vakman on 2008-07-28
I have seen a thread with this GRUB error just the other day ([http://ubuntuforums.org/showthread.php?t=872006](http://ubuntuforums.org/showthread.php?t=872006)). Try Super GRUB Disc?

---

### Post by Kg001 on 2008-07-29
Lots of good info in that post I now seem to have grub setup correctly as it presents me with the list of boot options as it used to & will boot windoze However if I try & boot Ubuntu it still comes up with grub error 17 (unable to mount this drive) Ideas?

---

### Post by caljohnsmith on 2008-07-29
That's great news that you can boot Windows, because that means your Grub is working fine and that your Grub's menu.lst is intact also. To figure out how to boot Ubuntu correctly, I would boot from a Live CD, then do:
```
sudo fdisk -l
```
Find out which is your Ubuntu partition (under "system" it will say "linux"), mount it and then output the contents of /boot/grub/menu.lst:
```
sudo mount /dev/<partition> /mnt
cat /mnt/boot/grub/menu.lst
```
Post the contents of menu.lst back here, along with the output of the "sudo fdisk -l" command you ran, and we can help set your menu.lst to boot Ubuntu.

---

### Post by geirha on 2008-07-29
Grub error 17 means it can't find the correct partition. If you've repartitioned a harddrive or added or removed a harddrive, then this is probably the reason why you got this error.
Try this:

In the boot menu, select the ubuntu entry and hit **e** to edit it. Then select the root line and hit **e** to edit it. Now change hd**X**,**Y** to something else. Then hit **b** to boot. Keep trying this until you find the correct hdX,Y.

Once you find it, ubuntu will boot. Make sure you edit /boot/grub/menu.lst and change the line ```
# groot=(hd**X**,**Y**)
``` to the proper value, then run ```
sudo update-grub
```

---

### Post by Kg001 on 2008-07-30
> **geirha said:**
> Grub error 17 means it can't find the correct partition. If you've repartitioned a harddrive or added or removed a harddrive, then this is probably the reason why you got this error.
Try this:

In the boot menu, select the ubuntu entry and hit **e** to edit it. Then select the root line and hit **e** to edit it. Now change hd**X**,**Y** to something else. Then hit **b** to boot. Keep trying this until you find the correct hdX,Y.

Once you find it, ubuntu will boot. Make sure you edit /boot/grub/menu.lst and change the line ```
# groot=(hd**X**,**Y**)
``` to the proper value, then run ```
sudo update-grub
```
Thanks everyone for your help 
Grub was trying to boot hda(4,0) instead of hda(1,0) probably because the usb drives were not plugged up the same way after moving house. I am now up & running & can honestly say that with the appropriate level of knowledge fixing a problem in Linux is just as easy as it is with windows. Many people forget that it is unreasonable to expect to be able to fix things without help when they have years of windows experience & weeks or months of linux experience.

---

