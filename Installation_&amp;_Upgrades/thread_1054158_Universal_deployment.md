---
title: "Universal deployment?"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by sbkdrb on 2009-01-29
Hey all,

I'm brand new to Linux, so please bear with me if some things bounce off of my skull.

I have a nonprofit charity that refurbishes donated computer equipment and distributes it to those in need at no cost. Some of the machines we get do not have licenses, and we have decided to use a mix of Ubuntu/Edubuntu and Puppy-Linux (for the very old hardware). The problem I'm having is trying to come up with an integrated solution for processing the machines.

Windows OS Process
Boot to Utility CD
Shred hard drives to preserve data
Use Ghost to burn a pre-configured + updated universal image


Is there a way to create a hardware independant image so that I can duplicate this process with Linux?

Jason

---

### Post by dagriff on 2009-01-29
You will want to look at the automatic installation systems on Ubuntu

There is KickSeed, which processes a redhat style kickstart file. It can do most things in an automated fashion and is very simple.

```

sudo apt-get install system-config-kickstart

```

You will then need to edit the boot loader on the install cd (isolinux) to pass in the kickstart file "install ks=http://some.where/ks-test.cfg"


For more advanced stuff, you will need to look at preseeding the debian installer. The way we currently do it at work involves a custom initrd.gz in the CDROM.

EDIT: 

Forgot to say that the system-config-kickstart tool allows you to generate kickstart files suitable for automated installations.

---

