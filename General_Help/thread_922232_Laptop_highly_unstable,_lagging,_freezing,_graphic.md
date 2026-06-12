---
title: "Laptop highly unstable, lagging, freezing, graphical corruptions."
date: 2008-09-17
forum: General Help
---

### Post by richandcreamy on 2008-09-17
My laptop screen sometimes flickrs then hangs for a moment to close to a minute.  Sometime it just freezes or the graphics on the screen start to splinter as shown in the attachment below.  The caps lock light also blinks when the system completely locks up.  I'm running the latest Ubuntu on a HP DV9000.

How do I even begin to try to diagnose this problem?

---

### Post by richandcreamy on 2008-09-17
Ok I think my laptop is ok as long as I don't do any internet browsing.  That includes firefox, flock, and opera.

---

### Post by prshah on 2008-09-17
> **richandcreamy said:**
> 
Sometime it just freezes or the graphics on the screen start to splinter as shown in the attachment below.  

> **richandcreamy said:**
> Ok I think my laptop is ok as long as I don't do any internet browsing.  That includes firefox, flock, and opera.

As a first step, you should (temporarily) turn off desktop effects (System-Preferences-Appearance-Visual Effects-None).

Second, do you think it possible that if you avoid flash-based websites (temporarily) your system is performing OK?

Third, do you feel that your system is hanging up when playing, or just about to play, audio?

Post back results with first step, and your impressions about 2nd and 3rd points.

---

### Post by richandcreamy on 2008-09-18
Turning off effects actually made a drastic difference and I was able to work on my laptop tonight for 2.5 hours till the first crash.  This time I was getting blue and yellow streaks before the lock up.  This was while running 10 tabs in firefox some flash some not.  I was playing music the entire time but the lock up occurred after starting a new mp3.  Upon restarting I did get a few of the lines and a little lag but it seems ok for now.  I really wonder if an update has somehow made things get all funky.  =/

---

### Post by prshah on 2008-09-18
> **richandcreamy said:**
> Turning off effects actually made a drastic difference and I was able to work on my laptop tonight for 2.5 hours till the first crash.

Next step will be check if the graphics card is setup properly, for full performance. Once this is done, you should be able to use desktop effects in all their glory.

As far as I recall, the DV9000 series uses nVidia for graphics. Open a terminal (Applications-Accessories-Terminal) and give the commands below for more information on your graphics subsystem and setup```
lspci -v | grep -i -A 5 -B 1 -E graphics\|vga\|display
glxinfo | grep -i direct
cat /var/log/Xorg.0.log | grep -i graphics

```

---

### Post by richandcreamy on 2008-09-18
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at dc000000 (64-bit, non-prefetchable) [size=16M]

direct rendering: Yes

Hmm last command doesn't return back anything.

Shall I try running envy?

---

### Post by richandcreamy on 2008-09-18
On the second freeze of the night, after restarting I was getting graphical errors while the computer was booting.  Then it would hang with multi color blocks on the screen before reaching the splash page.  Tried restarting 4 times after that with same result.

I tried restarting in a kernel that would force me into low graphics mode that worked.  Then restarted again as normal and was finally able to log in.

Strange!

---

### Post by prshah on 2008-09-18
> **richandcreamy said:**
> 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30bb

direct rendering: Yes

Hmm last command doesn't return back anything.

Shall I try running envy?

Well your graphics look OK to me (esp since direct rendering is enabled), but I don't have much experience with nVidia/ATI cards. The "unknown" part in subsystem worries me.

You can try one of the following (either / or, don't try both).

EITHER:
Press Alt+F2, and give the command ```
gksudo displayconfig-gtk
```, click on the "Graphics Card" tab, and make sure that an appropriate nVidia driver is selected. (Either proprietory or open-source "nv").

OR:
As you've suggested, use envy.

---

### Post by richandcreamy on 2008-09-18
So far so good, just ran Envy and nothing strange has happened yet.  Websites that have youtube videos or attempting to play a video will no more often kill my web browser but the overall system is ok.

I'll post again if I crash >_<

---

### Post by richandcreamy on 2008-09-18
Starting to show signs of instability again.  Text is missing on webpages and on menus in firefox.  Tomboy notes and Twitux don't seem affected though.

---

### Post by richandcreamy on 2008-09-20
After that last restart system lasted about 6 hours till lines started showing up.  Is there some sort of slow desegregation somewhere?

---

### Post by richandcreamy on 2008-09-20
System lasted about 3 hours till crapping out again.  Before restarting both cpu's were running at most 20%

Any other tests I can run?

---

### Post by richandcreamy on 2008-09-26
I reinstalled 8.04 and after 2 days I have the same errors!  What can be going on here?

---

### Post by patrickballeux on 2008-09-26
You seem to have a conflict between your graphic card and you network card.

I had the same problem with my Averatec Laptop where doing 3d stuff froze the computer when doing network stuff at the same time.

The solution was to put in the boot options this line :

acpi=noirq

As root, open /boot/grub/menu.lst with gedit or any other editor...

Add this option at the end of your boot line,

```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=26b53312-8165-4dff-aecc-7508a04da50e ro quiet splash acpi=noirq
initrd		/boot/initrd.img-2.6.24-21-generic 
quiet

```

Don't know if it will work for you, but it did the trick for me.

Good luck!

---

