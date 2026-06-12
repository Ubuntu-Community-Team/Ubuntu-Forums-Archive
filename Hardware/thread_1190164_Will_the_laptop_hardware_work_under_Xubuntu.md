---
title: "Will the laptop hardware work under Xubuntu?"
date: 2009-06-17
forum: Hardware
---

### Post by Tijmen007 on 2009-06-17
Hello all,
 
This is my first post on your forums and it's about my laptop. My laptop is around 9 - 10 years old with the following specifications:
 
-Intel Pentium 3 433Mhz / sometimes recognized as a Celeron. With only MMX instructions available.
-Intel 440BX/FX Chipset
-3 Com Wireless pcmia adapter
- Touchpad and normal keyboard
- Meastro sound card ( No idea )
- Ati RAGE LT / XPERT 98 , with 8 mb of video ram.
 
I'd like to install Xubunte on this laptop because windows 2000 uses to much memory and space, yea I know, since the HD is only 6,4 GB in size. ;)
 
Any other suggestions are welcome ( Other OS, but nothing OLDER as Windows 2000 :KS )
 
Thanks in advance,
 
Tijmen :p

---

### Post by MikeEvans on 2009-06-17
It should work in that system but be sure you use the alternative install disc.  The normal install disc requires more RAM (im guessing since you didn't state how much RAM is in the system).  If that doesn't work Damn Small Linux is a good alternative although its GUI is no where near as robust as in Ubuntu.  If your wireless doesn't work you need to use ndiswrapper with the windows driver

---

### Post by cariboo on 2009-06-17
> -Intel Pentium 3 433Mhz / sometimes recognized as a Celeron. With only MMX instructions available.
-Intel 440BX/FX Chipset
-3 Com Wireless pcmia adapter
- Touchpad and normal keyboard

All of the above should work out of the box

```
- Meastro sound card ( No idea )
```

Should be no problem as drivers are included with the kernel

> - Ati RAGE LT / XPERT 98 , with 8 mb of video ram.


You may have to use the vesa drivers for such an old graphics adapter.

The biggest problem you will probably have is not enough ram. To use the Live Cd you need at least 348MB ram. I would suggest using the [Alternate install iso]("http://releases.ubuntu.com/9.04/").

---

### Post by Tijmen007 on 2009-06-17
Thanks for the quick replies! Coffee beans for everyone!
 
Another question about the Vesa drivers. Will this greatly reduce my graphics preformance? I assume the vesa drivers will create a VGAsafe situation as in Windows XP. My laptop has 200 mb of memory, I'm looking for 512 mb ( 2 x 256 ) but I've only found very expensive shops so far. 
 
Back on topic, if I now run the knoppix ( 4.x ) cd, will this give me a good impression of what the hardware compatability will be ?
 
Tijmen

---

### Post by Tijmen007 on 2009-06-17
Just ran Knoppix, videocard fully supported and all. The only thing i couldn't figure out was how to get to the device manager or something alike. Maybe 3com has some linux drivers, I'll check it out later, it's getting late here. About the knoppix I was running, the kernel version was 2.6 , this means ( because its older ) that everything will be compatable in the newer versions and in this case with Damn Small Linux ?

---

