---
title: "Please help.  (total newb)"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by Esteria on 2009-10-07
I had a problem with windos vista locking up so my friend installed Ubuntu 9.04 on my computer. Because windows was in safe mode he had to select full instill without a partition to get it to work. The only OS on my machine now is Ubuntu. I have been trying to instal vista back on my computer for just my games but iw will not install off the dell cd. If I buy a windows XP program and wish to install it with a half and half hard drive partition.... how do I do this? I do not want to go buy a copy of xp to not have it instal. Please help. I like what I have been able to get running with ubuntu and wish it to be my main OS but i need windows xp for gaming.

---

### Post by MelDJ on 2009-10-07
> **Esteria said:**
> I had a problem with windos vista locking up so my friend installed Ubuntu 9.04 on my computer. Because windows was in safe mode he had to select full instill without a partition to get it to work. The only OS on my machine now is Ubuntu. I have been trying to instal vista back on my computer for just my games but iw will not install off the dell cd. If I buy a windows XP program and wish to install it with a half and half hard drive partition.... how do I do this? I do not want to go buy a copy of xp to not have it instal. Please help. I like what I have been able to get running with ubuntu and wish it to be my main OS but i need windows xp for gaming.

did you set your BIOS to boot from cd when you tried installing vista?

---

### Post by Esteria on 2009-10-07
no.  I don't even know how to do that.   :(

---

### Post by MelDJ on 2009-10-07
when the dell boot screen comes up when you on your computer, press F12. then select to boot from your cd drive. i am assuming that my dell and yours uses the same BIOS though

---

### Post by Esteria on 2009-10-07
if this works, will it be able to install windows and set a partition for it or do i need to create a partition for it first?  If i need to create a partition first..... how?   I can't try this untill i get home from work.

---

### Post by MelDJ on 2009-10-07
i don't know about vista but installing XP will require you to format your whole disk into fat32 or ntfs. so if ubuntu is on the same drive, i believe it will be formatted. try googling about it though:)

---

### Post by MelDJ on 2009-10-07
this might be helpful: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Esteria on 2009-10-07
ok.  i will mess with it when I get home.  Thank you for the info and I am sure I will have more questions. :)

---

### Post by MelDJ on 2009-10-07
be sure to come back here and ask though:)

---

### Post by Esteria on 2009-10-07
oh i will.  Google has not been my friend so far.  I can find all kinds of info on installing ubuntu and dual boot when windows is installed but not the other way around.   especially when windows was deleted when ubuntu was installed.    Thanks for your help...so far.  haha

---

### Post by raymondh on 2009-10-07
Let's take a look at what your HD contains

In ubuntu ... access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

Small L (not 1 nor I).  You'll be asked for your password which when you type will not be shown.

Copy and paste back the results in your next post.  From this, we can quickly see if windows is still there.  If it is, the workaround may be cheaper and easier than buying an XP disc ;)

If you want, another tool to analyze is the boot info script (see signature below) which you'll have to download and save to your desktop.  Once downloaded, open a terminal and type this :

sudo bash ~/Desktop/boot_info_script*.sh

It'll produce a results.txt file which wil be saved to your deskptop as well.  Copy and paste that in your next post.  It'll be a long report so to save on space, highlight the whole text and wrap it in codes (the # sign among the tools in the post box).

Happy ubuntu-ing.

---

### Post by Esteria on 2009-10-07
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37785   303507981   83  Linux
/dev/sda2           37786       38913     9060660    5  Extended
/dev/sda5           37786       38913     9060628+  82  Linux swap / Solaris


That is what i got for your first option.  It looks as if windows is not there at all.   I will look into your second part now.

---

### Post by raymondh on 2009-10-07
> **Esteria said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37785   303507981   83  Linux
/dev/sda2           37786       38913     9060660    5  Extended
/dev/sda5           37786       38913     9060628+  82  Linux swap / Solaris


That is what i got for your first option.  It looks as if windows is not there at all.   I will look into your second part now.

Yes .. windows is not there.  Various options as you mull over a windows install.

1.  windows as a virtualized guest with Ubuntu as the host.  I recommend virtualbox as the tool.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

2.  windows in it's own partition.  

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

Remember (if you follow this guide) that when you install windows, only select the NTFS partition ... nothing else.  Also, you will have to reinstall GRUB as windows will overwrite the bootloader.

Back-up your valuable data/files.  Be patient as a windows install takes a long time.  Post back if unsure about anything before proceeding.

Regards,

---

