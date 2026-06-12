---
title: "startx autostarting, but not set correctly"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by andale on 2009-01-19
Installed command-line from Xubuntu alternate cd. Installed Xorg. Installed Xfce. Tried to run StartX and got flashes and lines and made me worried about my screen. Shut down with forced power off. When I restarted X started automatically apparently. How can I prevent that. I can't do anything in X since its just glowing and flashing and having lines flashing all over.

---

### Post by kerry_s on 2009-01-19
use the second boot option, that puts you in single user mode.

what kind of hardware, vid card, etc...

your really not giving us anything to help you.

---

### Post by andale on 2009-01-19
and i still can't figure out what's up with "ACPI: no DMI BIOS year, acpi=force is required to enable ACPI"
I added something to the boot but I don't remember what it was offhand 
BUT
that's probably not causing any problems right now so I just mentioned it in case

---

### Post by andale on 2009-01-19
Sorry, i thought maybe a simple solution existed.
Running a [Toshiba 490XCDT]("http://www.e-laptop.com/catalog/toshiba/490xcdt.shtml") with Pentium II 266 and 160 RAM.
You mean the second option in GRUB? I'll try that. But how do I use that to keep X from autostarting, I would like it off for now so I can play in command line to configure everything (trying to learn to use command line more), I will make note of it and reinstate the autostart l8r if I can do that.

---

### Post by kerry_s on 2009-01-19
thats just saying it can't find what year your bios is.

---

### Post by andale on 2009-01-19
> **kerry_s said:**
> thats just saying it can't find what year your bios is.
figured. it's ancient. i was trying to get rid of it but i guess it makes no real difference.

---

### Post by kerry_s on 2009-01-19
have you tried dsl? [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

the ram is good, but the slow processor is going to make things really slow.

---

### Post by andale on 2009-01-19
okay, i'm in as root and let it try to auto-reconfigure X 
I tried to enter 'xorg -configure' as root
but it just says command not found
it confuses me because 'man xorg' works

restarted

X still starts on its own and its not configured  so i still just get flashes and lines.

---

### Post by andale on 2009-01-19
> **kerry_s said:**
> have you tried dsl? [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
I was trying it and liked its look, but everytime I tried to install it I had a kernel error.
I just don't know enough to deal with it

---

### Post by kerry_s on 2009-01-19
> **andale said:**
> okay, i'm in as root and let it try to auto-reconfigure X 
I tried to enter 'xorg -configure' as root
but it just says command not found
it confuses me because 'man xorg' works

restarted

X still starts on its own and its not configured  so i still just get flashes and lines.

the command is "**X**org -configure" linux is case sensitive.

than you got to copy it from root to /etc/X11/xorg.conf:
**cp /root/xorg.conf.new /etc/X11/xorg.conf**

---

### Post by andale on 2009-01-19
i keep forgetting the case sensitive thing

---

### Post by kerry_s on 2009-01-19
by the way you know xfce is way to heavy for your specs, you should try a window manager instead, some thing like fluxbox or icewm, better yet jwm, like dsl uses, it's what i use, i have it on 450mhz 256mb ram and 700mhz 128mb ram, both laptops run great with it.

---

### Post by andale on 2009-01-20
my fault, i misunderstood a post elsewhere and believed Xfce was less than FluxBox, I will go with FluxBox then.
Is there an easy removal for xfce? like 'apt-remove'
XFCE's [website]("http://www.xfce.org/documentation/installers/xfce/index.html#uninstalling") says it will bring up a graphical uninstall interface with "$ xfce4.uninstall", but I can't even run X currently.
...i'm working on that, i promise

maybe i should just reinstall and let the xubuntu disk just do a full install since i wanted to try fluxbox anyways

i noted in 'man Xorg' it saws CTRL+ALT+BACKSPACE will kill the X server, but on pressing this nothing seemed to happen

---

### Post by andale on 2009-01-20
> **kerry_s said:**
> have you tried dsl? [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
the ram is good, but the slow processor is going to make things really slow.
decided to give it another wack and i'd planned ahead for problems. there was a partition for dsl already and i installed dsl to hard drive instead of frugal but I can't seem to get the boot loader (GRUB) configured quite right despite a lot of reading
That's another problem for another thread I'd think so I'm just gonna leave that be for now.

In the meantime...
> **kerry_s said:**
> the command is "**X**org -configure" linux is case sensitive.

than you got to copy it from root to /etc/X11/xorg.conf:
**cp /root/xorg.conf.new /etc/X11/xorg.conf**

i ran Xorg -configure but all I got was a black screen, it never did anything or responded to any keystrokes so far as I could see. How long does should I be waiting for this to do something different?
I will do my best to copy any info to here that will be helpful or even wipe it and start from scratch if I must. 
Til tomorrow I gotta sleep for the night shift

---

### Post by kerry_s on 2009-01-20
Xorg -configure is just a starting point, you still have to go in there and set it up. 
nano /etc/X11/xorg.conf <-in single mode

from the specs you linked to it should be something like this for the monitor section:

```

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        DefaultDepth 16
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "800x600"
	EndSubSection

```

and make sure:
```
	Driver      "s3virge"
```
for the vid card driver.

---

### Post by andale on 2009-01-22
okay. I'm gonna close this one up for a bit. I can't seem to get this to operate currently and I have 2 Linux users helping me in person with no luck.

Gonna go back to trying to get Damn Small Linux to work on here since it takes less time to install and boot the live cd.

thanks for the help, i will refer back to this if i decide to try again with xubuntu

---

