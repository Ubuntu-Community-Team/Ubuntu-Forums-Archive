---
title: "Display not functioning on an old POS unit"
date: 2011-08-10
forum: Hardware
---

### Post by tomsimmons on 2011-08-10
I have an old POS touch screen unit that I would like to run Ubuntu on.

When I stick the Live CD in it won't display on the touch screen, but does on an external monitor.

I went ahead and completed the install using the external monitor thinking I could fix this afterwards, might be something as simple as resolution.

Well needless to say it wasn't a resolution problem, I know it's not a BIOS issue because it works fine with Windows installed.

Would someone be able to give me a little guidance on trying to find out what the problem is please?


Thanks

Tom

---

### Post by jualin on 2011-08-10
> **tomsimmons said:**
> I have an old POS touch screen unit that I would like to run Ubuntu on.

When I stick the Live CD in it won't display on the touch screen, but does on an external monitor.

I went ahead and completed the install using the external monitor thinking I could fix this afterwards, might be something as simple as resolution.

Well needless to say it wasn't a resolution problem, I know it's not a BIOS issue because it works fine with Windows installed.

Would someone be able to give me a little guidance on trying to find out what the problem is please?


Thanks

Tom

Can you go to the command line and post the output of ```
lshw
dmesg
```

This will display your hardware specifications and your kernel messages

---

### Post by tomsimmons on 2011-08-10
> **jualin said:**
> Can you go to the command line and post the output of ```
lshw
dmesg
```

This will display your hardware specifications and your kernel messages

I will grab this output as when I get done with work.

One thing I should have mentioned is that both screens display up until the Ubuntu 10.10 with the dots below, then this clears only the external monitor is working.

Similarly when you choose shutdown/restart, when the text appears for stopping this and that it display on both screens


Tom

---

### Post by oldsoundguy on 2011-08-10
Off hand, would say that the driver is needed for that point of sale touch screen.  Might be hard to come by. I had one that I never was able to get to function properly .. could never find the driver.
(what is the make and model of the screen .. for info for others to help?)

---

### Post by tomsimmons on 2011-08-10
> **jualin said:**
> Can you go to the command line and post the output of ```
lshw
dmesg
```

This will display your hardware specifications and your kernel messages

Found my USB pen, so here is the output....

(Had to zip the, dmesg was too large)


Tom

---

### Post by tomsimmons on 2011-08-10
> **oldsoundguy said:**
> Off hand, would say that the driver is needed for that point of sale touch screen.  Might be hard to come by. I had one that I never was able to get to function properly .. could never find the driver.
(what is the make and model of the screen .. for info for others to help?)

The touch side of things works fine, it's just the display and I'm afraid that I have no idea what make or model it is.

I have had other small versions of Linux running on there, can't remember what it was called it was a GUI based recovery system when the HDD that ha Windows on got scrambled.


Tom

---

### Post by tomsimmons on 2011-08-27
No one got any thoughts on this?


Tom

---

### Post by oldsoundguy on 2011-08-27
so you have some sort of display, but not as desired?

what does running "lshw" in CLI tell you?

If you can not get a maker that way, try hooking it to a Windows box and running Belarc Advsor.

---

### Post by tomsimmons on 2011-08-28
> **oldsoundguy said:**
> so you have some sort of display, but not as desired?

what does running "lshw" in CLI tell you?

If you can not get a maker that way, try hooking it to a Windows box and running Belarc Advsor.

LSHW is included in the zip above, however because the machine was struggling under full Ubuntu I have installed Lubuntu.  I don't think it will make a difference to the LSHW output though.

The built in display functions fine until it turns truly graphical (end of the (L)Ubuntu with the four dots underneath) then only the external display works.

I've tried 800x600, no difference.

Under Windows the driver is shown as missing currently, but at least it displays the GUI.

Tom

---

### Post by tomsimmons on 2011-08-28
Just a thought...

From what I can find online the video card is a VIA/S3G Unichrome CLE266.  Which seems to agree with LSHW output.

I find here...

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

That this used to be supported un Ubuntu, then by the looks removed as of 8.10.

However, because I have full video support on the external monitor, and everything until Ubuntu loads the full driver (at a guess), is this something to do with multiple monitors?

Sadly in the GUI monitor config, there is no mention of there being a multiple monitor, but I'm wondering if a config file somewhere would have the output for the video card and for some reason it's only seeing the external as an option.


Tom

---

### Post by tomsimmons on 2011-09-13
Wondering if anyone has any thoughts on this, it's beginning to annoy me now.

I'm wondering if it's a driver issue, but don't really know how to find out if it's making do with a generic driver that is working with the external monitor but not the internal or what.

I don't want to think that I'm going to have to admit defeat and return the machine to a Windows install.


Tom

---

