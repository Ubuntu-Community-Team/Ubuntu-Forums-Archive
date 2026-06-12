---
title: "Canon LiDE 600F Scanner in 6.10 Edgy"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by kacheng on 2006-11-21
Does anyone have insight on setting up the Canon LiDE 600F scanner in Edgy?

I've install sane-utils and Xsane, and played with some various configuration files, but the scanner is not identified.

What other steps are required?  
(I believe that some of the various sane dll.conf tweaks in 5.10 and 6.06 are no longer required.  Is this the case?)

Thanks.

---

### Post by red_Marvin on 2006-11-21
This fix is not specific for your scanner, but I've got the impression that it's a common problem, not brand specific...
[http://www.ubuntuforums.org/showthread.php?t=95442](http://www.ubuntuforums.org/showthread.php?t=95442)

---

### Post by kacheng on 2006-11-22
Is any one involved in working on the sane project's genesys backend?

How can I contribute help/testing for the LiDE 600F?

---

### Post by originaluoc on 2006-11-23
Because I have exactly the same problem, does anyone recommends another scanner compatible to Ubuntu with similar characteristics of that of LiDe 600F, whatever the producer is? As I have read to another topic many of you, use HP, but unfortunately I dont trust them so much. In Addition, my main emphasis is to scan texts and just a fine quality with photos, and to be portable, in other words not heavy, to carry it to a library. A weight like that of LiDE 600f looks fine.

---

### Post by kacheng on 2006-11-23
Unfortunately, I believe Canon's imaging products (cameras, scanners, printers) are the best value around.  Excellent quality, reasonable price, and reliable.

The fact that they don't support Linux drivers is a major downfall.

---

### Post by kacheng on 2006-11-23
Has anyone tried using a scanner in a Virtual Windows Machine?

---

### Post by gjtoth on 2006-11-27
Actually, the problem is not specific to any one brand or model.  I discovered a "work around" here in the forums but I'll be darned if I can find the real solution to the problem.

To get your scanner working in Xsane, hit Alt-F2 and type "gksu xsane".  You'll get a warning telling you how dangerous it is to run the scanner as root and that your eyes will fall out (just kidding) but, your scanner WILL work.  I've tried it on Epson, Canon and HP scanners.  Finds 'em all.

---

### Post by amanita on 2006-11-27
My CanoScan 4200F is not detected when "gksu xsane", and I have also tired VM player with windowz with no result the best thing would be to get rid of this crap.

---

### Post by originaluoc on 2006-12-11
[Here]("http://www.zepan.org/index.php/2006/01/29/the-canon-lide-60-and-ubuntu-dapper/") there is a guide for installing Canon Lide 60 to Drapper. My question is twofold:

- does anybody know if this driver would be compatible for an Edgy version ?

- would this driver work with canon lide 70?

I have been compromised with the idea tha my Canon Lide 600f would not work under Linux, so I will sell it. Because the Lide series is what exactly I want, I would prefer to take the 70 to the 60. On the other hand, as soon as I am not interesting so much for scanning high-quality photos but rather to scan books and articles, I was wondering if there is a real difference in the quality between the 60 and the 70 model. 

Cheers.

---

### Post by Dafydd on 2006-12-22
> **originaluoc said:**
> [Here]("http://www.zepan.org/index.php/2006/01/29/the-canon-lide-60-and-ubuntu-dapper/") there is a guide for installing Canon Lide 60 to Drapper. My question is twofold:

- does anybody know if this driver would be compatible for an Edgy version ?

- would this driver work with canon lide 70?

I've just tried the above guide (adapting where applicable to the Canoscan Lide 70 - ie. replacing with the code 2255). 

Unfortunately, this doesn't work. Works fine with my girlfriend's XP!

Anyone have any ideas?

Dafydd

---

### Post by lptr on 2007-02-09
Tried Canon LiDE 600F here on this Edgy install:

```
> dmesg
...
[17206321.156000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[17206321.300000] usb 5-6: configuration #1 chosen from 1 choice
```

```
> sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2224 [CanoScan]) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

```
> scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

Tried the workaround running xsane under root (xsu). It tells me same: No scanner found.

Very valueable scanner but only working under W :mad: 

rob*

---

### Post by luke411 on 2007-02-21
This will seem strange but I know it works. I just don't know why it's not working for me now.

I originally had Ubuntu installed as a dual boot on a windows desktop, installed with it's own hard drive. The LIDE 60 is what is hooked up to the desktop and when I installed XSane it just worked.

Now I have Ubuntu installed on a laptop and I can't get it to work no matter what I do. It's simply not recognized. I'm wondering if it might be a difference between installing Ubuntu with it already connected, ie. a kernel module issue and trying to use it on a computer that already has Ubuntu on it.

I recall that the only issue I had with it when it was hooked up to the Desktop was that it would not do multiple PDF's on one file and only performed single page scans. Otherwise it would freeze up. 

I don't know the answer, I know I didn't do anything on the desktop installation except install Ubuntu and run it. I no longer have the desktop setup, as I used the hard drive for another Ubuntu box after I installed it on my laptop.

---

### Post by luke411 on 2007-02-21
I just found this on the internet and it makes sense. This is the exact behavior I got out of the scanner when I tried to scan multiple pages. This may not be a good scanner to use with linux if true, but it describes my experience to a tee and I have to believe it is probably accurate.

THIS BUG MAY PERMANENTLY DAMAGE HARDWARE.

This bug pertains to CVS HEAD 'sane-backends' as of this bug's opening date.  File revisions and system info listed
below.

When using the genesys driver to connect to Canon CanoScan LiDE 60, the scan head occasionally sticks and belt/motor
continue to exhibit 'grinding' noise until scanner is unplugged.  Otherwise, scanning performs normally in various
modes/resolutions.

As an example, when performing 75 DPI Lineart Letter page scans, the scan head sometimes sticks immediately after attempting
return/recall (~10% scans).  The motor/belt exhibit a 'clunk' or 'click' behavior upon changing directions that is not
so loud, but much more distinct than previous versions of this driver or vendor drivers (~75% scans).

After scan head sticking at the page end, and unplug is required to prevent physical damage, the scanner is unresponsive
to SANE.  Power reset does not help.  (Scanner shows on USB but won't operate).  Connecting to Mac OS X with vendor
drivers resurrects the scanner.

Mac OS X vendor drivers do not exhibit this behavior.
sane-backends 1.0.17 release does not exhibit this behavior.

# sane-find-scanner | grep 'found USB'
found USB scanner (vendor=0x04a9 [Canon], product=0x221c [CanoScan], chip=GL841) at libusb:001:024

# gcc --version | grep GCC
gcc (GCC) 3.4.5 (Gentoo 3.4.5-r1, ssp-3.4.5-1.0, pie-8.7.9)

# uname -a
Linux barnabas 2.6.16-gentoo-r2barn8 #7 Sat Apr 15 18:37:12 EDT 2006 ppc 7447/7457, altivec supported GNU/Linux

# cvs status genesys*.[ch] | pcregrep 'File:|Working rev'
File: genesys.c         Status: Up-to-date
   Working revision:    1.9
File: genesys_conv.c    Status: Up-to-date
   Working revision:    1.3
File: genesys_conv_hlp.c        Status: Up-to-date
   Working revision:    1.3
File: genesys_devices.c Status: Up-to-date
   Working revision:    1.4
File: genesys_gl646.c   Status: Up-to-date
   Working revision:    1.13
File: genesys_gl841.c   Status: Up-to-date
   Working revision:    1.6
File: genesys.h         Status: Up-to-date
   Working revision:    1.2
File: genesys_low.h     Status: Up-to-date
   Working revision:    1.4

---

### Post by greg.johnson on 2007-03-18
The Canon 600f ((0x04a9/0x2224) does not appear to be supported, even in sane cvs. (see below).

Does anyone know what chipset is used in the 600F, or how to pull the scanner apart (non-destructibly :-)) to determine the chipset? I assume it would be a Genesys Logic ([www.genesyslogic.com](www.genesyslogic.com)) chip and required an adaptation of the genesys backend.

Thanks.


Background:

The Canon 600f  is marked as "unsupported" in the sane cvs head devices list ([http://www.sane-project.org/lists/sane-mfgs-cvs.html)](http://www.sane-project.org/lists/sane-mfgs-cvs.html)).

Part of the output from "$ sane-find-scanner -v -v" reports:

<trying to find out which USB chip is used>
    checking for GT-6801 ...
    this is not a GT-6801 (bcdUSB = 0x200)
    checking for GT-6816 ...
    this is not a GT-6816 (bDeviceClass = 255, bInterfaceClass = 255)
    checking for GT-8911 ...
    this is not a GT-8911 (check 1, bDeviceClass = 255, bInterfaceClass = 255)
    checking for MA-1017 ...
    this is not a MA-1017 (bDeviceClass = 255, bInterfaceClass = 255)
    checking for MA-1015 ...
    this is not a MA-1015 (bcdUSB = 0x200)
    checking for MA-1509 ...
    this is not a MA-1509 (bcdUSB = 0x200)
    checking for LM983[1,2,3] ...
    this is not a LM983x (bcdUSB = 0x200)
    checking for GL646 ...
    this is not a GL646 (bDeviceClass = 255, bInterfaceClass = 255)
    checking for GL646_HP ...
    this is not a GL646_HP (bcdUSB = 0x200)
    checking for GL660+GL646 ...
    this is not a GL660+GL646 (bDeviceClass = 255, bInterfaceClass = 255)
    checking for GL841 ...
    this is not a GL841 (bNumEndpoints = 2)
    checking for ICM532B ...
    this is not a ICM532B (check 2, bcdUSB = 0x200)
    checking for PV8630/LM9830 ...
    this is not a PV8630/LM9830 (bDeviceClass = 255)
    checking for M011 ...
    this is not a M011 (bcdUSB = 0x200)
    checking for RTS8822L-01H ...
    this is not a RTS8822L-01H (bDeviceClass = 255)
    checking for rts8858c ...
    this is not a rts8858c (bDeviceClass = 255)
    checking for SQ113 ...
    this is not a SQ113 (bDeviceClass = 255)
<Couldn't determine the type of the USB chip (result from sane-backends 1.0.18-cvs)>

found USB scanner (vendor=0x04a9 [Canon], product=0x2224 [CanoScan]) at libusb:002:005

---

### Post by .simon on 2007-03-18
Hi there,

For what it's worth (slightly off topic) I'm having the same problem with my canoscan LiDE 80

I'm going to give it a try with xp in vbox...

I'll post if I have any luck 

Cheers

Simon

---

### Post by greg.johnson on 2007-03-20
Ok, Canon say they're not allowed to say what chip is in the Canon Lide 600F because it's propretary driver info, so I've had to pull one apart.

(Canon are so un-coperative about anything 'nix that I'll be boycotting all Canon products in the future.)

Anyway, the controller chip is marked as:

Phillips
CP2155BE
SE3854.1      21
ZSG0633DY

Does anyone know what this is or have a data sheet?

I've attached photos as well.

---

### Post by lptr on 2007-03-20
> 
Phillips
CP2155BE
SE3854.1      21
ZSG0633DY

Does anyone know what this is or have a data sheet?


When looking at this CS it seems like a 8 or 16 Bit single chip mikroprocessor (uP). I fiddled around with SAB8031/51 (8 Bit) many years ago. In the beginning 8031 was a simple 48 pin package all the memory logic descretely grouped around. During the time the number of pins grew, RAM and ROM inclusiv logic has been taken on the chip, dedicated digital and analog interface lines included and so on. I would not wonder if this Philips device is something derived. Because this scanner is probably driven by a micro stepping motor, a single step motor control device must be included with it on chip. 

Firmware: The core logic will be some sort of a scheduler that controls and syncronizes different events doing calculations (some) and (mostly) data forwarding. Call it a small mini OS. Because of the uP high grade of integration it will be very difficult to guess what it does inside. So the only way would be to analyze the data flow on USB interface side during sending control sequences. Then the same with the resulting blocks of data comming back.

Canon does not give away infos because they would have to share not only the protocols but a lot of methods how they handle data on a computer. I assume this, because the onboard controller has only limited power. But the PCs uP is built for number crunshing. So they will have done huge of their logic inside the driver. I expect additionally, that they do use bought firmware blocks. Maybe methods that are patented, too. This will prevent giving things out.

So the only thing for us would be to look out for devices that ARE fully supported under Linux. I agree with your initial statement and will only buy Linux supported devices in future, too. Maybe Canon (and other manufacturers) will be rethinking their logic?


rob*

---

### Post by greg.johnson on 2007-03-22
thanks for that rob. 
i can see now that most of the 600F functionality is in the windows driver and doing a sane driver from scratch with no docos is not practical.
ok, off to buy an epson or brother - anyone need spare parts for a 600F :-)

---

### Post by kacheng on 2007-04-04
Since other Canon LIDE series scanners have some basic functionality in Sane, what would it take to get just basic functionality for the 600F?  Is the protocol completely different, or a derivative of the earlier LIDE series?
If anyone can provide a little direction on this, that would be great.

---

### Post by drummingpariah on 2007-05-10
Man, I wish I had looked through this before buying the lide 600f I just got.  Looks like I'll be headed back to return it tomorrow, though.  Too bad Canon is being so frustratingly uncooperative.  They could at least release limited-functionality closed drivers for us, so we could at least USE their hardware.

---

