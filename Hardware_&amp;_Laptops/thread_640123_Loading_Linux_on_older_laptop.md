---
title: "Loading Linux on older laptop"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by hbbliss on 2007-12-13
I have an IBM 560x that I want to load with Ubuntu. My laptop does not have a CD-ROM and therefore I can't use the CD to load it. I do have a PCMCIA CD drive but it is not recognized as a boot source like the hard drive or the floppy. The CD-ROM reads fine but just will not serve as a boot device. Currently the 560x has Windows installed and it works ok but I want to switch to Ubuntu. I have both 6.10, 7.04, and 7.10 CD's but they of course want to boot from the CD drive. Is there an easy way to convince my laptop to load Ubuntu? I looked at Smart Boot Manager but it won't recognize my CD drive either and therefore is no help. Any help will be greatly appreciated.

---

### Post by crmanski on 2007-12-13
How about this?
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by Dark_Stang on 2007-12-13
Or maybe a boot floppy that will allow you to boot from your pcmcia cd drive...? This is a new one for me.

---

### Post by JeffoOfMetal on 2007-12-13
What does the computer run already?

If you can get internet access, you might want to try UNetbootin

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

The only thing is you'll need to have a wired connection for part of the install.

So, check to see if your laptop has an ethernet port and if it does, hook it up to your modem, after you've downloaded UNetbootin and rebooted into the text install.

It's tough to explain, but I hope you know what I mean.

---

### Post by hbbliss on 2007-12-14
Alas, no network connection except dialup. I am trying to find a floppy loader that will boot from the CD. Thanks for the suggestions.

---

### Post by W3ird_N3rd on 2008-02-09
> **hbbliss said:**
> Alas, no network connection except dialup. I am trying to find a floppy loader that will boot from the CD. Thanks for the suggestions.
It's a slightly older thread, but in case you still care. I also have a Thinkpad 560X, but running Ubuntu on it isn't really a good idea. De maximum amount of memory this machine can have is 96MB, and the 64MB EDO SODIMM required for that is quite expensive (easily over 25 euro).

What I did was make floppies for Debian, boot with that, load network drivers for my Xircom Realport2 100mbit Cardbus and install Debian from the internet. Since you do not have broadband access, it's good to know there are also drivers for PCMCIA and cdrom drives. You can find them here: [http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/)

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies) could also help.

After Debian has been installed, you could move to Ubuntu with that - but again, with 96MB or less, I wouldn't recommend you to do so. Ubuntu is based on Debian, so you might consider installing a Debian base system. After booting that up, <30MB of memory will be in use. You can "apt-get" everything you want from there (in that case don't get gnome but go for xfce or even jwm). But it will be more work compared to having Ubuntu, you will need to configure more stuff. Still, this is one of the few ways to install a recent system that will run smooth. Xubuntu won't be smooth on this box, if it runs at all with 64MB or less.

You could also look at [http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/), but I have no experience with it.

Also, I have not been able to get the Cirrus Logic CS4237B going. The instructions in [http://www.thinkwiki.org/wiki/CS4237](http://www.thinkwiki.org/wiki/CS4237) don't work for me. [http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode) does not work either. Alsaconf detects a CS4232 (which is wrong. it should use the CS423**6** driver) and is not able to start it. Running the ISA non-pnp search with alsaconf, no dice. Everytime the same error the device couldn't be found when modprobe tries to load the driver. I'm starting to think it has to do with the simple/quick boot option that should be disabled to get this working, but there's no such option in the BIOS (easy setup). The changelog does not seem to indicate there would be anything different with the most recent BIOS. I've been trying for hours and am starting to think this is impossible.

So, could you run Ubuntu on it.. Really slow and without sound? I guess so. But should you want to? Debian or another distro that needs less memory, still without sound? You could. I guess you can't have it all on an older machine.

---

### Post by twiddler on 2008-02-09
I would try using "xubuntu', its much smaller and works fine for older computers, even with just 64mb ram. As for installing it without a boot cd, try this site [http://www.jonlee.ca/installing-xubuntu-without-a-cd-drive-the-weekend-project-continued/](http://www.jonlee.ca/installing-xubuntu-without-a-cd-drive-the-weekend-project-continued/)

If you have a usb port, you maybe able to install from a flash drive using a bootable floppy disk.

---

### Post by W3ird_N3rd on 2008-02-09
> **twiddler said:**
> I would try using "xubuntu', its much smaller and works fine for older computers, even with just 64mb ram.
It won't. Ubuntu as a CLI version already needs approximately 100MB of memory after starting and logging in. No applications have been started at that point yet, there's no Xorg and no XFCE yet. Just a shell where you can type commands. That already needs 100MB with Ubuntu. It's perfect if you have enough memory and want/need all the features, but with 64MB of memory it simply isn't going to run smooth.

On my Thinkpad 600E laptop with 160MB of memory, Xubuntu starts to run a bit. But I would absolutely recommend 256MB if you open a few applications at once, assuming you also want to run apps like Firefox 2.x and not Dillo of Lynx for a webbrowser.

Obviously I don't know what sort of speed you consider to be "fine", but if the 64MB of RAM is already completely filled after logging in and, say, 50MB+ of swap is in use already without even having fired up a webbrowser.. That's not going to be smooth. It's just going to swap all the time. Xubuntu can run with considerably less memory compared to Ubuntu with Gnome, but 64MB is still not going to be enough for an experience that does not include drinking liters of coffee while waiting for something to load.

[edit]
Well I can now say the sound does work. [http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads](http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads) after setpnp it was no more problem. That means my BIOS does quick/simpleboot, though there are no options to change that. Still, a standard Ubuntu (or Xubuntu) will take a bit too much memory to run quickly even with 96MB.

---

### Post by james_vanb on 2008-02-12
Consider trying Wolvix, DSL or Puppy.  They will boot from a USB flash drive.  Takes care of problem with booting from cd or floppy.  Xubuntu probably too much for your laptop.  these take very little RAM to operate effectively.

---

