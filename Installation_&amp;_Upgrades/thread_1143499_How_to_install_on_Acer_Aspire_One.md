---
title: "How to install on Acer Aspire One"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by dugh on 2009-04-30
How can you install Ubuntu Netbook Remix (UNR) to an Acer Aspire One?

It can't boot from an sdhc card.  I also tried burning the UNR .img to a DVD (too big for CD) and connected a USB DVD drive to the Acer, and while it recognized the drive and was selected to boot first in the BIOS, it didn't boot. 

My guess is that the UNR image is bootable only for flash drives, not CDs, for which you need an ISO.  But UNR has no ISO version.

The instructions I've found either completely skip the step on how to get it the live UNR version to boot, or else hack around with grub on Linux that is already pre-installed on the machine - mine had XP pre-installed.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
[http://ubuntuforums.org/showthread.php?t=981951](http://ubuntuforums.org/showthread.php?t=981951)

I'm guessing my only option is to download and burn a regular Ubuntu ISO, install it, and then install all the extra netbook packages.  Or is there an actual solution that works for booting up UNR and installing it on an Acer Aspire One?

(p.s. I installed UNR Jaunty just fine on an Eee PC, it booted from the SDHC slot just fine)

---

### Post by passonno on 2009-04-30
I will get back to you shortly on this, the solution is pretty simple.

---

### Post by passonno on 2009-04-30
Ok, first, you will need at least a 1gb usb flash drive.

Then, go [here]("https://wiki.ubuntu.com/UNR")

The instructions there are pretty straightforward, and you should be able to be up and running fairly quickly.

You can send me a private message if you need further assistance.

Good Luck

---

### Post by dugh on 2009-04-30
Yeah I guess I forgot to mention I already tried that too.  I put the SDHC card in a USB adapter and hooked it up that way, and still wouldn't boot to it, although again it booted just fine on an Eee PC.

---

### Post by lucylettuce on 2009-04-30
I used an SD card in a card reader and that worked ok.
Good luck

---

### Post by dugh on 2009-04-30
Oh OK, I burned it to a regular USB flash drive instead, and that worked! 

Thanks for all your help!

---

### Post by johnhenry on 2009-04-30
Yes, it installs OK. But can you get the wireless configured on 9.04?

I found the wireless works perfectly with 8.10, but not 9.04. I have had to revert to 8.10.

---

### Post by inspectre69 on 2009-04-30
> **dugh said:**
> How can you install Ubuntu Netbook Remix (UNR) to an Acer Aspire One?

It can't boot from an sdhc card.  I also tried burning the UNR .img to a DVD (too big for CD) and connected a USB DVD drive to the Acer, and while it recognized the drive and was selected to boot first in the BIOS, it didn't boot. 

My guess is that the UNR image is bootable only for flash drives, not CDs, for which you need an ISO.  But UNR has no ISO version.

The instructions I've found either completely skip the step on how to get it the live UNR version to boot, or else hack around with grub on Linux that is already pre-installed on the machine - mine had XP pre-installed.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
[http://ubuntuforums.org/showthread.php?t=981951](http://ubuntuforums.org/showthread.php?t=981951)

I'm guessing my only option is to download and burn a regular Ubuntu ISO, install it, and then install all the extra netbook packages.  Or is there an actual solution that works for booting up UNR and installing it on an Acer Aspire One?

(p.s. I installed UNR Jaunty just fine on an Eee PC, it booted from the SDHC slot just fine)

I have an aopen netbook &...
I wondered what would happen if I used unetbootin utility to image my USB key with the Netbook Remix .ISO file. I booted my USB key on the netbook and when it finally finished, I was as the busybox initramfs prompt.  I now see the problem. I had intended to use the distribution image iso it as the bootable installed image, when thats what I am supposed to be using for the source install media.  I will make another attempt at actually loading the key with remix as I want to install it TO the key not from the key.

Is there a way to launch the USB key Ubuntu Netbook Remix thats on the key from where I landed?  Any help would be appreciated.

still working on making an installed ubuntu bootkey thats independent of anything else as far as storage.

My key is only 2gb, this is another problem, & I am wondering if it is enough. I had only 1.1gb left after imaging key with ISO.  I will see if I can get a bigger key to work as well.
Just want to use the key as linux only.  I still need to try the 64 bit 9.04 version on my AM2 Desktop.
I will try it with the WUBI loader as I now have XP on both desktop and netbook.

---

### Post by Cyn Jade on 2009-04-30
> **johnhenry said:**
> Yes, it installs OK. But can you get the wireless configured on 9.04?

I found the wireless works perfectly with 8.10, but not 9.04. I have had to revert to 8.10.

Ouch!!  If you get an answer to this, please post, I am now going to hold off on jumping from XP to UNR on my AA1:  I use it for travel and the wireless capability is not an option.

---

### Post by dugh on 2009-04-30
I spoke a little too soon.  It worked (the live usb image booted), but then I ran the installer, and it choked out at about 36% with ErrNo 5: input/output error or something.  I eventually ran the 'check this image' option and it said there was an error with 2 files (on the usb flash drive).  It didn't say which 2 files.  I completely re-did the UNR image on the usb flash drive and same exact error.

SO, I used my regular desktop Ubuntu CD and booted to that (using an external USB DVD drive).  That installed fine.

BUT now I wanted to install the ubuntu-netbook-remix package to switch it over to UNR, and that worked, but it has these glitches that I didn't see in the live version (or the version on the Eee PC).  The menubar is black, and I can't see other applications that are open.  The documentation on how to upgrade from regular Ubuntu to UNR is out of date and incomplete - nothing about this problem: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)



> **dugh said:**
> Oh OK, I burned it to a regular USB flash drive instead, and that worked! 

Thanks for all your help!

---

### Post by dugh on 2009-04-30
> **Cyn Jade said:**
> Ouch!!  If you get an answer to this, please post, I am now going to hold off on jumping from XP to UNR on my AA1:  I use it for travel and the wireless capability is not an option.

At least with regular Ubuntu, wireless worked perfectly fine on my Acer Aspire One.  I just had menu glitches when I upgraded from regular Ubuntu to UNR (see above note).


Remember you can run UNR "live" off a CD or USB flash drive without installing it.  Wireless worked fine for me in live mode too.

---

### Post by dugh on 2009-04-30
I turned off visual effects under preferences->appearance and that took care of the graphics glitches but now I have both nautilus and UNR's interface showing up.  I just need to find out how to kill or hide nautilus.  I ran the command on the UNR wiki page (below) but no dice.

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

I found this hint that seemed to help make it look more like regular UNR:
"7) finally as the launchpad page says delete the bottom panel and set the top panel to 'GoHomeApplet|WindowPickerApplet|NotificationArea| Clock'"
(from [http://ubuntuforums.org/archive/index.php/t-908287.html](http://ubuntuforums.org/archive/index.php/t-908287.html) )

The machine froze at first when I shutdown, but after rebooting it seemed to work fine.  (Remember to right click on the top panel to move stuff around - you can use that to widen the top of the frame of applications)


> **dugh said:**
> I spoke a little too soon.  It worked (the live usb image booted), but then I ran the installer, and it choked out at about 36% with ErrNo 5: input/output error or something.  I eventually ran the 'check this image' option and it said there was an error with 2 files (on the usb flash drive).  It didn't say which 2 files.  I completely re-did the UNR image on the usb flash drive and same exact error.

SO, I used my regular desktop Ubuntu CD and booted to that (using an external USB DVD drive).  That installed fine.

BUT now I wanted to install the ubuntu-netbook-remix package to switch it over to UNR, and that worked, but it has these glitches that I didn't see in the live version (or the version on the Eee PC).  The menubar is black, and I can't see other applications that are open.  The documentation on how to upgrade from regular Ubuntu to UNR is out of date and incomplete - nothing about this problem: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by johnhenry on 2009-05-01
The thread at 

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=13627](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=13627)

in the Acer Aspire forum, seems to indicate that wifi does work OK in 9.04. I must try again. I had used the USB pen img. I must try with a proper CD version and a USB drive. All those contributing to the thread seem to have had no problems at all with wifi.

---

### Post by devinewind on 2009-05-01
I've installed the ubuntu 9.04 on Acer Aspire One. Everything is ok. Ever my card reader 5 in 1 cannot detect anything when i insert the sd card. Please help me!

---

### Post by johnhenry on 2009-05-02
My wife and I each have an Acer Aspire One, both bought within a week or so of each other from Amazon (UK). Both, of course, came with Linpus, but I immediately replaced this with identical dual-boot systems, XP and Ubuntu 8.10. Everything worked and, with these, still works fine. Wifi is recognised and configured quite automatically.

The other day though I decided to add a partition with Ubuntu 9.04. (Again, everything identical.) Here is where it gets interesting. On MY machine, the package installed perfectly easily, and everything works except WIRELESS. I have been quite unable to get the system to recognise the Atheros chip. On my wife's machine on the other hand, EVERYTHING, including wireless, installed effortlessly and worked immediately!

I can only assume that they have a different batch of Atheros wireless chips, and that one suits Ubuntu 9.04, and the other does not. I repeat that BOTH work perfectly with XP and Ubuntu 8.10!

---

### Post by johnhenry on 2009-05-03
A brief postscript to the above.

I decided to try restoring an fsarchiver image of my wife's setup of ubuntu 9.04 onto my own machine - hoping that the correct configuration might just get accepted and work. It merely needed to adjust the UUID in the fstab and grub files.

As I rather expected though, the result was that the restore worked, and everything EXCEPT wireless worked perfectly!

---

### Post by teh603 on 2009-05-03
> **johnhenry said:**
> 
The other day though I decided to add a partition with Ubuntu 9.04. (Again, everything identical.) Here is where it gets interesting. On MY machine, the package installed perfectly easily, and everything works except WIRELESS. I have been quite unable to get the system to recognise the Atheros chip. On my wife's machine on the other hand, EVERYTHING, including wireless, installed effortlessly and worked immediately!

I can only assume that they have a different batch of Atheros wireless chips, and that one suits Ubuntu 9.04, and the other does not. I repeat that BOTH work perfectly with XP and Ubuntu 8.10!
Its possible, although unlikely, that you got different models of AAO, even with similar system specs. There are a couple which have major wifi issues with Jaunty.

---

