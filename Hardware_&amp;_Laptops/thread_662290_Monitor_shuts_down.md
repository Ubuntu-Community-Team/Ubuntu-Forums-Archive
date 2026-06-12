---
title: "Monitor shuts down"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by wilsonone on 2008-01-08
Not sure if this is what is happening but it sure looks like it.  The first thing the install program for 7.10  does is shut down the monitor.  Even if I try to turn the monitor on again it just gets turned off.

Is this possible? How do I get past it?

Is there a boot parameter I can change that will over ride it?
Thanks

---

### Post by jespdj on 2008-01-09
Maybe for some reason the video mode gets set to a resolution that your monitor cannot handle. You can try adding the **nosplash** boot parameter to not show the boot splash screen. Doesn't the live CD have options to boot with safe graphics mode, etc.?

---

### Post by wilsonone on 2008-01-09
I tried several boot parameters as suggested by many users in these forums.  Do you think I should just start going through  the list of possible monitor setting ie 'vga =771' until I hit on one that works?  There must be one that works, otherwise how would I ever see anything at all on my monitor in the first place.

Thanks :)

---

### Post by Yellow Pasque on 2008-01-09
I would suggest the alternate install CD. It's usually better with graphics compatibility.

---

### Post by wilsonone on 2008-01-09
Here is what happens.

[LIST]
[*]Insert Alternate install (Xubuntu) into CD drive.
[*]Power on computer.
[*]Wait for splash screen and install options.
[*]Select install and hit enter.
[*]Loading Linux Kernel progress bar appears and grows to 100%.
[*]Monitor turns black and then shuts off/perhaps hibernate?.
[*]Cd continues to spin in drive.
[*]I turn the power button for the monitor on again.
[*]Monitor shuts off/hibernates again.
[*]Eventually the cd stops spinning but in order to turn the computer off I must pull the power cord out of the computer.
[/LIST]

---

### Post by Philosopher on 2008-01-11
Did you fix the problem?  I am being held from installing Ubuntu for the same reason.

---

### Post by wilsonone on 2008-01-11
Yes I did come across a solution to my problem.  I will refer you to the following thread.

[http://ubuntuforums.org/showpost.php?p=4112209&postcount=32]("http://ubuntuforums.org/showpost.php?p=4112209&postcount=32")

Hope it helps.

---

### Post by gartenzwerg2 on 2008-04-10
sorry, wrong thread

*****************
Hi, I don't know if this is your problem, but I had a similar one:

I bought a preconfigured ubuntu system and tried to hitch it up with my old benq fp533 LCD monitor. The system booted ok, but shortly before the login window the monitor told me "out of range". I hitched the computer to another monitor and didn't have any problems there. I tried setting the resolution to one that the LCD could definitely handle, but the problem persisted. Funnily enough, if I entered my login blindly while the monitor told me "out of range", it did work after successful login. It turned out that my graphics chipset (SIS mirage) didn't communicate well with the monitor, to be more specific, the EDID probe of the monitor didn't work with it (that is why my older monitor worked fine).

I finally replaced the driver for the graphic chipset, and it has since worked fine. You'll find the details here (at the very end of the post): [http://ubuntuforums.org/showthread.php?t=463077&page=4](http://ubuntuforums.org/showthread.php?t=463077&page=4)

good luck!

---

