---
title: "Presario 1255 (Sound not working)"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by Modki on 2006-08-09
Hi Ubuntu Forums!

First I'd like to say that installing Xubuntu was very smooth nothing like what I thought I'd go through with Linux. Before it ever installed anything all my hardware was detected (keyboard, touchpad, display) and it even found my wireless PCMCIA card easily and setup a connection for it right away. I've been using Xubuntu on the laptop for a better part of the week now and it's great!

But (isn't there always a 'but'?) I have no sound. Here's a quick rundown of what i've tried:

**lspci:** no soundcard in the list; from there I went looking for the drivers but find only the PCI version when mine is on-board sound.
**lsmod:** nothing there either
**modprobe sb irq=5:**Sometimes I get errors, sometimes I get something that says it found part of it.

Now from googling non-stop since monday I've found out the following. Compaq lists on their specs for the 1255 the souncard being a "Aureal A3D Interactive 360 degree Positional Sound". In windows it's listed as 1886. There are no drivers I can find and no solutions to this problem.

I found one post on another forum that pointed to a solution on a page that no longer exists.

> I gave up on the ALSA drivers. I just couldn't get them to load correctly for the Aureal card and I don't have the time to mess with it anymore.

Now here's the good news:

I followed the directions for setting up the sound at:
[http://www.putzin.net/linux/compaq/](http://www.putzin.net/linux/compaq/)

And it worked fine. What I did was to enable sound, OSS and the "Sound Blaster 16" drivers as modules in the kernel. Upon reboot I loaded the 'sound' module and then the 'sb' module according to these directions:

[http://www.putzin.net/linux/compaq/kernel.html](http://www.putzin.net/linux/compaq/kernel.html)

"# Sound. Here is what I have

1. Yes to sound card support
2. Module for OSS sound modules
3. Module for 100% Sound Blaster Compatible
4. Then, because it is a module, you need to load the sound module (sound.o) and then load the module sb.o with the line /sbin/modprobe sb io=0x220 irq=5 dma=1 dma16=5. This should work just fine."

The sound works great! According to the above mentioned web pages you don't get all the trick, surround sound stuff but who cares. It's a laptop Games and MP3's are all I really care about.!

[SIZE="2"]**TLDR? Here's all I really need:**
I am fairly new at this Linux thing and I catch some of what is going on. But I thought the kernel was something dangerous to go into. Could someone break down where I need to go to in the kernel to *"enable sound, OSS and the "Sound Blaster 16" drivers as modules in the kernel"* and going about *"load the sound module (sound.o) and then load the module sb.o with the line /sbin/modprobe sb io=0x220 irq=5 dma=1 dma16=5"*

**Help me ObiWan Ubuntu, you're my only hope.**

-Modki
[/SIZE]

---

### Post by Modki on 2006-08-09
Fixed, hehe guess I didnt look hard enough, link to solution in sig.

-Modki

---

### Post by Modki on 2006-08-10
Ok, finally fixed.

added this to /etc/modules
```

snd-es18xx

```

and I made a /etc/modprobe.d/sound file with the following
```

options snd-es18xx isapnp=0 port=0x220 irq=9

```

You can change your IRQ to 9 in the BIOS by hitting F10 when the big red COMPAQ screen comes up. Though I don't know if this is neccesary it just made mine work for some reason.

THis works like a charm, I can even control the 3D settings and this laptop pumps :D JBL knew what they were doing ^_^

---

### Post by ceno-byte on 2007-12-26
thankyou so much i finally have decent sound on my compaq presario 1235 worked like a charm

---

