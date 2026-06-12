---
title: "karmic m1400 tablet update breaks usb keyboard at startup"
date: 2009-12-05
forum: Hardware
---

### Post by alexvd on 2009-12-05
I have a Motion Computing tablet model m1400 that I am running Karmic Koala on.  Due to a bug on startup I have to manually interupt startup by pressing escape on the keyboard and editing the startup command line.  Basically I modify acpi=force to acpi=ht or off.  This allows me to boot but it kills all the acpi power saving etc..  I was doing this through lots of updates successfully even though I probably should have just edited my startup permanently so that I could reboot/startup without this manual process.   The latest update for the kernel last night told me to reboot and upon restart it no longer recognizes my usb keyboard so that I can press escape and edit the boot command.  This now means I can no longer boot into ubuntu.  I am typing this from my windoze pc for work.  

A couple of observations:
1. The usb keyboard works as I can use it to enter bios. 
2. In BIOS I checked to verify everything was enabled.

What are my options here?  I think the only thing I can do is either use a usb stick or livecd to get access and startup the pc.  Then go in copy my files out and reinstall.  Unless using the livecd would allow me to modify the startup boot line to add acpi=ht.  

Can anyone help.

---

### Post by Favux on 2009-12-05
Hi alexvd,

When you boot you should be able to chose to boot using your previous kernel that worked.

You might also try using:
```
acpi_osi="Linux"
```
instead of acpi=ht or off.  See if that gets you anywhere.

---

### Post by alexvd on 2009-12-06
Favux

Thanks for the reply.  The issue I have is that I cannot interrupt the startup because the escape key is not recognized by my usb motion keyboard. It works in bios so I no the keyboard is not broken.  Basically I get the bios screen and then the "starting up" message and then it hangs.  This is due to the bug that has been out thier for ages.  I think your aware of this already.

With the livecd can I get into the pc and modify the existing grub?

---

### Post by Favux on 2009-12-06
Hi alexvd,

Sorry for being dense.  Yes off the live CD you need to mount the drive you want to modify.

---

### Post by guyhillyer on 2009-12-11
Hi alexvd,

I was just contemplating installing ubuntu on my m1400.  Can you say which is the latest kernel version that doesn't have the usb problem?  Were you able to get the usb keyboard to work with the latest kernel after booting with acpi=off?

My Motion cd drive is broken, so I was planning to move the drive from the m1400 into another laptop and do the installation there.

Thanks

---

