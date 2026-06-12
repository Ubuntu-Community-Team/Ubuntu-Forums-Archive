---
title: "I can't start a live session"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by joaquin1 on 2009-03-02
Hello,
I can't start a live session with the 8.10 version live/install CD.
The menu appears correctly, and I've checked memory and CD integrity in the options.

When I try to start a live session, the logo of Ubuntu and the progress bar show up. The cursor inside the bar starts bouncing from side to side several times, but then when the bar starts filling up from left to right, it stops in the middle and the computer locks up and I have to reset.
I'm a complete beginner in Linux. Any help would be very appreciated. Thank you.
Computer specs:
Pentium 4, (2.8 GHz), Intel 865 Chipset
1 Gb RAM DDR 333
Video: Nvidia GeForce 7800GS (AGP bus)
Monitor: LCD Hyundai L90D+ (1280x1024 native resolution)

---

### Post by taurus on 2009-03-02
Try using F4 (safe graphic mode) at the initial screen to see if it boots.

---

### Post by joaquin1 on 2009-03-02
Thanks taurus.
I tried that also.
In fact, I've also installed it in the hard disk (well apparently) but when try to run it from the hard disk the result is the same: it stops in the middle of the progress bar.

---

### Post by taurus on 2009-03-02
At the GRUB menu, hit letter e to edit your kernel and move to the end of the line that starts with _kernel_, remove both **quiet splash**.  Then, hit b to boot.  Now, you will see text printing on the screen.  Post the last thing that it prints before it hangs.

---

### Post by joaquin1 on 2009-03-02
Well, I've done that.
After several screens, the last line says:

init: rc-default main process (4438) terminated with status 139

If you could translate this to normal English ...

Edit: The emoticon is not really an emoticon is an "8" and a ")"

---

### Post by avtolle on 2009-03-02
Try this to see if it helps; when the progress bar quits moving, press and release the power button once to see if the process continues. The problem you are encountering seems to affect a number of laptops, in particular HP/Compaq, and is related, IMHO, to something in the kernel used in 8.10 (as well as Linux Mint6, OpenSUSE 11.1) and a proprietary function of said laptops. If this doesn't help, let us know, and we'll try to go from there.

---

### Post by joaquin1 on 2009-03-02
No, the process doesn't continue.
Exactly what happens is that the bar stops at a quarter of its length (approximately) and 2 o 3 seconds later the screen goes blank.
I've also tried Ctrl-Alt-F1 at that point but nothing; the computer is locked up.
Also, my computer is desktop, not laptop. Thank you for your interest

---

### Post by sgosnell on 2009-03-02
Did you verify the md5checksum before burning the CD?  Did you verify the CD after burning?  Most of the time problems like these are due to a faulty CD.  You might try burning a new CD, but I would suggest verifying the md5checksum before doing that, to make certain the .iso you downloaded is perfect.

---

### Post by joaquin1 on 2009-03-03
Yes, in fact i tried first from a DVD from a book, then from a CD with prior md5cheksum verified in the iso file and then CD verified also after burning.

---

### Post by abn91c on 2009-03-03
try removing compiz and see what happens

---

### Post by joaquin1 on 2009-03-03
What's compiz?
Can't see anything related compiz in the boot secuence.

---

### Post by abn91c on 2009-03-03
> **joaquin1 said:**
> What's compiz?
Can't see anything related compiz in the boot secuence.
compiz is the desktop effects for the OS loade by default in ubuntu(no prompts)some video card cant handle the visual effects and it locks up the systems in a terminal the commands are
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by clarknova on 2009-03-03
Other boot options you could try are "acpi=off" or "noapic". When the computer is booting and you see the progress bar try hitting alt-leftarrow a few times to watch the boot messages. Do this before it locks up to try to get a sense of where it is hanging.

---

### Post by joaquin1 on 2009-03-04
abn91c:
thanks, but i can't go to terminal mode. Ctrl-Alt-Fx doesn't work. The computer is hung up.
 
clarknova:
i've tried your suggestions and dissable acpi and apic but is all the same.
 
i think the key is to understand what this line means: ( :confused:)
 
**init: rc-default main process (4438 ) terminated with status 139 **
 
it is the last line displayed on screen before it hangs up.

---

### Post by abn91c on 2009-03-04
look at this report a similar problem with add on video card, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229753](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229753)

---

### Post by joaquin1 on 2009-03-04
Well thanks abn91c.
Sort of relief i am not alone in this struggle

---

