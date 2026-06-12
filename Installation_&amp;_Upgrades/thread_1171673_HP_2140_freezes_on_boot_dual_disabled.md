---
title: "HP 2140 freezes on boot/ dual disabled"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Nunatak on 2009-05-27
Hi all,

I just wanted to install UNR 9.04 on my new Hp2140 via USB, doesn't work. I turned off dual core in the bios, turned off the vent, increased boot time to 5 and upgraded bios to F3 via usb stick. Nothing helps. After pressing f9 I choose boot from usb, that's where it stops. Screen is black but for the menu option f10 to enter bios, when I do that it changes the word to entering bios or some such and then stops. I tried several usb sticks, no change, bothe ports, no change.

Anyone have a clever idea?

---

### Post by subnivean on 2009-06-04
I'll second this - tried everything suggested in the forums to no avail. When I first received the netbook it still had XP Home on it and I could get UNR to start via F9 after a 'Shutdown | Restart' from Windows. I used that trick to install it, but now I want to reinstall with ext4 filesystem and I can't since I've wiped XP.

I've tried several media sticks, multiple image downloads, both ports, etc. Unit came with F03 Bios pre-installed. FWIW, I can boot several other laptops with this USB stick, and I *can* boot the netbook with a regular Jaunty (non-UNR) image. (Slight aside: would it be ok to just install the standard Jaunty and install the UNR packages later?)

I don't know if this matters, but this 2140 has the HDD display (1366 x 768 ). Other than that I'm stumped.

Thanks

---

### Post by cos^ on 2009-06-05
Try resetting bios settings. I fought with the netbook not able to boot from USB disk for long time, but finally HP support chat resolved the issue. Looks like the BIOS has bug and it can't boot from USB until the settings have been reset.

---

### Post by Nunatak on 2009-06-06
Hi what do you mean you reset deafaults. Did you turn off dual afterwards? Can you give a little more detail? Btw just borrowed an external usb-cd drive from a friend. It can see the regular ubuntu cd, but unfortunately the remix is not available on cd. anyone have any hints. I have been reading forums for hours and talked to the support twice to no avail.

---

### Post by Harlort on 2009-06-08
I have the same problem. Installed 9.04 on my brand new HP2140, everything worked, 9.04 downloaded updates and I installed them. After that I cannot get
the wireless to work. Tried a lot of things, but since I'm a newbie to Ubuntu I'm
lost right now.
 
When I now want to reintall the 9.04 it seems I can't, after reading this thread.
 
To me Ubuntu isn't ready for a user like me. I don't have the time or experience to
solve issues like this. I'm going back to Windows, to bad becouse I was really curious about Linux and Ubuntu.
 
I'm a bit sad.

---

### Post by barney.baldwin on 2009-09-27
> **subnivean said:**
> I'll second this - tried everything suggested in the forums to no avail. When I first received the netbook it still had XP Home on it and I could get UNR to start via F9 after a 'Shutdown | Restart' from Windows. I used that trick to install it, but now I want to reinstall with ext4 filesystem and I can't since I've wiped XP.

I've tried several media sticks, multiple image downloads, both ports, etc. Unit came with F03 Bios pre-installed. FWIW, I can boot several other laptops with this USB stick, and I *can* boot the netbook with a regular Jaunty (non-UNR) image. (Slight aside: would it be ok to just install the standard Jaunty and install the UNR packages later?)

I don't know if this matters, but this 2140 has the HDD display (1366 x 768 ). Other than that I'm stumped.

Thanks
I struggled with this yesterday as well, and could find no conclusive solution in the posts. However, I finally got it to work this morning.
For whatever reason, the bootable USB stick created with ImageWriter on my Ubuntu 9 desktop doesn't work (same issue as described here), but using unetbootin-windows-372 on my XP laptop created a bootable flash with the UNR 9.04 image. 
Hope this helps someone.

---

### Post by acalora on 2009-09-27
> **barney.baldwin said:**
> I struggled with this yesterday as well, and could find no conclusive solution in the posts. However, I finally got it to work this morning.
For whatever reason, the bootable USB stick created with ImageWriter on my Ubuntu 9 desktop doesn't work (same issue as described here), but using unetbootin-windows-372 on my XP laptop created a bootable flash with the UNR 9.04 image. 
Hope this helps someone.

Could you elaborate, please? I have a similar problem, but I installed it on an External hard drive. And now my computer won't boot anything. I think it's because GRUB is on the external drive and my bios can't boot from my usb hard drive.

---

### Post by barney.baldwin on 2009-09-27
I was referring specifically to the issue described for the 2140 - hang on boot. If your BIOS doesn't support booting from USB, this won't help. What exactly are you trying to do?

---

