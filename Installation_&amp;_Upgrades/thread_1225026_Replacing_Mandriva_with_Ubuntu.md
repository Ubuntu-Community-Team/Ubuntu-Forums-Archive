---
title: "Replacing Mandriva with Ubuntu"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by unmole on 2009-07-28
I was using Jaunty under wubi. I finally decided to do a full install. I created a new ex3 partition by resizing the partition I previously had Ubuntu wubi installed on but at the last moment was talked into installing Mandriva without even trying it out first. ( :???:I know I'm the worlds greatest moron, but bear with me.) After the resize, ubuntu-wubi would not boot saying the entry was moved,corrupt or something to that effect. So i went ahead and uninstalled Ubuntu wubi without even trying to fix it. (My stupid day I guess.) Now I am stuck with M$-Vi$ta and Mandriva.

                                               Now, can I just pop in the Ubuntu cd and install into the Mandriva partition or will this screw the GRUB ?


Note:If you did not get it from the post, when I power up, Mandriva's GRUB shows up with options for booting either Mandriva or Vi$ta (i.e.) Mandriva's GRUB has taken over the MBR. (not sure if I said that right.)

---

### Post by coffeecat on 2009-07-28
Someone doesn't like Mandriva, I see. :)

Installing Ubuntu to the Mandriva partitions shouldn't be a problem. When you install from the Ubuntu live CD, when you get to the partitioning stage of the installer, select "Manual" - it's the last option after the "guided" options. Assuming you've got just two Linux partitions, a root (/) and swap partition, simply designate the present Mandriva root partition as the root partition for Ubuntu. Mark it for reformatting and choose whichever filesystem you prefer - ext3 for safety, ext4 if you're daring. The installer will detect the swap partition automatically - you don't have to do anything. The installer will also replace Mandriva's grub with an Ubuntu grub and menu dual-booting Ubuntu and Vista - so long as you don't click on the "advanced" button at the last stage, just before the installer does its work. Just be aware that the Ubuntu grub menu is not as pretty as Mandriva's.

If you're not sure which is your Mandriva root partition, or if you have a more complicated partition setup, boot into Mandriva, open a terminal, su to root and post the output of:

```
fdisk -l
```Or if you're **really** fed up with Mandriva ( :wink: ), boot up with the Ubuntu live CD, open a terminal and post the output of:

```
sudo fdisk -l
```

---

### Post by Partyboi2 on 2009-07-28
Hi, you should be able to install Ubuntu onto the Mandriva partition which will wipe it. During the Ubuntu installation grub should be re installed for you.

---

