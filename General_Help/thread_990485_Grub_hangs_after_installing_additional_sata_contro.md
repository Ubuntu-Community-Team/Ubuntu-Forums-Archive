---
title: "Grub hangs after installing additional sata controller"
date: 2008-11-22
forum: General Help
---

### Post by Abstract40 on 2008-11-22
Hi Everyone,

I've got a really nasty problem. 
In the office I run an Ubuntu server 6.*. It had 2 ide disk and one pci sata controller with one additional sata disk.
Now I've added a additional pci sata controller with 2 disks. When I try to start the server up Grub hangs at:

 "grub loading, please wait"

When I disconnect the two additional disks it works fine again. I understand why Grub isn't loading, but I can't find a solution for it. It drives me crazy!

Does anyone has a solution for this?

Thanks Arian

---

### Post by gTinker on 2008-11-23
There is really not much troubleshooting information in your post to work with. However, from what you stated I would look at the order in which the device nodes are enumerated. Since you state you know why it isn't working, I expect I'm answering someone who is knowledgeable about their system. You'll probably need to determine the new order in which the system enumerates the drives when the new drives are installed and amend your GRUB install to reflect the new device order. Likely even have to reinstall the GRUB MBR with the correct partition for /boot under the new device order.

---

### Post by sdowney717 on 2008-11-23
perhaps supergrub will help you out
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by caljohnsmith on 2008-11-23
Your problem sounds like it might be a classic case of where Grub is installed to the MBR (Master Boot Record) of some drive other than the drive that has Grub's boot files, and then when you add additional drives, the boot order is changed and Grub looks on the wrong drive for its boot files. How about connecting your additional SATA drives, boot your Live CD, open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". Next, please boot the Super Grub Disk that sdowney717 linked to, and when you get the main menu, press "c" to get the command line. Then type the following without pressing enter:
```

grub> geometry (hd

```
Instead, press TAB for tab-completion to see a list of your drives, starting with (hd0). Then to see the size and partitions of each drive starting with (hd0), use:
Code:
```

grub> geometry (hd0)

```
And press enter. Use the output of the geometry commands to figure out which of your drives correspond to (hd0), (hd1), (hd2), etc. and please let me know what they are. And lastly do:
```
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
And let me know the output of those commands. That will give us enough information to reinstall Grub so that it points to the correct drive/partition for its boot files with your new drives connected. :)

---

