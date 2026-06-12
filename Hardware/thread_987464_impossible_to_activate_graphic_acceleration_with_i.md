---
title: "impossible to activate graphic acceleration with intel graphic chip"
date: 2008-11-19
forum: Hardware
---

### Post by el_Nacho on 2008-11-19
Hi there, i am so f*#?="ng frustated not being able to get my ubuntu run properly. here is the thing. since the last 2 versions or so ubuntu recognizes my graphics card so i don't have to install this 915 resolution tool anymore. the graphic acceleration though doesn't work. that makes my system run shitty even in that low resources mode (which i don't really want to use) or run xfce.

installing these drivers [http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900) was my last shot but the script tells me there are no kernel headers even though i've got the package installed.

in the device section of my xorg.cong my graphic card is just called "configured video device" instead of i810

these packages mentioned somewhere as supposed to help but just don't:  xserver-xorg-video-intel - libgl1-mesa-glx - libgl1-mesa-dri

I am running Intrepid, my graphic chip is a intel media accelerator 900.

Please help, i just want to get rid of my windows you know :-&

Thanks in advance!!!!!

---

### Post by el_Nacho on 2008-11-20
I think i figured out something, according to this bloke [http://blog.csdn.net/givemeliu/archive/2008/11/07/3249848.aspx](http://blog.csdn.net/givemeliu/archive/2008/11/07/3249848.aspx)
the i810 allocates only 8mb of the shared memory by default. that makes perfect sence cause my system lacks the same way when i activate compiz with lots of effects and when i run in low resources mode. now i need to figure out how i can tell ubuntu to allocate more memory for graphics and maybe change the color depth.

does anyone know how to do that?

by the way, is it normal that my swap space is always at 0% ??

---

### Post by Yezinki on 2008-11-20
Check your BIOS........other wise your stuck.

---

### Post by amauk on 2008-11-20
yeah, in the BIOS there's usually an option to specify the "graphics aperture" size (the amount of memory given over to the integrated chip)

see if you can alter it

also, Re: swap usage
yes 0% is normal
means the OS is not short of physical memory, and doesn't have to page out

---

### Post by el_Nacho on 2008-11-20
my bios doesn't have any options like that, already had a look :/
will try to update the version tomorrow though ...

i've put this option into xorg.conf
VideoRam    32768
but eventhough gnome accepts that and starts there is no change, not with 32 nor with 65536 and so on :(

can someone explain to me why adding
Driver      "i810"
to my xorg.conf doesn't work? the xserver-xorg-video-intel package is installed and thats supposed to be the driver. it simply looks like this:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

:confused:

---

### Post by Yezinki on 2008-11-21
Get your BIOS updated, if possible....most likely you are stuck up with the OEM's dedicated video memory!

---

### Post by el_Nacho on 2008-11-21
alright, will do.

i achieved a lot of performance by adding

```
DefaultDepth 16
```

to the screen section in my xorg.cong since i've read acceleration with th 810 only works at 16 bit. now compiz won't work anymore but FINALLY i have an environment wich actually allows me to work.

thanks to you guys for your quick answers

---

### Post by Yezinki on 2008-11-21
Hope your issue gets resolved to your needs!

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
128 MB is good enough for Ubuntu with no visual effects  performance........but not enough to use emerald, Compiz, desktop customization.....they shall work but your screen shall start to hang/freeze.......wont be smooth........sluggish.

Happened with me.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
1. add to panel CPU frequency & scaling.

2. Click on it & check performance.

3. For both CPU 0 & CPU 1.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
Screen shots for your views.

---

