---
title: "BIOS erased while installing Karmic Koala on Asus Z92J"
date: 2009-11-07
forum: Hardware
---

### Post by iganchev on 2009-11-07
Hello to everyone

Here is a strange and hard problem I went in while trying to install Karmic Koala on a Asus Z92J laptop.

I was trying to install the GNU/Linux from a USB flash drive. I didn't setup the boot sequence in the BIOS but was hitting the 'escape' button to display the boot sequence menu. The firts attempt to install got stuck in the middle (at the regional settings) and I restarted the installation process and changed the USB drive (I had two usb drives that I've just prepared before the installation begins). So with the new USB drive I followed the same steps -- first I put the USB drive in the USB port. Then powered the laptop, then started hitting the escape button.

Then suddenly a dos-like screen appeared with three horizontal bars the first saying erasing BIOS, the second reinstalling BIOS, the third saying making verification. After it finished I restarted the computer and now there is nothing on the screen. There is only a brief check of the CD-ROM drive.

In the same day it happened on a friend of mine, also on a ASUS laptop but he got the reflex to pull-out the key and turn-off the computer. It was OK after and he continued the installation from a CD-ROM. It is worth saying that I've installed a dozen other laptops with the same USB drives the same day.

Any suggestions, ideas? Could I recover the BIOS the same way I erased it? Help needed. 

Keep in mind to be very careful if you install Linux from a USB drive on an Asus laptop -- if you see something similar to happen pull out the USB drive immediately and turn-off the computer.

Best,

Shtereff

---

### Post by ubersolid on 2009-11-07
> **iganchev said:**
> Hello to everyone

Here is a strange and hard problem I went in while trying to install Karmic Koala on a Asus Z92J laptop.

I was trying to install the GNU/Linux from a USB flash drive. I didn't setup the boot sequence in the BIOS but was hitting the 'escape' button to display the boot sequence menu. The firts attempt to install got stuck in the middle (at the regional settings) and I restarted the installation process and changed the USB drive (I had two usb drives that I've just prepared before the installation begins). So with the new USB drive I followed the same steps -- first I put the USB drive in the USB port. Then powered the laptop, then started hitting the escape button.

Then suddenly a dos-like screen appeared with three horizontal bars the first saying erasing BIOS, the second reinstalling BIOS, the third saying making verification. After it finished I restarted the computer and now there is nothing on the screen. There is only a brief check of the CD-ROM drive.

In the same day it happened on a friend of mine, also on a ASUS laptop but he got the reflex to pull-out the key and turn-off the computer. It was OK after and he continued the installation from a CD-ROM. It is worth saying that I've installed a dozen other laptops with the same USB drives the same day.

Any suggestions, ideas? Could I recover the BIOS the same way I erased it? Help needed. 

Keep in mind to be very careful if you install Linux from a USB drive on an Asus laptop -- if you see something similar to happen pull out the USB drive immediately and turn-off the computer.

Best,

Shtereff

pics or it didn't happen. :lolflag:
I really do not believe that Karmic comes with an automatic bios upgrade for a specific brand of laptops. I'd check that usb drive of yours for any bios updates you have left behind when using that drive to flash the bios in the past.

---

### Post by iganchev on 2009-11-07
> **ubersolid said:**
> pics or it didn't happen. :lolflag:
I really do not believe that Karmic comes with an automatic bios upgrade for a specific brand of laptops. I'd check that usb drive of yours for any bios updates you have left behind when using that drive to flash the bios in the past.

Heya, and thanks for the answer.

