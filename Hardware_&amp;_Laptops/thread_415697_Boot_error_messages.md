---
title: "Boot error messages"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by rmfought on 2007-04-20
Just installed Ubuntu Feisty amd64 onto my Acer Ferrari 4005 ...

The first error I get is

"MP-BIOS : bug: 8254 timer not connected to IO-APIC"

though it doesn't seem to affect anything (yet, at least).

The second I just started getting after installing xubuntu-desktop - and this one prevents the computer from successfully booting:

"bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed"

Yarg!  What happened to my shiny new Ubuntu install?

---

### Post by rmfought on 2007-04-22
Well, the second error has to do with the bcm43xx module needing specific firmware to run correctly, which I apparently don't have.

I tried blacklisting the bcm43xx module, and it did get rid of the error message - but it still failed to boot.  It just hung up where I would have gotten the error message.

---

### Post by se2131 on 2007-04-24
[http://ubuntuforums.org/showthread.php?p=2528532#post2528532](http://ubuntuforums.org/showthread.php?p=2528532#post2528532)

---

### Post by arijel on 2007-04-25
Regarding the second problem. I have installed the bcm43xx-fwcutter just after I installed the Ubuntu Feisty and the problem was solved. You can try this by doing:
sudo apt-get install bcm43xx-fwcutter and when it prompts you to download the driver and extract firmware from it press YES. After that reboot. This worked for me. I'm using HP nx6325 (AMD turion TL-52 x2) with Broadcom Dell 1390 wifi card.
I just saw that you installed 64bit version, mine is 32bit, maybe you should switch to latter.

---

