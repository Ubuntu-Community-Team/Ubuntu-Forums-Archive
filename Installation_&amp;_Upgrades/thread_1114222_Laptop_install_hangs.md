---
title: "Laptop install hangs"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by dwcth on 2009-04-02
Hello,
I have a Toshiba Satellite M115 with Windows XP. I've tried to install 8.10 using the live CD but the system hangs every time. It hangs after I select 'English', the I choose "install without changing anything on your system ..." and the progress bar bounces back and forth, and then the progress bar begins to load from left to right. It gets about 3 bars full and it freezes - the only thing I can do is hard boot to make it work again.

The CD is good - I used it for my desktop and ran the "check disk for defects" test... I've searched the forum but have only found a few post and no real solution... Any ideas?

---

### Post by Partyboi2 on 2009-04-02
Try removing the splash screen (loading bar) to see where it is freezing. At the main menu of the live cd press F6 and change 'splash' to 'nosplash' then press enter to boot.

---

### Post by dwcth on 2009-04-02
It displays this error constantly while running 

"Buffer  I/O error on device sr0. logical block 357795"

then it stops with:

"cs: IO port probe 0x3e0-0x4ff:"

---

### Post by upchucky on 2009-04-02
if the laptop has any pcmcia cards, remove them, also check see if internal modem can be disabled in the bios, sometimes an internal lucent winmodem messes up linux, or a pcmcia is hogging a resource, pcmcia can be set up later manually if needed,lucent winmodem can be shoved up Micro..oh nevermind.

other than this any other devices should work, but if you have some funky device attached, disconnect it for the time being.

---

### Post by paradigm2 on 2009-04-02
> **dwcth said:**
> 
"Buffer  I/O error on device sr0. logical block 357795"


I pretty much get the same errors.  After burning ten CDs at 4x speed, alternative and the regular.  Checked all the MD5s on the ISOs, turned off acpi.... same thing.

[http://ubuntuforums.org/showthread.php?t=1114556](http://ubuntuforums.org/showthread.php?t=1114556)

---

