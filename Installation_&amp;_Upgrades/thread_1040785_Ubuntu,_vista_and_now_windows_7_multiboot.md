---
title: "Ubuntu, vista and now windows 7 multiboot?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by colint1 on 2009-01-15
heres the story:
     -got a new computer with vista installed
     -then i got a new harddrive to store more stuff in  ;p
     -i found out about ubuntu, so i put it on the 2nd harddrive
     -everything went fine, and i got a menu when i boot so i can choose what 
OS i want
     -now i got a copy of windows 7 beta so i thought "why not?" 
     -i partition the drive that ubuntu is on with the live boot so its around 50% 50% split
     -then i formated the half of the harddrive that i wanted win7 on to NTFS 
     -i installed win7 on the partition 
     -but now when i boot up i get a slightly different menu and only the choice's "windows 7", "windows vista" or some debugging tools for both
     -also i could never view the parts of the harddrive that had ubuntu on it in any windows os (strange)
      
anyways, just wondering how i would go about getting all 3 on that bootup menu, i am 100% sure i didnt do anything to the ubuntu half partition, just need to know how to access it ;p

---

### Post by wildmanne39 on 2009-01-15
Hi, when you install dual boot you always have to have windows installed first because windows always wants to be the only operating system. You can run windows inside linux in virtual box as long as you have aleast 2 gigs of ram. It is a great way to run windows and it frees up disk space. Look at the posts about virtuualization.

---

### Post by colint1 on 2009-01-15
yea ive heard about that, i was just hoping for any other ways
would the way to go now is to  just install ubuntu again on the same partiton it used to be on from the live cd? (formating that half of the harddrive while im at it?)

---

### Post by drjonze on 2009-01-15
Hey,

I'm triple booting Vista, 7 and Ubuntu on my laptop. I had Ubuntu and Vista then Windows 7. Its better to install Ubuntu last as Windows will overwrite Grub and you won;t be able to boot intop Ubuntu. This happened to me. I followed this and it fixed the problem: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by beattyml1 on 2009-01-15
I don't know much about the in's and outs of windows 7 but I do know about why you can't see your ubuntu partition in windows, you see ubuntu and most linux versions use the ext2 or ext3 filesystem format which is not able to be read by windows, hope that answers that question:)

---

### Post by drjonze on 2009-01-15
> **beattyml1 said:**
> I don't know much about the in's and outs of windows 7 but I do know about why you can't see your ubuntu partition in windows, you see ubuntu and most linux versions use the ext2 or ext3 filesystem format which is not able to be read by windows, hope that answers that question:)

There's software available for Windows that will allow you to see your linux partition.

---

### Post by logos34 on 2009-01-16
> **drjonze said:**
> There's software available for Windows that will allow you to see your linux partition.

+1

[fs-driver]("http://www.fs-driver.org/download.html")

(vista is supported, so it's a good bet it'll work on windows7)

---

