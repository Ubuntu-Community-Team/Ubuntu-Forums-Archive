---
title: "need help installing hardy on my notebook"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by malspa on 2009-01-25
I am unable to get X started on my old Balance notebook when I try to run the Ubuntu Hardy live cd.

This notebook is currently running Kubuntu Dapper, kernel 2.6.15.  I have also successfully run the Mepis 6.5 live CD on it, also kernel 2.6.15.

I'm unable to run the following live CDs:  Ubuntu Hardy and Mint Elyssa (both kernel 2.6.24) and Mepis 7 (kernel 2.6.22).

I seem to get caught in a status bar which then turns to a black screen with apparently no further computer activity.

With Hardy, I tried removing "splash" from the boot code, and adding "vga=771" or "vga=791" because those worked with Kubuntu Dapper.

What happens next, I start seeing messages like the following:

udevd-even[1555]: udev_rules_apply_format: unknown format variable '$:rvr1.0:cvnUnknownChassisManufacture:ct3:cvrVersion1.00:'

I end up getting to a command prompt.  If I try startx from there, I get "Fatal server error: no screens found."

The notebook has a VIA C3 processor (Nehemiah).  From the User Guide:  Display - 14.1" TFT XGA.

I don't know which specs to provide here, but here are the results of a couple of commands, run from within Kubuntu Dapper:

```
steve@steve-laptop:~$ sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: VT8623 [Apollo CLE266] integrated CastleRock graphics
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@01:00.0
       logical name: /dev/fb0
       version: 03
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list fb
       configuration: depth=8 frequency=75.12Hz mode=800x600 visual=pseudocolor xres=800 yres=600
       resources: iomemory:d8000000-dbffffff iomemory:de000000-deffffff irq:10
```

```
steve@steve-laptop:~$ cd /var/lib/acpi-support
steve@steve-laptop:/var/lib/acpi-support$ grep . -r *-*
bios-version:Version 07.00T
system-manufacturer:Elitegroup Co.
system-product-name:ECS G320
system-version:1.0
```

I don't know where to go from here, or what info to provide here to get some help.  Any ideas?

---

### Post by aheckler on 2009-01-25
You could try starting the LiveCD in "Safe graphics mode". It's under "Other options" or some such when you boot up the LiveCD.

---

### Post by malspa on 2009-01-25
Well, I tried safe graphics mode, same results, I ended up at a command prompt.

I noticed that one of the messages I'm getting on my screen is:

cat: /var/lib/acpi-support/bus-version: No such file or directory.

So I tried adding **acpi=off** to the end of my boot code.  Same results, I end up at a command prompt, X will not start.

I don't want to give up on this but it's starting to look like Hardy will not work on this notebook.  Not sure what else to try to get it to work.

---

### Post by aheckler on 2009-01-25
You might try an Intrepid disk and see if you have any luck.

---

### Post by malspa on 2009-01-26
Thank you for your replies and suggestions, aheckler.

I tried the Ubuntu Intrepid CD, same results.

These CDs that I'm trying were from Shipit.

I have been googling around and have tried some other codes at the end of my bootline, such as nopic, acpi=off irqpoll, xmodule=vesa...

I have to use these in combination with something like vga=771 or I end up with a black screen.  But with each of them, I still end up at a command prompt.  I use **sudo reboot -h now** to reboot, and try something else.

Since Dapper and the earlier Mepis live CDs boot on this machine, I feel that it has something to do with kernels 2.6.2x kernels.  Other than that I have no clue as to why anything beyond Dapper and Mepis 6.5 will not boot on this notebook.

I can continue to use Kubuntu Dapper with this notebook but I guess the Dapper repos are dead so I'd like to install something newer.

I don't know what else to try; I guess I'm at a dead end with Ubuntu on this notebook, but if anyone has any other suggestions, I'll give them a try.

---

### Post by malspa on 2009-01-28
To follow up, I tried the PCLinuxOS 2007 live CD on this notebook.  It booted up fine.

But then I realized the kernel is 2.6.18.8, which means I still haven't found a live CD with kernel 2.6.2x that will work on the notebook.  What's going on here?  Is this notebook's hardware no longer supported by Linux?  That seems to be the case.  Any suggestions?

---

