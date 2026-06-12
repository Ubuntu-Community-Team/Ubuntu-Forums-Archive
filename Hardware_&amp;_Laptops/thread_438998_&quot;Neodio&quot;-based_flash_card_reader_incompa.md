---
title: "&quot;Neodio&quot;-based flash card reader incompatible?"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by Fraoch on 2007-05-10
Hello:

I have a flash card reader - it's a USB 2.0 external reader in a transparent case so I can see the chipset - a "NEODIO ND3260-LD".  Searching the forums for "NEODIO" it appears that some users have gotten this chipset working as it's listed in their lsusb outputs as a flash card reader:

> ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader

However I have now tried mine in two completely different motherboards with the same result - the power light comes on but in 10-15 seconds all the lights start flashing, indicating some sort of I/O error.  There are no cards inserted and it doesn't matter if there are.

This has also been the case for Breezy, Edgy and now Feisty.

It would seem I have an incompatible flash card reader and that's that, but the reports of "3260 Neodio" chipset flash card readers in other posts here indicate otherwise.

---

### Post by Fraoch on 2007-05-16
Bump?

Seeing those "ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader" entries in others' lsusb outputs is so frustrating!  It seems I'm close...?

---

### Post by teaker1s on 2007-05-16
firstly this page mentions it with debian on which ubuntu is based
[http://www.wayfinder.it/resources/inspiron8500.php]("http://www.wayfinder.it/resources/inspiron8500.php")

it would appear that your issue is that the drive doesn't automatically mount, but driver should be in  kernel you could try inserting a card into it and then in terminal
```
fdisk -l
```

can you see the card ?

you could then use the pmount command-for more info in terminal
```
man pmount
```

---

### Post by Fraoch on 2007-05-17
> **teaker1s said:**
> firstly this page mentions it with debian on which ubuntu is based
[http://www.wayfinder.it/resources/inspiron8500.php]("http://www.wayfinder.it/resources/inspiron8500.php")

it would appear that your issue is that the drive doesn't automatically mount, but driver should be in  kernel you could try inserting a card into it and then in terminal
```
fdisk -l
```

can you see the card ?

you could then use the pmount command-for more info in terminal
```
man pmount
```

Thanks.  Unfortunately it doesn't seem to be detected on a hardware level.  fdisk -l shows nothing but my hard drives, card plugged in or not.  I don't seem to have pmount installed but it seems the kernel doesn't have anything *to* mount.

To see if the reader was being detected, I used lsusb for USB devices and dmesg | tail for kernel messages (I think this is correct, the dmesg output is the same as kern.log).  Neither one showed a change, card inserted or not.  It just doesn't seem to detect there's any new USB device plugged in. 

Interestingly I don't get the all-lights-flashing-I/O-error when I use a different USB cable and my case front USB ports, but neither lsusb nor dmesg | tail show it's detected any new USB devices.

I seem to recall it worked once in a very old version of Ubuntu (prior to 6.06?).  I'll try one more thing - my scanner also doesn't work, see [http://ubuntuforums.org/showthread.php?p=2668777#post2668777](http://ubuntuforums.org/showthread.php?p=2668777#post2668777) so I'll be trying to boot to older kernels through GRUB and some live CDs.  I'll see if this device can be detected.

This leaves me in a difficult position because I need a card reader and if I replace this one I don't know if the new one will be detected either. :(

Oh and also - I have removed my avatar.  Sorry about that.

---

### Post by Fraoch on 2007-05-17
Unfortunately I booted into a Dapper live CD - the card reader wasn't detected.  I even had an old Warty live CD - nothing there either.  Interestingly as I was switching boot devices to boot off the live CDs, my motherboard BIOS recognized the reader (4 ports - SM, CF, SD and MS, the same as the physical ports) and would have allowed me to boot off it.

It looks like the sorry conclusion is my reader just isn't compatible.  Given that the Neodio ND3260 is recognized for other people, perhaps the version I have "ND3260-*LD*" is different than the ones recognized.  A quick check of the Neodio website, which gives very little information, does show photos of other chip variants: the ND3260-LA is pictured on their front page and inside.

[http://www.neodio.com.tw/](http://www.neodio.com.tw/)

They have a datasheet, [http://www.neodio.com.tw/spec/nd3260v1.1-cutomer.pdf](http://www.neodio.com.tw/spec/nd3260v1.1-cutomer.pdf) which indicates that the "LD" version contains "I19" firmware.  Other versions contain older firmwares, perhaps I am "lucky" to receive the newest one.  I suspect that perhaps kernel support was for older firmware versions.  There doesn't seem to be a way to downgrade the firmware - the spec is written right onto the chip, implying it's permanent.  There's a driver - Windows only, of course.

Does anyone have such a card reader that works?  What is the exact chip model?

---

### Post by Fraoch on 2007-05-17
I'm thinking of reporting this as a kernel bug, but that seems a little drastic and pretty intimidating for a novice like me.

I do know this device had no support in 2.4 kernels and that kernel support was added somewhere in 2.6 (don't know where or when, or how to find out.)  I strongly suspect the new firmware versions of the controller chip require different USB commands.  If anyone would post working chipset versions, I bet they are not "LD" versions.

The closest thing I can find on the web is this:

[http://software.frodo.looijaard.name/neodio/](http://software.frodo.looijaard.name/neodio/)

which indicates it doesn't work in 2.4 and provides a patch, and also indicates support was added in 2.6.

---

### Post by teaker1s on 2007-05-18
report as a bug, also no worries on avatar-several people saw mine and decided to use it as it's fun.
It may also be worth speaking to the person who created the patch-maybe something as simple as altering the hardware ID in patch would make it work

---

### Post by ka1axy on 2007-07-09
Edgy, upgraded to Feisty user here.  I have the (in)famous Neodio controller on two of my Ubuntu systems.  One is a 3 year old Dell Precision workstation at work, and the other is an older Supermicro P4SBA+ motherboard.

The Dell has worked all along.  The Supermicro has not worked.  I've tried pretty much everything I could think of, and the "lsusb", "lsscsi" outputs look pretty much the same.  I stick the card in and nothing happens.  The system sees the reader and sets up the scsi disks for the cards, but never does anything.

Well, today, I decided to try something different.  I pulled off the side of the box, and unplugged the connecting USB cable from the motherboard.  Those of you with externally mounted Neodio readers can just try unplugging your USB connector.  I waited 5 seconds or so, then replugged the reader.  When I inserted the CF card, I got the light to flicker and the icon appeared on my desktop.

---

### Post by ka1axy on 2007-07-10
(lsusb output for my card reader/writer)
Bus 002 Device 002: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
It's a very cheap, drive-bay mounted reader.  I can't remember the brand, but I got it from NewEgg for around $20. The one that worked all along, is an Iogear external "Universal Reader/Writer", also from NewEgg.  They both appear to use the same Neodio chip - the one in the Iogear is an "ND3266-GA".

"lsmod | grep usb" returns:

usb_storage            72256  0 
libusual               17936  1 usb_storage
usbcore               134280  5 usb_storage,quickcam,libusual,uhci_hcd
scsi_mod              142348  5 usb_storage,sg,sr_mod,sd_mod,libata


After a bit more testing, my reader seems to be working reliably.  I must have rebooted several times since I installed the reader, but maybe it required a power cycle, which I can't guarantee I have done since I upgraded from Edgy to Feisty.

(hey, Linux never crashes, so I don't need to reboot as much as I used to with Windows)

Since initially getting the reader to work,  I have rebooted my system and tried CF and MMC cards (the only ones I have available).  Both work fine and are detected and mounted automatically on the desktop.

If you haven't been able to get your Neodio-based card reader to work, and it's showing up in "lsusb" and "lsscsi", try powering the unit off and on again, and perhaps power-cycle the machine.  I can't explain it...maybe the power cycling triggers a reload of the driver or some firmware.  There was absolutely no response to a card insertion before the power cycle, and now I get a select light flashing next to the card socket as soon as a card is inserted.

Hope this helps someone else,
Peter

---

### Post by Fraoch on 2007-07-21
I tried this:

[http://ubuntuforums.org/showthread.php?t=485218&page=2](http://ubuntuforums.org/showthread.php?t=485218&page=2)

(the tifm script)

which despite being for TI-based card readers, did something - I can plug the reader in without the lights going haywire.

However still no go.  When I plug in a CF card, it's not recognized and the lights lock up in the error indication again after about 3 seconds.

I haven't tried power-cycling yet.  But I've tried so much stuff with this stupid POS I may just leave it in the drawer.

I didn't log a kernel bug because it seems so trivial, and the documentation required to submit a bug and have someone look into it is too daunting for a newbie.  Plus I still don't know if it's a kernel bug or not.

---

### Post by Fraoch on 2007-07-24
Well I kept trying.  My final findings are similar to ka1axy's - you have to go to great lengths to get it to work, but it does seem to finally work!

After the tifm script I knew I was close.  It turns out that something (the card or the OS?) likes to see several unsuccessful connection attempts before it will work.  So I just kept unplugging and replugging it - after 2-3 times it started to work consistently.

For some bizarre reason this was not true on all USB ports.  Some didn't work at all (I/O error light 3-5 seconds after connection every time).

So I can't say it's rock-solid, but it does seem to be working now.

---

### Post by Fraoch on 2007-08-01
Dangit, a couple of reboots later and it's giving me the "all lights flashing" error again.

Perhaps it needs to be on a certain USB port, or perhaps it needs to be recognized in a certain order on bootup?

Back in the drawer again.:mad:

---

### Post by pavlinux on 2008-06-12
> **Fraoch said:**
> 
I have a flash card reader "NEODIO ND3260-LD".  Searching the forums for "NEODIO" it appears that some users have gotten this chipset working as it's listed in their lsusb outputs as a flash card reader:


* In kernel 
    
            CONFIG_SCSI_MULTI_LUN=y

* In /etc/modprobe.conf

           options scsi_mod max_scsi_luns=8

* In /boot/grub/menu.lst or /etc/lilo.conf 

           max_scsi_luns=8

* In shell 

          echo 8 > /sys/module/scsi_mod/parameters/max_luns


Read this - [http://www.cs.sfu.ca/~ggbaker/personal/cf-linux](http://www.cs.sfu.ca/~ggbaker/personal/cf-linux)

---

