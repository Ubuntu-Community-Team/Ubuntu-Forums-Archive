---
title: "Grub error 17 on installation of Karmic Koala"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-10-29
Hello, I am upgrading to Karmic Koala today, and I wanted to create a video on how to do this as part of my series of Linux videos, to share Karmic love with the world!

Unfortunately I am having problems on boot. Here is my situation:

I had Jaunty 64-bit installed on my machine, dual-booting with Windows. I have 3 HDDs in the computer, and Windows was the primary partition on the WD Raptor that also held Jaunty's swap, /, and /home partitions.

From a Jaunty live CD I deleted the Jaunty partitions in preparation for installation (I wanted to show unpartitioned space like someone would see if they made room on their Windows hard drive for dual booting). I then installed Karmic Koala on three partitions: /, /home, swap.

So far, so good! Unfortunately on trying to boot to my snazzy new distribution, I was greeted with a Grub Error 17. I'm not quite sure how to proceed, as I understand that Karmic Koala is running Grub 2, correct?

Thanks!

---

### Post by Nixie Pixel on 2009-10-29
Sorry for the instant reply, but when I type "sudo grub" in the live CD terminal, I am told that grub is not installed.

Am I missing something?

:(

---

### Post by Dimarchi on 2009-10-30
Maybe. Maybe not. One thing that you might check out is that you are booting from the correct partition (see BIOS settings for that one initially). I got error 15 after fresh install which was fixed in BIOS by selecting the other hard drive I have.

---

### Post by Soul-Sing on 2009-10-30
karmic uses grub2 afaik know, maybe there is problem....

---

