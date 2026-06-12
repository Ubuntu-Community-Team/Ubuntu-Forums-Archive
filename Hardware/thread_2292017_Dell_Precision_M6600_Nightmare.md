---
title: "Dell Precision M6600 Nightmare"
date: 2015-08-24
forum: Hardware
---

### Post by chadrlz on 2015-08-24
I have a Dell Precision M6600 (bios A09) that I am working on. I have tried ubuntu 15.04 (32-bit and 64-bit), Zorin OS 9(64-bit) Zorin OS 10 (32-bit and 64-bit), Linux Mint 17.2 Mate (64-bit), Sabayon Linux 15.08 (64-bit), and Ubuntu 10.04 (which I am currently installing. 

I have disabled the following in bios: Multi-core, hyper-threading, free fall protection, C-States, and the over-clocking stuff (can't recall exact name for those options)

With the last one that I ran Sabayon it was working until I tried to access the power options. On various versions of ubuntu it has a ACPI modprobe failed message that briefly displays on screen while it is booting. I really need to get this working. Ubuntu 10.04 loads but fails to install, possibly due to a dirt disc, need to get another download of that. It's possible that it has something to do with the display but I don't know the exact command to put into the boot sequence to tell it to use a different display adapter/driver. I know these are problematic units to begin with but I really need to get this thing going so any help would be greatly appreciated.

It might help to mention that in XP Pro which I know is not a supported OS with this model, does fine until you do certain drivers, namely the video which in this case is an ATI. The whole unit just shuts down and you have to unplug it and take out the battery then plug it back in to get it to POST.

---

### Post by oldfred on 2015-08-24
Did you try Lubuntu.
Ubuntu now requires newer hardware & often better video card/chip to support Unity.

10.04 is not supported any more.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by grahammechanical on 2015-08-24
You may need to set the nomodeset boot option. This wiki page will show you how to do that. Go to the section called "Changing the CD's default boot options" and look for section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Another point to consider is this: the latest versions of Ubuntu install newer proprietary video drivers. Depending on the age of the graphic adapter in that machine the newer proprietary video drivers may no longer support the video adapter. When installing do not tick the box "Install third party software." Then Ubuntu will be installed with an open source video driver. The live session uses the open source video driver. So, if the live session works fine then stick with that for the installation.

When we have a working installation of Ubuntu we can install third party audio and video codecs by installing Ubuntu Restricted Extras from the Ubuntu Software Centre and experiment with proprietary video drivers by going to System Settings>Software & Updates>Additional Drivers tab. These instructions apply to Ubuntu 14.04 and 15.04 and not to 10.04. 

You do not actually describe what problems you are seeing. So, we cannot give advice to deal with the specific problems you are seeing. As for the ACPI modprobe failed message, do not be distracted by it. It is a system message that really should be hidden by a splash screen. I saw that through a good part of the 26 week development period of Ubuntu 15.04. It did not affect my use of 15.04 at all. And it is not present in 15.10.

Regards.

---

### Post by monkeybrain20122 on 2015-08-24
That computer looks quite new (2011?) and has good specs (corei5 or corei7) What exactly is it that doesn't work and why do you disable multicore and other useful options in bios?? The ACPI thing is not important as far as I know. I used to get that too but everything worked (it was gone later after a few kernel updates)

---

### Post by chadrlz on 2015-08-24
This unit shuts down. Thats what it does. I can not even get a live session with any of the newer ubuntu discs. The only that even successfully loads is the 10.04. The newer version of Zorin loads to a live session but as soon as I try to access the menu (bottom-left) it shuts down. In Sabayon (gentoo-based) it is fine until I access the power options. In XP it's fin until I do the video drivers. I can hear what sounds like a relay. These models have a lot of weird stuff associated with them and a lot of people have had problems very similar to mine however they have no answers that have worked for me. It is really quite simple there is a piece of hardware that is being accessed that kicks a relay and shuts the unit down. By unplugging the unit and removing the battery you are effectively telling the BIOS "it's ok now" I'm trying something different. It could be that the hardware that it is trying to access is faulty. This thing ran hot for years before it ever made it to me. I was hoping someone here would know what piece of hardware that is. Whatever it is it isn't accessed in 10.04 because I can install that and access all kinds of stuff with no problems. 12.04 does the exact same thing as the others it shuts down before even getting to a desktop. These are all live sessions. I have had a long day, I will have to try some more suggestions tomorrow.

---

### Post by oldfred on 2015-08-24
With 12.04 perhaps it needs the Dell Sputnik drivers. Supposedly all those were in the 14.04.

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

Dell normally works well with Ubuntu.

---

