---
title: "Weird screen when shutting down/hibernating/restarting, jaunty, ubuntu 9.04"
date: 2009-04-29
forum: Hardware
---

### Post by garuhhh on 2009-04-29
hi all!

am having problems with jaunty (ubuntu 9.04) and my nvidia driver (180.44).

i get this weird screen, which flashes white and streaks of horizontal and vertical white lines all over my screen when i shutdown/ restart/ hibernate.

i don't see the splash screen.

for reference, i posted a video on youtube [here]("http://www.youtube.com/watch?v=LBjT7Pye36I"), and [here]("http://www.youtube.com/watch?v=_b9xxmg_02o"). sorry for the bad quality...i just used my phone for it.

[http://www.youtube.com/watch?v=LBjT7Pye36I](http://www.youtube.com/watch?v=LBjT7Pye36I)
[http://www.youtube.com/watch?v=_b9xxmg_02o](http://www.youtube.com/watch?v=_b9xxmg_02o)

hope anybody can help..

---

### Post by K. Hendrik on 2009-04-29
I've got the same problem on my Acer Aspire 6935 with Jaunty I'am using the NVIDIA driver 180.51 for my Geforce 9600GT. even when using the standard ubuntu drive the problem remains.

---

### Post by garuhhh on 2009-04-29
ahh yes, by the way, am also on an Acer Aspire 4520..

amd turion 64x2
3GB RAM
nvidia 7000M graphics

without the nvidia driver installed, i don't have such artifacts..though i've tried only the 180.44.

---

### Post by garuhhh on 2009-04-30
@K.Hendrik,
are you not having hibernate/suspend issues?

i can't resume from suspend. no backlight from my laptop when i resume,though there seems to be disk activity, after that, the only way out is to press the power button!

my pc hibernates and resumes well from hibernate. but i have to press enter many times before it hibernates or resumes.

---

### Post by K. Hendrik on 2009-05-01
I will try the hibernation when I'm home I normaly don't use it so perhaps I've got that probem too i will write back when I've tested that.

Edit:
Ok I've got the hibernate/suspend issues too.

---

### Post by K. Hendrik on 2009-05-04
Hi, I've tried to fix my usplash to fit on my 16:9 screen by adding a vga parameter in /boot/grub/menu.lst after that it was good a startup but did'nt show at shutdown but the glitches when shuting down were also gone so perhaps its got something to do with usplash.

---

### Post by garuhhh on 2009-05-04
hello!
from what i read, it's not about usplash. it seems during non-X displays (like the terminal), the refresh rate/resolution of the monitor is not detected well. so by specifying vga=xxx you are manually setting the resolution.
see this [link]("http://ubuntuforums.org/showthread.php?t=996719").

i corrected mine by putting vga=791 to the boot menu. it sets my terminal resolution to 16bits, 1024x768.

---

### Post by Obnoticus on 2009-05-08
Hi garuhhh,
  I seem to be having the same problem right after upgrading to the new nvidia driver... can you give me a more detailed description on exactly how you resolved the issue?  Thanks!

---

### Post by garuhhh on 2009-05-08
hello obnoticus,

to try it at first on your PC if it will solve your problem:
while in the grub menu, choose the option which you usually use to boot to Ubuntu 9.04 (am using 9.04), in my case that's the following option:
> Ubuntu 9.04, kernel 2.6.28-11-generic
then press "e", you will now edit the boot parameters of that option.
now choose the line which is similar to the following:
> kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=44cfa5f2-5ccc-4a66-8e32-208160c3c5d9 ro  single
then press "e" again.
add the following code to the end of the end of the code:
> vga=xxx
you should now have
> kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=44cfa5f2-5ccc-4a66-8e32-208160c3c5d9 ro  single vga=xxx
For the "xxx" value, you will be choosing the resolution that fits your screen well, in my case i use 1024x768,16bits, so i use 791. The code i added is "vga=791". To check which code to use, try this [link]("http://en.wikipedia.org/wiki/VBE#Linux_video_mode_numbers").
So mine looks like the following:
> kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=44cfa5f2-5ccc-4a66-8e32-208160c3c5d9 ro  single vga=791

If that works, you should now see your Terminals (Ctrl+Alt+FnKey), or won't experience the weird artifacts during Shutdown, Restart or Hibernate.


To make the changes more "permanent", open your text editor with Root permision, Press Alt+F2, and type
> gksu gedit /boot/grub/menu.lst
but before you do this, it's wise to make a backup copy of menu.lst first.

look for the similar lines:> 
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		44cfa5f2-5ccc-4a66-8e32-208160c3c5d9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=44cfa5f2-5ccc-4a66-8e32-208160c3c5d9 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
and change them to something similar:
> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		44cfa5f2-5ccc-4a66-8e32-208160c3c5d9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=44cfa5f2-5ccc-4a66-8e32-208160c3c5d9 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.28-11-generic
save your menu.lst and that should make it more "permanent".
that will change again though if you upgrade your kernel/ubuntu (i think).

Hope that helps.

---

### Post by Obnoticus on 2009-05-09
Great stuff!  This worked perfectly.  I howver made one small change.  The vga=xxx was changed to vga=0x361 for my laptop's 1280x800 screen.  Otherwise the instruction worked as inteded.

Before this I would have trouble just shutting down from linux because the scren would get stuck at the flashing white lines and refuse to turn itself off (not very cool if you're gone for a 12+ hour workday and trying to turn the machine off before leaving).  But this seems to have solved for the problem.

Thanks for the help!

---

### Post by garuhhh on 2009-05-10
ahh yes.. vga=0x361 is the hexadecimal equivalent of vga=865, which is in decimal.

glad to be of help :D

---

