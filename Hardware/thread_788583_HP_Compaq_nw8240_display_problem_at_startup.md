---
title: "HP Compaq nw8240 display problem at startup"
date: 2008-05-09
forum: Hardware
---

### Post by Dagur on 2008-05-09
Hi,

When I start up Ubuntu I get a weird "wash out" effect where the screen gradually becomes white and then completely blank. Everything is running in the background and seems to be working. To get the display to work I have to do these steps

1. Enter grub and boot in recovery mode
2. Select xfix
3. Select "resume booting normally"

After that, everything works just fine. 

Any help or suggestions are appreciated.


btw, I've had this happen on Vista as well (on the same laptop), but it's much rarer

---

### Post by EXCiD3 on 2008-05-09
Ive got a HP dv9000t and have experienced this during hibernate/suspend and resuming from them in previous versions of ubuntu. I havent tried this with hardy yet. Which video card are you running? I have a nvidia 7600go.

---

### Post by Dagur on 2008-05-10
Thanks for replying. I have an ATI Mobility FireGL V5000

---

### Post by EXCiD3 on 2008-05-10
What video driver and version are you running?

---

### Post by Dagur on 2008-05-11
I've been using the default driver but if I install the proprietary driver from the hardware drivers menu

xorg-driver-fglrx 1:7.1.0-8-3+2.6.24

it makes the problem happen less often, but it still does. 

I also noticed that it's never happened when the laptop is running on the battery (insted of being plugged in) but maybe that's just coincidence. I'm really lost :)

---

### Post by EXCiD3 on 2008-05-11
I just read that this typically happens when increasing video brightness...Could this be what is happening?

---

### Post by Dagur on 2008-05-11
I won't rule it out, but it doesn't happen when I do it manually.

I've only seen this happen when grub is done and the loading/splash screen should appear. If it does appear, there are no problems past that stage.

---

### Post by EXCiD3 on 2008-05-11
hmmm i dont think that experiencing the problem that soon at boot would be caused by the ati driver yet. im not really sure whats going on.

---

### Post by Dagur on 2008-05-12
Yeah me neither, It's pretty weird. Thanks anyway though

---

### Post by ThonyJ on 2008-10-10
No solution but . . .

I have the same trouble with my HP Compaq nw8240. I am a newbee at Linux and have tryed some step by step solutions found in forums to install drivers. But I realy do not know how to do it.

I have Ubuntu 8.04.

---

### Post by ThonyJ on 2008-10-17
Solved

I have solved the problem. I added **vga=794** at the end of the line starting with 'Kernel' in the file /boot/grub/menu.lst

You add different numbers depending on the resolution (794 gives resolution 1280x1024). I havent been able to find how to get widescreen mode.

Here is a link to other forum posts listing all vga resolutions:
[http://www.linuxquestions.org/linux/blog/archtoad6/2007-12-29/VGA_Resolution_Codes_for_GRUB_Lilo](http://www.linuxquestions.org/linux/blog/archtoad6/2007-12-29/VGA_Resolution_Codes_for_GRUB_Lilo) 

here is a klipping from my file:

--------
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b05f845e-4bc2-4b48-b7f7-22ed1d7f4bac ro quiet splash **vga=794**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
-------------

---

