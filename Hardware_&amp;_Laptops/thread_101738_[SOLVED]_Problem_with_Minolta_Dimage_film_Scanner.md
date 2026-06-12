---
title: "[SOLVED] Problem with Minolta Dimage film Scanner"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by CyberBob on 2005-12-10
Can't seem to get either Xsane or VueScan to "see" my film scanner.

Here are some particulars:

Ubuntu 5.10 on Compaq Presario laptop
Konica-Minolta DiMage DualScan IV (usb scanner)

Output from  sane-find-scanner & scanimage -L

```
root@Presario:/home/bob # sane-find-scanner -q

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found USB scanner (vendor=0x132b [KONICA MINOLTA], product=0x000a [DiMAGE Scan Dual4]) at libusb:001:006


root@Presario:/home/bob # scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

As a result, I have not been able to get any scanner software to "find" the hardware yet.  I would REALLY like to get this scanner working in Ubuntu - having to go back to a windows box to use the scanner would be intolerable.

Please help!

---

### Post by CyberBob on 2005-12-14
I just read this morning here:
 [https://wiki.ubuntu.com/UbuntuBelowZero/LightningTalks?highlight=%28usb%29%7C%28scanner%29]("https://wiki.ubuntu.com/UbuntuBelowZero/LightningTalks?highlight=%28usb%29%7C%28scanner%29") 

... that all of the hotplug mess will be thrown away in Dapper.

Do those of us having problems with usb scanners just have to wait for the Dapper release next year, or *is* there a way to make stuff work that "should just work" but doesn't right now?

---

### Post by teaker1s on 2005-12-14
have you looked here
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Minolta&model=&bus=any](http://www.sane-project.org/cgi-bin/driver.pl?manu=Minolta&model=&bus=any)
you may be able to alter the sane  .conf  file with your model number and it may work
but be aware you may get limited functions and be ready to pull the plug when you first try it if it doesn't work as expected.
thats the advice I got

---

### Post by CyberBob on 2005-12-14
Yes I have looked at the sane project page ... and as I'm sure you noticed as well my scanner model (Konica Minolta Scan Dual IV)is unsupported.

Nevertheless I tried just as you have suggested but to no avail.  VueScan is also mentioned as a possibility - I have tried that but it also cannot "see" the scanner. 

[Refer to the code section in my original post]

I think the problem may be with the permission settings of the usb devices and how they are handled with the hotplug system.  Also I should mention that I did notice that by turning the scanner off and then on again causes the usb device assignment to increment.

---

### Post by Jenske on 2006-05-12
I've "switched" from Breezy to Dapper last night, hoping that my problems with the Minolta Dual Scan II (AF 2820U) would be resolved, but ... alas](*,) . I can start Xsane (from sudo) and their seems to be some communication between Xsane and the scanner. If I click "preview" the scanner starts to move in and out the tray with my slides ---the scanner tray holds 4 slides--- but then it reports "error".
So two questions:
[LIST]
[*]How can I "reset" everything I've done in the scanner software and access-rights to the "Dapper-standard"? After which, of course, I'd like to reinstall the Avision-programs. Yes, Avision, since the Sane-project tells me this particular Dimage Scan is actually an Avision scanner.
[*]Does anyone have an idea how to actually make this slide scanner work? I really need to get it to work and not just scan one image ---something I once experienced before I started changing system settings--- but to actually be able to scan images 1 to 4 or, e.g. just image 3.
[/LIST]

I'm desperately seeking a solution, since I use my slide scanner a lot.

---

### Post by CyberBob on 2007-01-11
I'm bumping this thread up to see if anyone out there has had success in getting the Konica-Minolta DiMage DualScan IV film scanner to work with VueScan in Ubuntu.  I *know* it works in FC6 because a friend tried hers out and it worked on the first go.

I really don't want to install FC6 on my machine as I am so comfortable (otherwise) with Ubuntu 6.06 ... but I cannot seem to get this #$%&#%^*$ scanner to be recognized by scanning software.  IT IS displayed as a device in the Device Manager application, but VuewScan cannot find it for some reason.  ](*,) 

Please help if you have any experience with this scanner or related issues with usb devices.

Thanks,

Bob

---

### Post by Jenske on 2007-03-11
Hi Bob,
Unfortunately nobody seems to have the answer to this Dimage IV-and-Xsane-problem. I've used VueScan and this program _does_ work.

---

### Post by Jenske on 2007-05-04
In the meantime I've switched from Dapper to Feisty Fawn (7.04) and now even VueScan won't find my scanner any more. As I understand, this has to do with a major bug in libusb. Unfortunately nobody seems to bother. I'm thinking of switching back to Dapper Drake (6.06) as this version DOES find my scanner in VueScan.

---

### Post by Jenske on 2007-05-20
> **Jenske said:**
> Hi Bob,
Unfortunately nobody seems to have the answer to this Dimage IV-and-Xsane-problem. I've used VueScan and this program _does_ work.

I must correct this, as I've found out that VueScan DOES NOT work in Ubuntu Feisty Fawn (7.04).

---

### Post by Apostata on 2007-10-29
bump

---

### Post by CyberBob on 2007-12-14
From the "better late than never" department ...


Thanks to the help from MK_Hayes (Nikonians.org member) my Dimage ScanDual IV is working.

The fix?

1. Be sure that the scanner is turned on before launching VueScan

2. Download a fresh copy of VueScan ([http://www.hamrick.com]("http://www.hamrick.com")) into a new subdirectory (folder)

3. Launch VueScan as root (even though I added my normal user account to the scanner group I can only get the scanner to work with root privileges - Dapper 6.06)


Note: after upgrading to 7.04/7.10 normal user privileges will successfully launch VueScan

---

