---
title: "more unwise nvidia hacks"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by farnsworth on 2005-05-23
I found this hack on a gaming site, and figured I'd write an Ubuntu-ized guide for everyone here.  If you're dissapointed with your nvidia/linux experience, and find yourself saying things like "Doom 3 runs slower in linux!" or "Return this drone to the collective!", give this a shot.

Disclaimer:  Enabling SBA and Fast Writes can lead to system instability for some.  It works great for me, so there!

OK, first off, type these two lines into a terminal:

~$ cat /proc/driver/nvidia/agp/card
~$ cat /proc/driver/nvidia/agp/host-bridge

these will give the specs of your graphics card and hostbridge (the thing what connects the system bus to the AGP controller, I think).  Mine looks something like this:

~$ cat /proc/driver/nvidia/agp/card
#########################
Fast Writes:     Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000017:0x1f000104
#########################

This tells me that my card supports fast writes, but NOT SBA.  It also supports up to 4x AGP.  Both the card and hostbridge MUST support a feature if you want to enable it, but for now just remember the card settings.  If the hostbridge shows "Not Supported" or "Disabled", you'll have to go into the BIOS chipset setup and enable them (probably under the "Advanced" tab or something).  We'll do that in a bit.

You also must be using the nvidia kernel module.  to find out your modules setup, type:

~$ lsmod | grep -i agp
It should look approx. like this:
agpgart                31784  1 nvidia

if anything else is in this line, it's probably "via_xxxx" or something.  if that's the case you'll have to blacklist that module (the "via" one, you don't want the kernel to get confused about your video setup).  do that by adding the module name to the bottom of the /etc/hotplug/blacklist file.  afterwards, enable the NvAGP option in your /etc/X11/xorg.conf :

        Option          "NvAGP"                 "1"

Note:  I don't have "RenderAccel" or "Compositing" enabled, and everything works great.  You might want to comment out those lines for now, just to be on the safe side.

Now that you have X agp ready, it's time to reboot and enter your BIOS setup.  Remember those card specs I told you to memorise?  Make sure the features your card supports are enabled (Fast Writes, SBA, both).  The AGP speed is probably already set to the highest rate you can get, but if not, change it.  Save settings and reboot.

OK, hopefully you're in X and nothing exploded.  type this again:

~$ cat /proc/driver/nvidia/agp/card
~$ cat /proc/driver/nvidia/agp/host-bridge

Every option that can be enabled should now be "Supported" by the card and hostbridge.  to actually enable them type:

~$ sudo gedit /etc/modutils/nvidia-kernel-nkc

and slap this line, or something similar, at the bottom of the file:

options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8

or, if you have an old 4x card like I do, that doesn't support SBA, type:

options nvidia NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=4

You get the idea.  Reboot.  Done.  On my system, this added an extra 20-25 fps in glxgears and improved X and Doom3 performance noticably.

---

