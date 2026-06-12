---
title: "usb stick doesn't work anymore even if correctly ejected"
date: 2015-10-10
forum: Hardware
---

### Post by kr0n1x on 2015-10-10
Hi, I was using my usb stick (a Kingston DataTraveler MicroDuo 3.0) on Ubuntu Mate 15.04 64bit.
I was copying some data in it (more than 1 GB) and once it finished (at least the GUI said so), i did the usual "Eject" thing from the file manager.
Some error showed up about IO problems. Probably data wasn't completely flushed from buffers to the usb stick.
Anyway, I phisically eject the usb stick and I plug it in again. Same error. Eject (software and physical) and plug it in again.
This time it's like I've plugged nothing in. I try it in Windows 7, nothing too.
I try it on another system, same problem.
It's like it completely destroyed (some pin fault?).
I haven't used it much, I got it for like 3 months but very limited use since then.

This is not the first hardware damage this distro has done to my system.
Two weeks ago the laptop speaker got some damage while the laptop was coming back from sleep mode (or maybe while it was going into sleep mode), maybe because the music player was on while this happened.

Is it possible to recover this usb stick?

Thanks for your time

---

### Post by v3.xx on 2015-10-10
No warranty?

My $8 stick came with a one year warranty.

---

### Post by kr0n1x on 2015-10-10
It was a gift :( I don't know if I can get that. What if I can? I should send the "broken" one to the company... it would probably cost more than what it is worth.
I hope in some technical solution to recover this one.

---

### Post by v3.xx on 2015-10-10
I don't know how shipping and handling works on your side of the pond.

You say that it has been tried on other machine and windows with same results.  Sorry, but that's dead to me, RIP

---

### Post by Yellow Pasque on 2015-10-10
Have you tried fsck'ing the volume?
If you don't care about the data on it you should also try creating a new partition table in gparted.

---

### Post by weatherman2 on 2015-10-10
> **kr0n1x said:**
> This is not the first hardware damage this distro has done to my system.

I'm not aware of any way an operating system can cause "hardware damage" to a USB flash drive  Corruption might occur in rare cases, but it's never happened to me with a USB flash drive.

I have had USB flash drives fail, though.  It is not uncommon.  They are highly vulnerable to ESD (Electrostatic Discharge) where a spark of static electricity destroys the entire drive.  This can occur by accident if, say, the computer is not properly grounded and you get a shock when you touch it and somehow touch the metal part of the USB drive.

If you plug the drive into a Linux machine and there is no reaction at all - no new output when you type "dmesg" in a terminal right after you've plugged the drive in - then it is probably a hardware failure unrelated to Ubuntu.

If you plug it in and you DO see a reaction (messages at the end of the dmesg output) then maybe it is alive.  Start up Gparted and see if any partition still exists on there.  You could also try testdisk to try to recover files from it, if the device is alive, at least.

---

### Post by coldraven on 2015-10-11
I revived a dead stick with mkusb. Use the "Wipe first megabyte" option. I've forgotten but most likely you will then need to re-format it with gparted. Maybe best to do a search for more info on this topic before zapping it.
mkusb is in the Software Centre

---

### Post by kr0n1x on 2015-10-11
> **Temüjin said:**
> Have you tried fsck'ing the volume?
If you don't care about the data on it you should also try creating a new partition table in gparted.
The OS doesn't see the plugged usb stick, so fsck or gparted can't see it either.

> **weatherman2 said:**
> I'm not aware of any way an operating system can cause "hardware damage" to a USB flash drive  Corruption might occur in rare cases, but it's never happened to me with a USB flash drive.

I have had USB flash drives fail, though.  It is not uncommon.  They are highly vulnerable to ESD (Electrostatic Discharge) where a spark of static electricity destroys the entire drive.  This can occur by accident if, say, the computer is not properly grounded and you get a shock when you touch it and somehow touch the metal part of the USB drive.

If you plug the drive into a Linux machine and there is no reaction at all - no new output when you type "dmesg" in a terminal right after you've plugged the drive in - then it is probably a hardware failure unrelated to Ubuntu.

If you plug it in and you DO see a reaction (messages at the end of the dmesg output) then maybe it is alive.  Start up Gparted and see if any partition still exists on there.  You could also try testdisk to try to recover files from it, if the device is alive, at least.
dmesg shows nothing when I plug it in or out.

> **coldraven said:**
> I revived a dead stick with mkusb. Use the "Wipe first megabyte" option. I've forgotten but most likely you will then need to re-format it with gparted. Maybe best to do a search for more info on this topic before zapping it.
mkusb is in the Software Centre
I can't find mkusb in Ubuntu Software Center. But probably mkusb wouldn't see the device, since the OS doesn't.

---

### Post by SuperFreak on 2015-10-11
You could try plugging it into a Windows PC .
I have recovered a USB stick that appeared dead with a low level format. You will likely find access to low level format software at your manufacturers web site. You will probably have to use Windows to use it though

[http://www.techspot.com/community/topics/how-to-fix-an-unreadeable-usb-flash-drive-illustrated.63357/]("http://www.techspot.com/community/topics/how-to-fix-an-unreadeable-usb-flash-drive-illustrated.63357/")

---

### Post by kr0n1x on 2015-10-11
Tried it. The device doesn't show up in the list, just my laptop hard drive does.
Tried also a kingston utility for another usb stick, no luck.
It's like I insert nothing in the usb port. I can't believe this usb stick got broken so easily. 3 months lifetime. I got years old usb sticks that cost less than this one.

---

### Post by v3.xx on 2015-10-11
Could it be a knock-off?

[http://www.kingston.com/us/support/product_verification](http://www.kingston.com/us/support/product_verification)

---

### Post by kr0n1x on 2015-10-11
> **v3.xx said:**
> Could it be a knock-off?

[http://www.kingston.com/us/support/product_verification](http://www.kingston.com/us/support/product_verification)

Can't check because:
> The following products **do not** feature Phantom or color shift technology: microSD, microSDHC (4GB-32GB), DataTraveler SE9, DataTraveler SE9 G2, DataTraveler GE9, DataTraveler microDuo 2.0, **DataTraveler microDuo 3.0**, DataTraveler microDuo 3C, DataTraveler Micro 3.1, DataTraveler Vault Privacy 3.0, DataTraveler Vault Privacy 3.0 Anti-Virus, DataTraveler 4000G2, USB 3.0 High-Speed Media Reader, MobileLite G4 Reader and USB microSD/SDHC/SDXC Reader. 

But the package looked legit... it came from Amazon seller.

---

### Post by coldraven on 2015-10-11
> **kr0n1x said:**
> I can't find mkusb in Ubuntu Software Center. But probably mkusb wouldn't see the device, since the OS doesn't.

Sorry I got that wrong it is installed from a PPA but there are only versions for 12.04 and 14.04
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2015-10-12
> **kr0n1x said:**
> The OS doesn't see the plugged usb stick, so fsck or gparted can't see it either.

If the pendrive is not seen as a mass storage device (for example as /dev/sdb), mkusb can't do its job.
> 
dmesg shows nothing when I plug it in or out.

I can't find mkusb in Ubuntu Software Center. But probably mkusb wouldn't see the device, since the OS doesn't.

You find [information about mkusb here](https://help.ubuntu.com/community/mkusb). It is not [yet] in the Software Center. The fastest way to start making USB boot drives is to install the mkusb PPA, install and update the mkusb package like all the other program packages.

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

Edit: The [PPA](https://launchpad.net/~mkusb/+archive/ubuntu/ppa/+packages) contains mkusb for all current Ubuntu versions: 12.04, 14.04, 15.04, and Wily (15.10). It is a bash script, and actually the same script works for all Ubuntu versions.

-o-

Maybe the pendrive was damaged by an electrostatic discharge. Maybe it was damaged in some other way. Pendrives are mass produced, and some individual pendrives have a very short lifetime while most of them last for years (when used in a sensible way). See [this link](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297) for more details.

---