Well, I never used the usb sticks for a BIOS update. More of it -- I messed-up the machine with one of them, and the same thing happened with my friend with the other key on different machine (except that he got better reflexes knowing what's about). I thing that the BIOS of the Asus laptop is confounding some file as a BIOS update or something.

Cheers

---

### Post by mdshann on 2009-11-07
Asus desktop boards usually have 2 BIOS's installed so that if you have a bad flash if you restart a few times or take the CMOS battery out it will revert to the old one from the second ROM chip. I don't know if this is built into their laptops or not but it may be a good idea to check the manual or call Asus. If the laptop is under warranty you may be able to get a new board. Generally the Asus flash utility can only be started by pressing the appropriate key of the F1-F12 variety. It is quite possible that there is some sort of bug when booting from a flash drive that is certain files / file names are present it will activate the flash but in the dozens of Asus boards I have flashed (and TONS of non Asus ones) I have never had a bad flash. I also use a USB drive to boot diagnostics utilities and have never had this happen. Being that this has happened to you and someone else you know you may be able to get it solved through Asus as it may be a bug. When you turn it on all you get is a black screen? It never POSTs?

---

### Post by iganchev on 2009-11-07
> **mdshann said:**
> ... When you turn it on all you get is a black screen? It never POSTs?

Yup, no POST at all. Actually as I said in an earlier post the CD was blinking when powering on the PC. So I started reading a bit on the net and it seems that the AMI BIOSes have something like a boot block that is never erased and that in case of bad BIOS checksum it is trying to recover the BIOS from floppy/CDROM.
Instructions available here: [http://www.garena.com/forum/viewthread.php?tid=401982](http://www.garena.com/forum/viewthread.php?tid=401982) and on couple of other sites.

The first method was unsuccessful because because of the bad BIOS I see nothing on the screen and it seems that there is some kind of interaction -- it is said "*follow instructions on the screen*". Otherwise it seems that there is something booting from the CD-ROM and it is giving me some hope.

I am currectly trying the second method.

If any other ideas please give it. If anyone wants to sacrifice his BIOS and tell me what are the instructions when loading the AMIBOOT.ROM, please welcome ):P

Cheers

---

### Post by iganchev on 2009-11-07
Ok the second method didn't work neither. I created a bootable DOS CD-ROM and tried to re-write the BIOS with it as described in the second method in [this link]("http://www.garena.com/forum/viewthread.php?tid=401982"), but with no success.

Any ideas would be appreciated.

Of some concrete help would be if someone could tell me what is on the screen when booting from a CD-RROM with a AMIBOOT.ROM file on it. If the flash procedure don't start automaticaly try hitting Ctrl+Home while booting. Please be sure to know what you're doing -- it is a potentially harmful operation.

Will continue tomorrow.

'night

---

### Post by iganchev on 2009-11-08
I think I need the original BIOS. Instructions on different sites say that the only thing that should be done to recover an AMI BIOS is to name a BIOS file AMIBOOT.ROM and put it on a floppy and boot on it using Ctrl+Home.

In my case I downloaded the latest BIOSes from the Asus support site and burned them on CD-ROM and then booted the machine. The CD LED starts to blink and the CD to turn. After about 15 seconds the LED stops blibking and after about 40 sec the CD stops turning. The CD makes some noise as if it is reading from the disk. If I put a CD with something else the behavior is slightly different.

So I suppose that the AMIBOOT.ROM is recognized but there should be incompatibility with the BIOS version I try to install.

Is there someone that has an Asus Z92J and a recovery  CDs near by. I would need the original BIOS for the laptop.

Thanks,

Shtereff

---

### Post by mdshann on 2009-11-11
From reading the first link in your post it sounds like you need to download the BIOS file from Asus, unzip it if it is in a zip file, and rename AMIBOOT.ROM uppercase letters is probably important here. Did the floppy drive light blink when you attempted this? If so you need to let the computer sit there for 5 minutes or so as flashing a BIOS takes a few minutes. Eventually you should here 4 beeps. At this point it is time to take out the floppy and reboot. Pressing Ctrl-Home is to force an update and is only needed if the floppy drive does not start flashing when the computer starts indicating it is reading from it. Judging from the fact that you have a laptop a USB floppy may work. I noticed you said the CD drive light lit up so it may also work to put the AMIBOOT.ROM file on a CD if the floppy doesn't do it.

---

### Post by mdshann on 2009-11-11
I was looking on Asus's site for the manual for your laptop and do not see Z92J listed anywhere?!

NVM I Found it it is listed under Z9200 series.

Of the 9 manuals listed none are in English!?!

---

### Post by iganchev on 2009-11-11
Hey there,

and thank you for the answer. I followed the procedure as described on different sites in order to update the AMI BIOS of the machine thought without success. The computer don't have a floppy, only a CD-ROM. When I insert a CD with a AMIBOOT.ROM file it starts reading the CD and stops after about 30 seconds. After nothing happens for more than 15 minutes. That's why I think that maybe the original BIOS is needed.

Indeed the two BIOSes with which I tried were from the asus site. I read some french and looked in the french documentation but no word about troubles with the BIOS.

Any ideas? Thanks again for your answer.

Shtereff

---

