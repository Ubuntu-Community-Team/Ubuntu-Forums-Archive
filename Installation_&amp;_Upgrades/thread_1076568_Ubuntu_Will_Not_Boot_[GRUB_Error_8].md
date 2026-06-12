---
title: "Ubuntu Will Not Boot [GRUB Error 8]"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by IcyPenguin on 2009-02-21
Hello,

So I was trying to put Ubuntu on my spare desktop, using a cd did not work and it gave me an I/O error and would not continue with the install. I also burnt 10 more CD's on 3 separate computers, all giving the same error message even when using slowest write speed.__

I used Wubi and I finally got Ubuntu onto my computer, but I wanted it to only have one boot so I removed XP. I did this by deleting Windows by using a partition manager before boot, and now I cannot boot into anything.

I have fooled around with BIOS as well as GRUB both of which to no luck.

The computer is a Gateway GT5058, with plenty of USB ports and CD Drives.

Any help would be greatly appreciated! :D

---

### Post by caljohnsmith on 2009-02-21
Wubi installs Ubuntu inside of Windows, so if you deleted your Windows partition, you probably deleted Ubuntu along with it. It sounds like you may have other issues with that computer though since you can't install Ubuntu to its own partition. Have you checked the HDD to see if it is in good health? If you don't have a diagnostics CD that came with the HDD, you might want to visit the manufacturer's website of your HDD to download their diagnostic software. Let me know how that goes.

---

### Post by IcyPenguin on 2009-02-21
I downloaded the text based AMD64 installer and I am putting that on my computer as I am typing this message, I will tell you all how it goes, and thanks for the inspiration caljohnsmith.

EDIT:

it looks like the AMD64 disk was just what I needed.

---

### Post by caljohnsmith on 2009-02-21
So installing 64-bit Ubuntu worked? If so, that's great news. Hope you enjoy your new Ubuntu install. :)

---

