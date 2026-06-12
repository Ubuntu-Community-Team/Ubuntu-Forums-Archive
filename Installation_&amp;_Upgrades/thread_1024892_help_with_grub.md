---
title: "help with grub"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by VeeDubZ on 2008-12-29
i have xp installed on my primary hard drive(C:/) and I've installed Ubuntu 8.04 to my second hard drive(D:/) as i(and my partner) wanted to keep them separate and immediately after install i got "error 21" from grub so i used super grub to restore the MBR to windows to ask here how to make it work/ ask me which os to boot from....

so any ideas?

---

### Post by Elfy on 2008-12-29
Try rebooting with supergrub and getting it to reinstall grub if that doesn't work boot the livecd and folllow this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

If you still have problems open a terminal from the apps >Accessories menu of the live cd and run this command 

```
sudo fdisk -l
```

---

### Post by VeeDubZ on 2008-12-29
> **forestpixie said:**
> Try rebooting with supergrub and getting it to reinstall grub if that doesn't work boot the livecd and folllow this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

If you still have problems open a terminal from the apps >Accessories menu of the live cd and run this command 

```
sudo fdisk -l
```


using super grub and re-installing i got the list of os like 

ubuntu 8.04
ubuntu 8.04(safe mode or similar cant remember)
windows xp

problem with this was that when i chose the ubuntu options i got error 21 again although the xp option did work.

following the link you gave i was instantly given error 21 upon reboot

the outcome of the fdisk:-

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bdbe69b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb583b583

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7165    57552831   83  Linux
/dev/sdb2            7166        7476     2498107+   5  Extended
/dev/sdb5            7166        7476     2498076   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 16.7 GB, 16777216000 bytes
255 heads, 63 sectors/track, 2039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00054202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1949    15655311   83  Linux
/dev/sdc2            1950        2039      722925    5  Extended
ubuntu@ubuntu:~$ 


```


im unsure where to go from here

---

### Post by cariboo on 2008-12-29
Can you bootup the LiveCD and select boot from harddrive from the menu and boot into your Ubuntu installation? If so you should be able to repair grub, by following the instructions [here]("http://help.ubuntu.com/community/GrubHowto").

Jim

---

### Post by Blonddeeni on 2008-12-29
Hi there. Just saw your post on "grub" and hope that I'm not interrupting too much. 
This link may help.
(It has certainly helped me with having four operating systems on the same machine)

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

I tend to mess about with the "hard Way", and use a live CD version of knoppix.

Cheerio and good luck.

---

### Post by caljohnsmith on 2008-12-29
So are you getting the Grub menu on start up now or a Grub error before seeing the menu? If you get the Grub menu, how abut selecting the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hd0,0) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. If you get the Grub error before seeing the Grub menu though, how about instead doing the following from your Live CD:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Elfy on 2008-12-29
Don't think root hd 0,0 will work - that's a ntfs drive

Could be an issue with sdb - > Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Not a message I've seen before.

Might be  hd1,0 or hd2,0

---

### Post by caljohnsmith on 2008-12-29
> **forestpixie said:**
> Don't think root hd 0,0 will work - that's a ntfs drive

Could be an issue with sdb - 

Not
I agree, (hd0,0) won't work if he has Grub installed to the MBR of his Windows drive, but he said he all ready reinstalled a Windows MBR to his Windows drive with the Super Grub Disk. So if he installed Grub to his Ubuntu drive and is booting the Ubuntu drive, then (hd0,0) should work. If he posts the output of meierfra's script, I think we will know a lot better and won't have to guess. :)

---

### Post by Elfy on 2008-12-29
aah - that wasn't there when I posted - just your root is hd0,0  ;)

---

### Post by VeeDubZ on 2008-12-30
right i have grub installed to the main hard drive and can boot to windows but not to Ubuntu so once i am back at that pc i will try editing the grub loader as advised in the post above....im hopeful that will work.

thanks for the help i will let you know how i get on with it.

---

### Post by VeeDubZ on 2008-12-31
yep that has sorted it, it was hd2,0 easy fix really.....thanks for the help

---

