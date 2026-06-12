---
title: "Wacom serial tablet not detected on Ubuntu 10.04 (Digitizer II UD-0608-R)"
date: 2010-05-27
forum: Hardware
---

### Post by purelinuxuser on 2010-05-27
I need some help getting this Wacom Digitizer II UD-0608-R tablet working under Lucid.  This tablet has not worked since Karmic and is not automatically loaded since it is a really old serial tablet.  I've googled serial tablets under 10.04 but no luck- any suggestions?

This is the only reference I can find to a tablet of any kind in [FONT=Courier New]dmesg[/FONT]:
```
[    0.607500] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.607604] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.608028] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

[FONT=Courier New]lsmod | grep -i wacom[/FONT] yields nothing :(

Thanks in advance! :)

---

### Post by Favux on 2010-05-27
Hi purelinuxuser,

Serial tablets are not supported by Xorg's X driver xf86-input-wacom in Lucid.  This turns out to be due to a lack of dev. resources not policy.  Some patches have been submitted to add serial support back.  They are still under development.  Using them two serial tablets have gotten things working.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1480915](http://ubuntuforums.org/showthread.php?t=1480915)

Good luck!

---

### Post by purelinuxuser on 2010-05-27
> **Favux said:**
> Hi purelinuxuser,

Serial tablets are not supported by Xorg's X driver xf86-input-wacom in Lucid.  This turns out to be due to a lack of dev. resources not policy.  Some patches have been submitted to add serial support back.  They are still under development.  Using them two serial tablets have gotten things working.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1480915](http://ubuntuforums.org/showthread.php?t=1480915)

Good luck!

Ouch!  I've already had to recompile a kernel to get around my laptop's buggy BIOS, now I have to recompile a driver for my desktop? :)

Thanks for the link, I'll get to it when I have time.

---

### Post by purelinuxuser on 2010-05-28
Ugh... I've tried pretty much everything I can do (tried all three patches, tried 0.10.6 release, tried recent git checkout, tried git checkout from May 24) but the tablet refuses to work.  I've gotten the wacom kernel module to load and the Xserver module to load but the tablet is not recognized at all!

*sigh*... guess I'll wait for further X driver updates and maybe release 10.10. :(

---

### Post by Favux on 2010-05-28
I'm assuming you configured through xorg.conf and used 'Option "ForceDevice" "SERIAL"'.

We spent some time trying to get similar models to work in Jaunty and Karmic with no luck.  I seriously doubt a later release will support it.  If you look through the code I think you see yours isn't listed.  I haven't really looked through the serial patch though.

As far as I know Hardy or maybe Gutsy was the last release it worked for.  So linuxwacom 0.7 or 0.6?

My guess is the code for your specific, and similar models, isn't in the code anymore and it doesn't default to basic stylus support for it.  You could try posting on linuxwacom-discuss and ask.  It seems like even if the tablet model doesn't have a serial PnP identifier because of it's age that it wouldn't take that much code to default it to stylus support.  Probably just changing some If Then statements.

---

### Post by purelinuxuser on 2010-05-28
Yup, tried the ForceDevice option too.  I even manually fixed a problem with the patch.

it kinda annoys me that something that worked fine in the past (back in Intrepid, maybe even Jaunty... definitely not Karmic) is no longer functional... :mad: The tablet works fine under the parallel Vista installation, which is currently broken ATM lol. :)

---

### Post by Favux on 2010-05-28
> The tablet works fine under the parallel Vista installation, which is currently broken ATM lol.
I feel your pain.  I just repaired an unstable XP install caused by some bad RAM on my triple boot Desktop.  Major job and quite the pain.  Lucid by the way recovered without a problem.

---

