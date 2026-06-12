---
title: "Broken 9.04 Upgrade on Dell XPS 1730"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by lbravo on 2009-04-25
Hello,

I attempted to upgrade my 8.01 install.  It took forever due to download times.  First it upgraded me to 8.04, then offered me the 9.04 upgrade, which I accomplished.  It booted once in 1024 video.  On reboot, all I get is a black screen with a blinking cursor.  I booted to repair mode, and then I get a command prompt.  I have no clue as what to do next.  Please help!

L.

---

### Post by itnet7 on 2009-05-07
> **lbravo said:**
> Hello,

I attempted to upgrade my 8.01 install.  It took forever due to download times.  First it upgraded me to 8.04, then offered me the 9.04 upgrade, which I accomplished.  It booted once in 1024 video.  On reboot, all I get is a black screen with a blinking cursor.  I booted to repair mode, and then I get a command prompt.  I have no clue as what to do next.  Please help!

L.

L. 

I have a dell XPS 1730 and built it up using the 9.04 CD. I have not had any issues as you are describing. My laptop has the Dual NVIDIA configuration, do you have Nvidia, Intel, or ATI? 

One other thing you can try quickly is when the machine is booting hit esc to edit the boot parameters like this: 

1. Reboot your computer
2. Hit “Esc” when prompted in order to enter the GRUB menu.
3. Select the proper kernel and hit the letter “e” to edit.
4. Arrow down to the Kernel line, and hit the letter “e” again.
5. You should see the last few words in the line. Remove the words “quiet splash” and hit enter.
6. Hit the letter “b” to boot the kernel without the Ubuntu splash screen.

[Check out his link for screenshots and even how to add it permanently if you want to]("http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/")

I would have written it from memory, but didn't want you thave further problems!

Thanks, 

Chris C.
itnet7
#ubuntu-us-fl @ freenode

---

