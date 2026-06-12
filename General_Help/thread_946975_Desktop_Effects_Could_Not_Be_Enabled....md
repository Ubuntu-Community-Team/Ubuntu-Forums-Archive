---
title: "Desktop Effects Could Not Be Enabled...?"
date: 2008-10-13
forum: General Help
---

### Post by icanfly0307 on 2008-10-13
Hi Everyone,
            I know that this question has already been asked many times. I've read through almost every single post on this issue and have tried every suggested method. However, when I try to enable desktop effects, my system becomes busy for a few seconds and then the windows disappear for a fraction of a second. After that, an error dialog comes up saying, "Desktop Effects Could Not Be Enabled."

I have an onboard Intel 82815 Graphics Chipset. The driver that I am currently using is the "i810" driver provided on Ubuntu.

Oh yeah, forgot to mention this... I'm running Ubuntu 8.04 Hardy Heron. :biggrin:

Any help would be appreciated...

---

### Post by neilengineer on 2008-10-13
Type the command
$glxinfo|grep direct rendering

Show the result.

---

### Post by pytheas22 on 2008-10-13
Desktop effects should work out-of-the-box on an 810 card in Hardy.  Did they work originally and stopped, or did they never work for you?  Please also post the complete output that you get if you open a terminal and type:
```

compiz --replace
```

(if that causes your screen to go blank or something else weird, press control-C and you should be dumped back to your desktop so that you can copy the output and post it here).

---

### Post by icanfly0307 on 2008-10-14
Hi Guys,
         Thanks for your reply. :)

First off, here's my reply to **neilengineer**:

This is what I got when I typed in your command:

[FONT="Lucida Console"]
root@Mars:/home/saravan# glxinfo|grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)[/FONT]

Is this a graphics card compatibility issue or do I just need to enable Direct Rendering? If it's the latter, could someone guide me on how to do that?

[B]
pytheas22:[/B]

When I tried out your code, the screen kinda sorta flashed for a while and then the border to the windows disapperead!!! Then, after about a second, they came back but my hard drive kept running (the light was on continuosly). The terminal also kinda froze after showing the following messages:

saravan@Mars:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:1132' found 
aborting and using fallback: /usr/bin/metacity

I couldn't get it to recover until I hit "Ctrl + C" like you suggested. Hope this helps in solving the problem.

Btw, if anyone else also has any ideas or suggestions, feel free to let me know.

---

### Post by neilengineer on 2008-10-14
> **icanfly0307 said:**
> Hi Guys,
         Thanks for your reply. :)

First off, here's my reply to **neilengineer**:

This is what I got when I typed in your command:

[FONT="Lucida Console"]
root@Mars:/home/saravan# glxinfo|grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)[/FONT]

Is this a graphics card compatibility issue or do I just need to enable Direct Rendering? If it's the latter, could someone guide me on how to do that?


It seems your graphics card or the driver doesn't support 3D while 82815 and i810 driver is supposed to support.  BTW, does the memory in your graphics card larger than 64MB? Someone said problem occurred when graphics card memory was less than 64MB.

---

### Post by pytheas22 on 2008-10-14
Yes, it seems that your graphics card is not compatible with compiz (aka desktop effects).  There was a bug report filed about this [here]("https://bugs.launchpad.net/ubuntu/hardy/+source/compiz/+bug/221920").  Unfortunately it doesn't sound like anyone is working to make your card work with compiz, because it's an old video card.

From what I'm reading, even with desktop effects turned off, you may have issues with 3D rendering, for example when you're playing games.  If this happens, take a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/243991"); it has some fixes.

Unfortunately, I don't think there's any way to use desktop effects on this video card.  If it's any consolation, though, my i810 video card--which does support compiz--is not really powerful enough to handle the effects at an acceptable speed.  So even if your card did support desktop effects, you would probably not really be able to use them every day because the machine would be too laggy.

---

### Post by icanfly0307 on 2008-10-15
Hi again,
                 Here's the weird thing. I had Fedora 8 installed a couple of months ago. When I tried to enable Desktop effects, they worked. However, it was only in the 16 bit color mode. Once I switched the settings to the normal 24 bit color mode, they stopped working. :confused:

Also, I think you guys are right. My video card does have less than 64 mb of video ram. Even if it did have more than that, my computer would seriously have performance issues because it's got only 256 mb of ram.

Thanks for your help. Maybe someone else will be able to benefit from these responses, too. :)

EDIT: I just figured out from the Intel website that my graphics card can only use up to 32 megs of RAM.

---

