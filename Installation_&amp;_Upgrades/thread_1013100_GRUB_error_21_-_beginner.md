---
title: "GRUB error 21 - beginner"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Eruditio on 2008-12-16
Hi all,

I'm a complete beginner with the whole Linux thing. I have a Live CD with Ubuntu 8.04 LTS on it. I installed Ubuntu to my external USB HD (clean install) and didn't do anything with my internal HD, which has Vista Home Premium installed on it.

Whenever I try and boot up, whether the external HD is connected or not, I get the error message: "GRUB error 21".

I've been doing lots of reading and have enlisted the help of several friends, but we can't seem to solve it. I have a relatively good understanding of the problem (correct me if I'm wrong): the BIOS points to my internal HD for the boot loader (GRUB), but it's not there - it has been moved/installed to my external HD. Since my external HD is connected via USB, I cannot point the BIOS to it.

It seems to me that all I need to do is install GRUB to my internal HD... I have no idea how to do that. I *think* that the partition I boot from (for Vista) is sda1... I think... like I said, I'm a complete novice and really have very little idea about what's happening. This is basically the sum of my knowledge. 

If anyone could help and explain in basic terms and when you need to give specific advice, explain *step-by-step* and explain every term that you use... if you use an acronym that I haven't used here, for example, please say what it stands for and what it actually is, as I am unlikely to guess what it is from the name!

Thanks :)

---

### Post by caljohnsmith on 2008-12-16
In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info8.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info8.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post, or you can attach the file itself to your post. That will help clarify your setup and what your problem might be.

---

### Post by therob1 on 2008-12-16
i get the same problem, i had vista with 2 1tb drives setup with motherboard raid 0. my spare 250gb disk got ubuntu 8.10 installed on it and reboots fine. soon as it tries to load i get the same message.

is this likely to be a sata / raid driver issue? i cant seem to get ubuntu or my vista install to work?!

---

### Post by Eruditio on 2008-12-17
I've managed to fix the problem so that I can boot into Vista as normal. Turns out there was a problem with the MBR when I installed Ubuntu onto the external HD. For anyone having a similar problem, follow these instructions (worked for me!):

1. Boot up computer using Microsoft Windows Bootable Disc
2. Configure language settings as instructed by the Windows Bootable Disc
3. When prompted, click "Repair your computer"
4. Click "Command Prompt" from the System Recovery Options
5. Enter: BootRec.exe /fixmbr
6. Press Enter

You should receive a confirmation message in the command prompt window - restart your computer and you should be able to boot into Vista!

---

### Post by Eruditio on 2008-12-17
I should mention that I still don't know how to boot from my external HD, so would appreciate any help on that :)

---

