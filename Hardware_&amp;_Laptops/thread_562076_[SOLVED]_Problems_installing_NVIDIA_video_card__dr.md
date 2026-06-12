---
title: "[SOLVED] Problems installing NVIDIA video card / drivers"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by dylanologist on 2007-09-28
I got a new 22" widescreen LCD monitor, and so I decided it would be a good time to upgrade from my Intel integrated graphics to a dedicated video card.  I choose an NVIDIA GeForce 8400GS.  However, every attempt I've made to install this new card has failed.

Here's what I did:

a) Made sure I had the restricted drivers repositories enabled.  Downloaded the proper driver from nvidia.com (after making sure that the card I had was supported by that driver).
b) Booted into the BIOS and disabled the integrated graphics, saved, and shut down.
c) Installed new video card in PCI-E slot and switched the monitor cable from the motherboard graphics output to the video card graphics output (I've tried w/ the analog cable, the digital cable, and both at the same time, w/ no difference in the final outcome).
d) Booted the machine - saw the Asus MB splash screen, and also the Grub 1.5 message (or something like that).  After that I get a blank screen and my monitor tells me there's no signal.

I can't use the restricted drivers manager in the GUI because I can't get to the GUI.  I also can't get to a terminal when I do a normal boot.  However, I am able to boot into the safe mode, and access a CLI that way, but when I tried to install the driver I downloaded from nvidia.com I get an error message - something about being in level 1 when I should be in level 3 (or vice versa, I can't remember off hand).  I assume this has to do with the fact that I'm in safe mode rather than the standard mode.  I tried going ahead with install anyway but encountered more errors and so the install failed.

I've also tried booting into safe mode and editing xorg.conf manually, changing the driver from "vesa" to both "nv" and "nvidia" but neither seemed to work.  Clearly the graphics card is working, because I can see stuff on the screen during boot.  And if X isn't starting properly, shouldn't I still be able to sign in and work from the CLI?

Any ideas why I'm getting a blank screen in standard mode but safe mode works?  I'm running Feisty 64bit if that makes any difference.  Let me know if I should post contents of xorg.conf or anything else that would be useful in diagnosing the problem.  Any help is of course greatly appreciated.  And did I mention that I am still something of a noob at this Linux thing?

---

### Post by kakalaky on 2007-09-28
Reboot into normal mode. When done booting press ctrl-alt-f1 to drop to a terminal and run this:
```
sudo /etc/init.d/gdm stop
```

install the driver, then

```
sudo /etc/init.d/gdm start
```

Edit:  you also might need to remove any vga= statement from menu.lst if you can't drop to a terminal

---

### Post by dylanologist on 2007-09-28
Thanks for the reply, but no dice.

I booted to the black screen, tried ctrl+alt+f1 but nothing happened.  Also tried ctrl+alt+f2 - f10 but none of them did anything.

Went back to integrated graphics, ran "sudo rcconf" and turned off gdm that way.  Restarted and was brought directly to the CLI.  However, when I reinstalled the NVIDIA card and booted it didn't bring me to the CLI but instead I got the black screen again.

Oh yeah, in menu.lst I didn't find any reference to VGA, but maybe I can check again.

I'm wondering if there's anything else I could turn off using rcconf that might help, but I don't want to do any serious damage.  Any other ideas?

---

### Post by dylanologist on 2007-09-28
The one idea I could think of seems a bit crazy:

1) Turn off gdm.
2) Install NVIDIA card.
3) When I boot up normally I'll hit a black screen, but I can assume (I think) that underneath the black screen I've booted into the CLI.
4) Enter the following info very carfully (as I would be working blind):

 a) username
 b) password
 c) cd /directorywithNVIDIAdriver
 d) sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
 e) password

The problem is at this point I would be at a loss for what to do.  I would need to know exactly the procedure for installing the NVIDIA driver (something I've never been able to do successfully) and I would have to hope for no error messages during the installation (because I wouldn't be able see them).  Does this sound at all feasible?

---

### Post by kakalaky on 2007-09-28
The part with vga= in it should look something like this (look at the end of the kernel line):

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/mapper/nvidia_ceejdgda2 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.20-16-generic
boot

```

---

### Post by dylanologist on 2007-09-28
No sign of "VGA=" in my menu.lst file.

I had another thought though.  It seems that the NVIDIA card is working up until the OS loads, and it's working if I boot into recovery mode.  Is it possible that, when I boot in normal mode, that the OS is defaulting to the integrated video rather than to the PCI-E video card?  This wouldn't make much sense, because the integrated video has been disabled in the BIOS, but it would explain the lack of any video output (clearly it's not just a problem with the GUI, because I also can't see anything if I boot to a CLI either).

---

### Post by dylanologist on 2007-09-28
Here are some of the contents of menu.lst if it's any help:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=411100c1-9adc-481c-860d-a9b996e805a0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=411100c1-9adc-481c-860d-a9b996e805a0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=411100c1-9adc-481c-860d-a9b996e805a0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=411100c1-9adc-481c-860d-a9b996e805a0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kakalaky on 2007-09-28
remove the "quiet spash" part and see if there are any error messages while booting.  You also might want to look at /var/log/Xorg.0.log

BTW, you don't have to actually edit menu.lst to change it.  Just hit esc when prompted during boot by grub and highlight your kernel.  You can then press e to edit it and press b to boot when you are done editing.  These changes will not be permanent, but it is much easier to troubleshoot this way.

---

### Post by dylanologist on 2007-10-01
Thanks for the help, but I'm getting a bit tired of the whole process of switching between integrated graphics and the new card.  Plus, I'm worried that installing and uninstalling the new card over and over again will end up damaging it or the pci-e slot.  I think I'll wait until the next version of Ubuntu comes out in a couple of weeks and see if I have any better luck with that new version.  Thanks again for the help though, I do appreciate it.

---

### Post by dylanologist on 2007-10-02
Finally I upgraded to Ubuntu 7.10 Beta (Gutsy) and that seems to have solved my problems.  I did the auto reconfiguration of xorg.conf, which loaded the "nv" driver, and when I entered the GUI I was prompted regarding installation of the proprietary driver.  I enabled that driver, and everything worked just fine.  I probably should've waited for the official release, but I'm happy to finally have the proper 1680x1050 res on my nice new widescreen LCD.

Thanks again for the help.  I learned a few tricks that will probably be handy down the road.

---

