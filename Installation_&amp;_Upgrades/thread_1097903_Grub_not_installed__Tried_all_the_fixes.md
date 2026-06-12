---
title: "Grub not installed?  Tried all the fixes"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by markdjones82 on 2009-03-16
All,
  I have installed ubuntu 8.04 but I cannot get it to boot into it or even get to a grub screen.

When i boot into the livecd and try to run setup(hd0) it doesn't work.  If I try to grub install it doesn't work.  None of the solutions I have found work.

When I look at the /boot directory, grub wasn't even there.  Any help?  I have tried reinstalling ike 10 times.  formatting the disks etc.

Anyway to wipe the Mbr completely?  fdisk /mbr doesn't even work.

---

### Post by meierfra. on 2009-03-16
> I have installed ubuntu 8.04 but I cannot get it to boot into it or even get to a grub screen.

What error messages to you get?
If you have more than one harddrive, you might try switching the boot order.


> When I look at the /boot directory, grub wasn't even there. 
Did you look in the boot directory of the live CD, or did you look in /media/disk/boot (or where ever Ubuntu was mounted)
Did you get any error messages while installing Ubuntu?
Did you check the disks for defects?

> Any help?

In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


```
sudo bash ~/Desktop/boot_info_script*.sh

```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.


> Anyway to wipe the Mbr completely? fdisk /mbr doesn't even work. 


Try 

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Here "/dev/sda" needs to be replaced by the device name of your windows partition. Use "sudo fdisk -lu" to determine the device name. But I suggest to troubleshot your booting problem first.

---

