---
title: "No Grub list menu on boot"
date: 2008-07-22
forum: General Help
---

### Post by nagius on 2008-07-22
Hello,


Need some help I used to boot ubuntu using the grub menu list, but since I formatted by mistake( well windows did automatically) my second hard drive with windows, I do not see the grub menu list to boot ubuntu, I think that grub was installed on the windows harddrive, but how do I make my ubuntu first hard drive (with only ubuntu) bootable?

Hope you understand.

---

### Post by northern lights on 2008-07-22
[SuperGrubDisk]("http://supergrub.forjamari.linex.org/") will do the trick.

Download, burn image to CD, reboot from CD, restore grub.

---

### Post by pmlxuser on 2008-07-22
Just re-install grub; following instructions may help you do that

This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

```


sudo grub

```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```


find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```


root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```


setup (hd0)

```
Finally exit the grub shell
```


quit

```
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.

copied from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by nagius on 2008-07-22
Thanks for your help, I tried the sudo grub which was easy to follow, but when I reboot grub did'nt load then I tried the super grub disk and I got my old grub list back but it now says error 15 file no found.

---

### Post by northern lights on 2008-07-22
> **nagius said:**
> then I tried the super grub disk and I got my old grub list back
Well, we're a step further.

> **nagius said:**
> but it now says error 15 file no found
When does that message occur? When selecting the latest Ubuntu from the grub menu (i.e. Windows can be selected)?

Should that be the case, boot from the LiveCD and post a partition table as well as the output of ```
cat /boot/grub/menu.lst
```

---

### Post by nagius on 2008-07-23
No need, started playing around with the super grub disk and finally I got it working tried everything, so I don't know what actually was the problem. 

Well sorted, thanks for your help.

---

