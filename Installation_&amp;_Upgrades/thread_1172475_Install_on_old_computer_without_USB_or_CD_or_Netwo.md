---
title: "Install on old computer without USB or CD or Network"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by jclb111181 on 2009-05-28
I recently bought an old kiosk computer that I plan to turn into a jukebox of some sort. The only propblem is that I need to install ubuntu or Xubuntu on it but I can't because the bios will not support booting from a usb or external cd-rom.  I have tried both ways. I have also messed with the bios to see if I could do a network boot.  Would it be possible to install the hard drive into my desktop, load a cd image onto it or maybe even just install ubuntu and then stick it back into the older computer.  Any help that you could provide would be greatly appreciated. Might it also be possible to install the netbook remix some other way?

---

### Post by x22 on 2009-05-28
> ...install ubuntu and then stick it 
> back into the older computer. 

should work OK

---

### Post by clonne4crw on 2009-05-28
> **x22 said:**
> > ...install ubuntu and then stick it 
> back into the older computer. 

should work OK

No, it wouldn't. If you were to install an OS on another PC, then stick that HDD into another with completely different hardware, the OS would kill itself.
--
Open the kiosk up. Does it have a secondary IDE controller? I would just grab a CD drive from another PC, and use that just to get the OS installed.

---

### Post by Old_Grey_Wolf on 2009-05-28
Try one of these suggestions:
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

I suspect that a computer of that age may not have the necessary RAM to run Ubuntu.

---

### Post by kerry_s on 2009-05-28
> **clonne4crw said:**
> No, it wouldn't. If you were to install an OS on another PC, then stick that HDD into another with completely different hardware, the OS would kill itself.
--
Open the kiosk up. Does it have a secondary IDE controller? I would just grab a CD drive from another PC, and use that just to get the OS installed.

your thinking windows, in linux we can install on 1 computer and stick it in as many computers as we want and it would work. ;)

---

### Post by clonne4crw on 2009-05-28
> **kerry_s said:**
> your thinking windows, in linux we can install on 1 computer and stick it in as many computers as we want and it would work. ;)
My thought is that if the Linux install is configured for specific hardware on a hard drive install, wouldnt it make sense for it to face problems in the event of sudden hardware changes, like drives, kernel architecture, etc?

---

### Post by kerry_s on 2009-05-28
> **clonne4crw said:**
> My thought is that if the Linux install is configured for specific hardware on a hard drive install, wouldnt it make sense for it to face problems in the event of sudden hardware changes, like drives, kernel architecture, etc?

no the modules are dynamic, detected and loaded at boot time.
the kernel is generic, made to run on a wide range of machines.
drivers are not loaded if the device is not there.

i have a laptop with a broken cd drive and have pulled the drive and installed on another laptop, then put it back in with out problems, i have done it like 6 times to date. the broken laptop is a acer 3500, the laptop i used to install is a ibmt20, a very old laptop.
i've done everything from a full install, to just installing the base and finished building it up back in the acer using apt-get.

---

### Post by jclb111181 on 2009-05-28
Where do you install the boot loader so that it will start up in the old machine?  I just tried to install on the hard drive by attaching it to my desktop(I detached the existing hard drives on the desktop).  I installed grub to the same partition as the operating system because I did not want it to screw up my existing setup on my desktop. I then installed it back into the old computer and it says "error loading operating system".  Thanks again for your help!

---

### Post by clonne4crw on 2009-05-28
> **kerry_s said:**
> no the modules are dynamic, detected and loaded at boot time.
the kernel is generic, made to run on a wide range of machines.
drivers are not loaded if the device is not there.

i have a laptop with a broken cd drive and have pulled the drive and installed on another laptop, then put it back in with out problems, i have done it like 6 times to date. the broken laptop is a acer 3500, the laptop i used to install is a ibmt20, a very old laptop.
i've done everything from a full install, to just installing the base and finished building it up back in the acer using apt-get.

Ahhh. OK. My bad. Makes sense to me. 

I learn something new here every day.

---

### Post by kerry_s on 2009-05-28
> **jclb111181 said:**
> Where do you install the boot loader so that it will start up in the old machine?  I just tried to install on the hard drive by attaching it to my desktop(I detached the existing hard drives on the desktop).  I installed grub to the same partition as the operating system because I did not want it to screw up my existing setup on my desktop. I then installed it back into the old computer and it says "error loading operating system".  Thanks again for your help!

detach the other drives, you must put it in as the master, because its going to be the master drive on the machine your putting it on.
then just install normal, like any other install.

---

### Post by jclb111181 on 2009-05-29
Its ALIVE!!!

---

### Post by tgalati4 on 2009-05-29
Once the smoke clears let us know how Frankencomputer turns out.

Another way to quickly load an OS:

Put the old drive on the secondary slot of the ribbon cable of a linux machine.

sudo cp /dev/hda1 /dev/hda2

Put drive in Frankencomputer and boot.

Watch in amazement.

(Machines should be reasonably similar to work 100%.)

---

### Post by kerry_s on 2009-05-29
:lolflag:
you should see my desktop, talking spare parts central.
even use a diy power switch to turn it on. :D

---

