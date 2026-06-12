---
title: "[SOLVED] uninstalling hardy"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by sandy8925 on 2008-12-17
Hi,

I recently installed Intrepid and now I need to remove Hardy.

The situation is:

Primary master hard disk- Windows XP and Hardy dual boot with grub

Primary slave hard disk- Intrepid with grub

Hardy is only using a single partition. I know I need to format that partition and install Windows' bootloader in the MBR but I don't have a Windows XP cd.

Also I might install some other small distributions in the freed up space so I wanted to keep grub as it is. Unfortunately the boot folder is in the Hardy partition.

Is it possible for me to remove Hardy and create a small partition in the master disk and then install grub to the new partition? If so how do I do it ?

Thanks for the help and for reading my long post.

---

### Post by albinootje on 2008-12-17
> **sandy8925 said:**
> 
I recently installed Intrepid and now I need to remove Hardy.
The situation is:
Primary master hard disk- Windows XP and Hardy dual boot with grub
Primary slave hard disk- Intrepid with grub
Hardy is only using a single partition. I know I need to format that partition and install Windows' bootloader in the MBR but I don't have a Windows XP cd.

If Intrepid is the last Ubuntu installation you did, then it was Intrepid who did the grub install for you.
If XP is still booting fine from the grub menu, then you don't need a XP cdrom, and you can just reformat the Hardy partition to use it for something else.

If you want to install some other Linux distributions in the old Hardy partition, then it's important to keep your current grub install.
You can *manually* add the kernel entries in the grub menu for your other Linux distributions that you'd like to install.

---

### Post by caljohnsmith on 2008-12-17
If you would like specific help setting up a dedicated Grub partition, I can help with that if you want; I just wanted to mention though that one really good alternative to a dedicated Grub partition is to use Grub4DOS inside of your Windows partition, and thus you don't need to give Grub its own partition. Here are specific directions for installing Grub4DOS in case you want to give it a try:

[http://ubuntuforums.org/showpost.php?p=6218177](http://ubuntuforums.org/showpost.php?p=6218177)

Or if you want to make a dedicated Grub partition, just make a super-dinky 5-10 MB ext3 partition, and I can help you install Grub to it if you want. But in order to know what your setup looks like, please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

