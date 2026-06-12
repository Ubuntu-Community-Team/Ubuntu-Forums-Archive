---
title: "External Hard Drive"
date: 2008-12-30
forum: Hardware
---

### Post by josher4 on 2008-12-30
Ok, I was just reading a thread about where another person had an external HD and installed 8.10 on it. However when he removed it, the grub loader had and error and he couldn't boot. After some commands, he got it working so that when the drive was not in, windows would load, but if it was plugged in, it would give him the option. I am a complete noob to Linux and I am wondering if there is any way to get the same set-up working for me before I install or during. I have an external drive 250 GB that I want to split (Meaning that I want to have about 80 GB for Linux and the rest for window's files and programs). What is the best way to get this split (The two partitions) and have the configuration of this other user?

---

### Post by josher4 on 2008-12-30
Here is the link to the post I am refering about.
[http://ubuntuforums.org/showthread.php?t=1022392&highlight=External+Hard+Drive](http://ubuntuforums.org/showthread.php?t=1022392&highlight=External+Hard+Drive)

---

### Post by caljohnsmith on 2008-12-30
When you go through the Ubuntu installer, just click the "advanced" button near the end of the installation, and specify to have Grub installed to /dev/sdb or whichever is the drive you are installing Ubuntu to. When you go through the partition setup part of the installer process, that's where you can choose which drive to install Ubuntu to, and it will tell you whether it is /dev/sdb or whichever drive it might be. So if you follow those steps, your other drive will be untouched, and you can keep your drives independent of each other. To boot Ubuntu, you would then need to change your BIOS to boot the Ubuntu drive before your other drive. Let me know how it goes or if you run into problems.

---

### Post by josher4 on 2008-12-30
Ok, I will, I'm going to be getting it in very short while so it might take a little bit but ill let you know.

---

### Post by josher4 on 2008-12-30
Hm... When I plug in my new drive, Ubuntu does nothing. Im going to check windows.

---

### Post by josher4 on 2008-12-30
Ok, it works with windows. Im going to see if I can get it recognized by the partition program.

---

### Post by josher4 on 2008-12-31
Ok, I played with it a while and, to make a long story short, I reinstalled Ubuntu st least 6 times. I had errors and such and I got so deep into my pit of confusion that Windows wouldnt even see the drive anymore. After speaking with other people I finally removed all my partitions on the drive and made a ntfs one that filled it. I might have to resize this so that I can try to re-add Ubuntu again later. Ideas on resizing and Ubuntu on external drives?

---

### Post by caljohnsmith on 2008-12-31
> **josher4 said:**
> Ok, I played with it a while and, to make a long story short, I reinstalled Ubuntu st least 6 times. I had errors and such and I got so deep into my pit of confusion that Windows wouldnt even see the drive anymore. After speaking with other people I finally removed all my partitions on the drive and made a ntfs one that filled it. I might have to resize this so that I can try to re-add Ubuntu again later. Ideas on resizing and Ubuntu on external drives?
What errors did you get? Did Ubuntu install successfully, but then you got errors afterwards when trying to boot Ubuntu? Or did the installer return errors? And by the way, you could use Ubuntu's partition editor gparted (System > Admin > Partition Editor) to resize the NTFS partition if you want.

---

### Post by josher4 on 2009-01-01
Here are some pics.

---

