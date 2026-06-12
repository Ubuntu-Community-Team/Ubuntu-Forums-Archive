---
title: "Getting Ubuntu to work with new Kaveri chip"
date: 2014-02-12
forum: Hardware
---

### Post by Peter_Witteveen on 2014-02-12
Hi all,


I am trying to get Ubuntu to work on a new system:

CPU > AMD A10-7700K 'Kaveri'
MSI main board with A88x chipset
8GB of 1600 mHz RAM
AMD GPU R7 250 Radeon

Device to install to would be an 60GB SSD. (Ubuntu 13.1)


A lot has happened, chronologically:


I took out the old mainboard/cpu/gpu and put in the new components.

There was a win7/Ubuntu 13.1 dual boot.
Win7 was not on the SSD.

Both would boot, Win7 had no hardware acceleration, Ubuntu worked, but no sound. (sound could have various reasons)
Because of the no sound I decided to re-install Ubuntu.

Ubuntu live would load, but after installation grub couldn't find the partition.

Grub: no such partition
Grub rescue

I wanted to verify that Ubuntu wasn't the problem (attempts to fix grub did not work, Uefi Bios has been looked over multiple times)
So i loaded OpenSuse live and Fedora live from USB images which worked before on other systems.
These would boot, but would not enter the graphical login screen.

Fedora had this to say:

fb (framebuffer I assume): conflicting fb hw usage Radeonrmfb vs EFI VGA- removing generic driver.

This afternoon I tried another reinstall of Ubuntu which now was able to boot after installation.
It booted so fast that I could not notice any grub, so I was not able to test Windows.
When inside Ubuntu, no hardware acceleration.
The Additional Driver option was not available.
I manually installed AMD's catalyst.
The install script suggested a reboot.
After reboot, blank black screen.

Having said this, this is my question:

What is going on?

My guess, Either I messed up in the BIOS, which I doubt, or something is wrong HW-wise.
Or... AMD's Kaveri line-up was launched (out for several days now, got it day 1) without good drivers and without any OS able to deal with it.

No OS works with this system, and I prefer to use Ubuntu which I have tried and tested with the most.
Getting Win7 to work is a secondary thing.

I have spend time googling Kaveri and other ppl have similar issues, but I can't imagine that there are APU's on the shelf that just won't work at all.


Thanks in advance for any tips/insights.


Peter Witteveen
I

---

### Post by grahammechanical on 2014-02-12
The Linux developers are always playing Catch Up when new hardware comes out. So, Ubuntu is booting but no Grub menu? That happens when Grub only sees a Linux OS.

When in Ubuntu open a terminal an run

```
sudo update-grub
```

Watch the screen printout. Does it see a Windows OS? Was the drive with Windows 7 connected during installation? I think that it is wise not to have the drive with another OS on connected during installation but then we need to run that command that I gave you. Without the Windows 7 drive connected the Grub os-prober utility will not find Windows 7.

Regards.

---

### Post by Peter_Witteveen on 2014-02-13
Thanks for your reply.

I am currently without a vga driver, so I must enter Ubuntu in runlevel 3 to reach a command line.
Usually I would use the 'e' button to add it as a boot parameter in grub.

I looked this up on google and people talk about either using grub or editing a config file.
Both would not work in this case.

Previously I installed grub via live-usb.
Grub would appear, but not working and giving the error in my main post:

Grub: No such partition
Grub rescue>

---

### Post by Peter_Witteveen on 2014-02-19
I am going to wait till April when a new Ubuntu will be released.
In the meantime I will use Win7 which I got working.
Thread can be closed.

---

