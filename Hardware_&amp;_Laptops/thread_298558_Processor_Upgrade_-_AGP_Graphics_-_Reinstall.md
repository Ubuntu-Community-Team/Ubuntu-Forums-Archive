---
title: "Processor Upgrade - AGP Graphics - Reinstall"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Twister594 on 2006-11-12
Hi, I recently got a new motherboard and processor for my computer - an A7V333 and an AMD Thunderbird 1400.  When I set the FSB multiplier to either 14x and 100MHz or 10.5 and 133MHz (the second being the one I expect to work) I can run through bios fine and it checks all the hardware and can boot into the live cd menu.  However, when I try to boot up the live cd, it displays all the graphics perfectly until it tries to load x.org.  At this point, I get a few gibberish signals and then the cursor with the normal brown background.  However, it fails to continue and blanks white, only to reload x.org again.  It continues this until it tries to display a garbled error message that I cannot read.

PS, please do not assume that I know what I am doing.  This is the first computer that I've practically built.  I have swapped out everything but processors before this, but this is the first processor I have ever installed.  Also, I have tried multiple graphics cards, all AGP, well, at least they go in the AGP slot.

Thanks, and if there is a better website for me to go to, please let me know.  (I'm not sure if this is a problem with me, Ubuntu, or my hardware.)

---

### Post by David Corrales on 2006-11-13
Hmm maybe there's a problem auto detecting your monitor settings, have you tried with another one?

---

### Post by Twister594 on 2006-11-13
It could be the monitor, but I will try that later today.  I've tried using a DVI graphics card and a VGA, but the DVI displays the gunk and the VGA displays "cannot display this mode".  My monitor is a Dell 2005fpw.

The DVI is one of those weird "Long" 'DVI' with 30 or so pins, and I am using a splitter to convert that into normal DVI for my monitor.

I am not sure if it is just Ubuntu or not, Ubuntu is my main operating system, is it possible that Windows or Knoppix would run?

Thanks.

---

### Post by David Corrales on 2006-11-13
You can try knoppix to see if something is amiss. Also, I suggest you look into your monitor manual o backside and see the exact horizontal/vertical refresh rates. Then, input those in the file */etc/X11/xorg.conf*.

---

### Post by Twister594 on 2006-11-13
More information, my graphics card is an ATI RAGE 128 Ultra 16MB.  Fedora detected it as a Radeon RV100 QY.

My next guess would be somehow to install Edgy in terminal mode seeming as I cannot even boot into the live cd in safe graphics mode.  Any clues as to how to do this would be great, I *think* I need the text installer cd, but I'm not sure.  After that I would probably try installing the ATI drivers from terminal and seeing where I get.  Anything else or better?

---

### Post by Twister594 on 2006-11-17
Problem has been resolved.  Turns out that sometimes the Athlon/Duron processors have JPEG algorithm errors that prevent the graphics from displaying.  I tested this by booting into Windows and downloading a JPEG to my desktop.  Double clicking on it opened up Windows picture and fax viewer, which did not display the image.

---

### Post by zgornel on 2006-11-17
How did you solve the problem ?

---

### Post by Twister594 on 2006-11-17
I replaced the Thunderbird 1400 with a known working Athlon 750.

---

