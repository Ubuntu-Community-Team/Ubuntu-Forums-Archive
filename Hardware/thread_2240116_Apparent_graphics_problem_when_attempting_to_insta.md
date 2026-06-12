---
title: "Apparent graphics problem when attempting to install v14.04LTS"
date: 2014-08-18
forum: Hardware
---

### Post by bobmac on 2014-08-18
Folks,

When attempting to upgrade from v12.04LTS to 14.04LTS the following displays:

Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?

The above URL shows the following:
When updating your system with Update Manager, you will see a warning if your machine does not have*3D support for running the unity desktop environment. This could happen for several reasons:
Outdated hardware not providing required level of OpenGL support
Too new hardware without driver support yet
Obscure hardware without 3d support
Virtual machines
Binary drivers required but not installed
If you choose to continue anyway, Ubuntu will try to run using software rendering (via LLVMpipe). While llvmpipe is pretty good on modern CPUs, if your video card is old your CPU is likely old too, and it may result in unusable performance.
Alternatives may include sticking with an old ubuntu release or switching to one of the lighter weight derivatives or Debian. For 12.04 and 12.10, ubuntu-classic (no effects) is also a feasible option. To do this, install the gnome-session-fallback package, and then on the login screen click the gear icon and select "Ubuntu-classic (no effects)".

I would like to be able to install the new version but I don't know what I can do to fix the problem as I haven't a clue what any of the information above means. 

The current version is 12.04.4 LTS with all the latest updates.

My system is less that a year old. It has an AMD chip and 8GB of memory and more than adequate disk space to accommodate a new version.

When I enter:

sudo lshw -C video, the following displays:

*-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdee0000-fdeeffff memory:fdd00000-fddfffff

The 'user manual' for the Gegabyte 78LMT-USB3 main board appears to say that the video (card) is actually part of the main board.

Does this mean that I need to get an individual new Graphics card, and if so what suggestions do you have, or does it mean that my main board is now defunct. The system is less than a year old.

Any other information you require please let me know.

Regards,

Bob

---

### Post by user1397 on 2014-08-18
Looks like it might be as simple as installing the proprietary AMD drivers.  Open the dash and type hardware, and open up the additional hardware program, and see if you have the option to install anything else for your graphics card.

---

### Post by bobmac on 2014-08-18
ubuntuman,

Tried your info, but 'Additional Drivers' reports 'No probrietary drivers are in use on this system'.

Regards,

Bob

---

### Post by Yellow Pasque on 2014-08-18
The proprietary fglrx/Catalyst driver no longer supports your GPU (it's actually an older GPU even though you bought it recently). However, it should run Unity fully-accelerated with the open-source radeon driver. 

In other words, the Ubuntu upgrade program shouldn't be giving you that message. It probably (incorrectly) thinks you need a binary driver.

---

### Post by Mark Phelps on 2014-08-18
Ubuntu 12.04 DID support fglrx drivers for your video card, but Ubuntu 14.04 does NOT.  AMD dropped fglrx driver support for your card as far back as Ubuntu 12.04.2.

---

### Post by pme 72 on 2014-08-18
I have had no issues with the same product: RS780L [Radeon 3000] with a fresh install of 14.04 on 2014 04 21. Motherboard is ASUS M5A78L-M LX with one 4GB ram module. Graphics driver is the default open-source Radeon one. 

I did change the setting for dedicated video ram from Auto to 512MB which improved performance in the game SuperTuxKart.

DPM was not enabled by default so I added the boot parameter for dpm to Grub and that worked. I did not notice any performance issues without DPM but enabling it allows the igp to clock down for normal desktop operations and ramp up for games like STK. 

I recently installed Window 8.1 on VirtualBox so I could study Excel for work. No issues.

---

### Post by bobmac on 2014-08-19
Folks,
Many thanks for your replies.
Since the main board doesn't seem to be updateable, would it be possible to buy a graphics card to fix the problem?

Regards,

Bob

---

### Post by Yellow Pasque on 2014-08-19
There is no problem (other than a bug in Ubuntu's upgrader that gives you this false message).

---

### Post by bobmac on 2014-08-19
Temüjin,
Many thanks for your reply and assistance. It seems that I should wait for a bit to again attempt to install v14.04LTS.

Many regards,

Bob

---

