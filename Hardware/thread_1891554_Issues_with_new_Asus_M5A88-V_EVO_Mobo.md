---
title: "Issues with new Asus M5A88-V EVO Mobo"
date: 2011-12-05
forum: Hardware
---

### Post by Georgette Burdell on 2011-12-05
I'm having difficulty installing Ubuntu on a new build.  I think I've tracked the issue to BIOS settings, but I'm unsure how to address it.    No matter how the boot priority is set, the motherboard seems to hang on checking my older IDE devices.  As long as devices are connected to the IDE ribbon cable, it will try to boot from them and inevitably hang on a blank screen with a flashing cursor.  Initially, booting from LiveCD's would usually get me to the text menu, but selecting any of the options would just give a flashing cursor.  Eventually, I installed WinXP and upon reboot .... the flashing cursor.  I tried multiple cables and devices and was unable to boot the computer until the IDE ribbon cable was disconnected from the motherboard.  Digging through the BIOS options, I disabled the IDE Boot ROM option.  Now the O/S will boot and recognize the older IDE devices, but I can no longer boot from the CD drive.  Making it quite difficult to install Ubuntu.  I'm hoping someone here may have some insight on things to try to fix this.  Hardware ASUS M5A88-V EVO AMD FX 4100  Seagate Barracuda 1TB HP DVD Writer LiteOn  Thanks in advance for any help you can give.

---

### Post by Micke184 on 2012-01-02
> **Georgette Burdell said:**
> I'm having difficulty installing Ubuntu on a new build.  I think I've tracked the issue to BIOS settings, but I'm unsure how to address it.    No matter how the boot priority is set, the motherboard seems to hang on checking my older IDE devices.  As long as devices are connected to the IDE ribbon cable, it will try to boot from them and inevitably hang on a blank screen with a flashing cursor.  Initially, booting from LiveCD's would usually get me to the text menu, but selecting any of the options would just give a flashing cursor.  Eventually, I installed WinXP and upon reboot .... the flashing cursor.  I tried multiple cables and devices and was unable to boot the computer until the IDE ribbon cable was disconnected from the motherboard.  Digging through the BIOS options, I disabled the IDE Boot ROM option.  Now the O/S will boot and recognize the older IDE devices, but I can no longer boot from the CD drive.  Making it quite difficult to install Ubuntu.  I'm hoping someone here may have some insight on things to try to fix this.  Hardware ASUS M5A88-V EVO AMD FX 4100  Seagate Barracuda 1TB HP DVD Writer LiteOn  Thanks in advance for any help you can give.

I've been trough basically the same thing with similar/exactly the same hardware: ASUS M5A88-V EVO, AMD FX 4100 and a  Seagate Barracuda 2TB. I toppled the whole setup with 8G DDR3 from Corsair. In addition I also have a DVD (noname) and an old HD on the IDE.

The result is exactly the same, even though I have tried to install Fedora 16 x86_64 and i686 (sic!) ;). The original install DVD will simply hang. I, however, found that the Live CD would install with if I  enabled the IDE Boot ROM option in the BIOS. The installation was done to the SATA HD. After the installation I simply disabled the IDE boot option again.

The system x86_64 now works but behaves "funny" in a multitude of sad ways :(


[LIST]
[*]I do not get any login screen - I have to boot it to run-level 3 and start the window manager manually (XFCE)
[*]If I try to play a movie something goes terribly wrong inside the kernel and the XFCE dies.
[*]Random crashes
[/LIST]
I first though it was the IDE-DVD that would the be culprit and hence bought a new Sony SATA DVD but with the same result (even though I have not reinstalled completely yet)


I have also tried to install Windows XP and Vista to the IDE connected HD. Neither would boot properly. XP gives blue screen with "unmountable_boot_volume" and Vista simply hangs and reboots.


So my next two/three steps are 


[LIST]
[*]to see if Windows XP could work from a separate partiontion on the SATA HD
[*]Reinstall the Fedora from scratch with all the work it will take
[*](try the i686 version of Fedora)
[/LIST]
So if anyone could shed some light here or give me any fresh ideas I would be very happy.


Georgette Burdell: Did you get yours up and running?

---

### Post by Georgette Burdell on 2012-01-03
I was able to get my system up and running by installing from a USB stick.  However, either the first round of updates or installing the drivers for the on-board sound promptly broke the system again.  While it was working, I could see and use both the IDE HD and the optical drive.  I have since reinstalled off the USB stick, but I am hesitant to update the system immediately.  (The first kernel update for the last LTS broke my video on my last system.  Subsequent updates were fine.)  I also currently have the IDE disabled in the bios as part of the troubleshooting from the system breaking.  I will try re-enabling the IDE controller and making sure everything still works.  Sorry I can't really be of more help ...  EDIT: I was able to install Windows XP and boot that while I was having issues with my Ubuntu install.

---

