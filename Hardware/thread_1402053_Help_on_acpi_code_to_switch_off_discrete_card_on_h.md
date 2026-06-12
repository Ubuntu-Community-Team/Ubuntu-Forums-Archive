---
title: "Help on acpi code to switch off discrete card on hybrid nvidia 9500m"
date: 2010-02-08
forum: Hardware
---

### Post by luizfar on 2010-02-08
Hello guys!

I need help!

I have a Dell Studio XPS 13 with a nvidia 9500m card (hybrid sli 9200gs + 9400m). I want to be able to switch off the discrete card to gain battery life and lower the overall computer temperature.

I found this thread [http://ubuntuforums.org/showthread.php?p=8587236](http://ubuntuforums.org/showthread.php?p=8587236) where avilella posts a piece of code to switch off the geforce 210m discrete card on the asus sli configuration.
So I was trying to modify the code for the nvidia 210m so that it would switch off the 9200gs discrete card on the XPS 13.

Analyzing the code (the pieces of it that I understand), I found out that it uses the method _SB.PCI0.P0P1.VGA._OFF to switch off the card.  So I started to look for a method that I could call to switch off my 9200 card.

I started by comparing the two DSDT tables and realized they were quite different. The XPS DSDT table has a Device named LGPU with a method _DIS, which I found out on Google that stands for 'disable'. So I tried compiling and loading the same piece of code but using the method _SB.PCI0.LGPU._DIS. I loaded the module and restarted X and it wouldn't come up again so I thought I had actually switched the integrated card off.

I restarted and started over.
I had to find out which Device on my DSDT table was the discrete card, so I did:

```
sudo lspci -vvv
```

and from it I got the discrete card was on the bus 02:00.0 and IRQ 23:

```
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
(...)
	Interrupt: pin A routed to IRQ 23
(...)

```

And then from the kernel log I found that the Device code for this is Z00Q:

```
Feb  7 22:24:18 xps kernel: [   10.420090] nvidia 0000:02:00.0: PCI INT A -> Link[Z00Q] -> GSI 23 (level, low) -> IRQ 23
```

So the discrete card is the device Z00Q, right? This Device has only 5 methods on my DSDT table: _STA, _DIS, _PRS, _CRS and _SRS.
Based on this I changed the code to use the method:

_SB.PCI0.Z00Q._DIS

The module compiled and loaded without problems, no errors.
But using powertop I noticed absolutely no difference on the power consumption, the battery life is still the same and the computer still runs hotter on Linux than on Windows with the card off.

I don't know how to make sure that the card has been switched off.. is there a way to do it?
But even so, it doesn't seem to have been switched off.. I don't understand anything about acpi or the kernel modules.. I am just trying to be a smartass here lol
But maybe some one who's more experienced can help me a bit from here and together we can figure out a way to get it off on this laptop?!

Thanks!!!!

---

### Post by avilella on 2010-02-09
Hi,

Have you tried the recent version of nouveau?

There is a: drivers/gpu/drm/nouveau/nouveau_acpi.c
that provides support in theory for *all* nvidia cards with the _DSM method.
If your DSDT.dsl table has a '_DSM' method, it should be supported.
Either try the latest Fedora development branch or wait for the first Ubuntu Lucid with the updated nouveau_acpi.c.

---

### Post by luizfar on 2010-02-09
Wow this is great news! I didn't know about it yet.
And yeah, from the DSDT file it seems like the 9500m configuration supports the _DSM method :)

I will take a closer look at this. Thanks for the information!

---

### Post by luizfar on 2010-06-28
Hey! Great news! I got the discrete card off, thanks to avilella and drphd!  ([https://launchpad.net/~drphd](https://launchpad.net/~drphd))

I made a blog post about it: [http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/](http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/)

---

