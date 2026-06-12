---
title: "WD My Passport hardware encryption"
date: 2009-10-07
forum: Hardware
---

### Post by Aperculum on 2009-10-07
So the new Western-Digital My Passport external harddrives came out and they come with builtin hardware encryption and I was wondering, does it work in Ubuntu? Is there a way to make it work in Ubuntu? Also what kind of drivers does it require on every computer I want to plug it in to view the encrypted files?

Thanks a lot in advance! :)

---

### Post by MauledByJesus on 2009-10-09
First of all, let me say that WD tech support knows painfully little about their own products. -_-

On a more relevant note, supposedly, the drive mounts a utility partition when you plug it in. That partition contains the encryption interface, so no software need be installed on the workstation.

There are PC and Mac versions so that implies that using them on Linux with full functionality probably won't be possible. Out of the box, neither of them work with the OS they weren't designed for (presumably because the encryption software would be a .app on an HFS partition for the Mac version and a Win32 app on the Windows version.)

 I've heard talk of being able to reformat drive so it can be used with other OSs, but then you completely lose the ability to encrypt/decrypt.

I've ordered one for testing and it should arrive next week:
[http://www.westerndigital.com/en/products/Products.asp?DriveID=722](http://www.westerndigital.com/en/products/Products.asp?DriveID=722) (WDBABM0010BBK)

I'll try to get back here to give some details after I've toyed with it a bit.

---

### Post by drkages on 2010-02-12
I came across the thread while looking for help in the similar topic of getting Hardware encryption to work on Ubuntu.

Really would like to maintain the Hardware encryption while remove my dependence on MS

There wondering what were the results of your experiment, and if others have had success in "hardware" encryption in ubuntu.

note I am aware that there are open-source software encryption tools but Wondering if hardware has been achieved.

---

### Post by gdi2k on 2010-03-07
I'm interested in this too. I have a WD Passport Elite (gotta love the names on these things ;-) ). It supports Full Disk Encryption (FDE). This is embedded in the hard disk itself, and can be activated / deactivated through special software, which works only on Windows and Mac from what I understand. 

Once encryption is activated, the drive is not accessible at all using Linux - not even fdisk can access anything. Once deactivated in Windows, it just acts like a normal external USB hard disk. There is no reformatting or anything like that required between en/disabling encryption - it just works with all data intact. 

This wikipedia article makes it sound like these things are based on standards and aren't vendor specific implementations: 
[http://en.wikipedia.org/wiki/Hardware-based_full_disk_encryption](http://en.wikipedia.org/wiki/Hardware-based_full_disk_encryption) 

My ThinkPad X200's Hitachi drive also has FDE, but is controllable from the BIOS which is transparent to the OS (works just fine in Linux). I may try putting the WD Passport's disk into the ThinkPad to see if it can be manipulated from the BIOS too - that would tell us if these things really are standardised I suppose. 

I haven't been able to find any software with which to manipulate hardware FDE in Linux yet.

---

### Post by vijayshankar on 2010-04-12
I am able to use the password locked drives in Ubuntu. Here is how I do it.
1) connect harddrive to Ubuntu Laptop
2) Run a windows XP virtual machine using vmware player
3) In vmware player menu, connect the WD my passport essential drive to to windows XP
4) In XP vm, it shows unlock dialog. Enter password, then the encrypted drive appears inside the XP virtual machine My Computer.
5) Using vmware player menu, disconnect the drive from XP. 
After step 5, the drive automatically mounts in Ubuntu and I am able to read and write to that drive.

This means unlocking (authenticating the drive with correct password) is one time activity. Once done it works with read and write until the drive is powered down. If someone can reverse engineer the unlock.exe that comes with the drive and write equavalent utility or write a wrapper around unlock.exe then we can use it in Linux.

---

### Post by Lanser on 2010-04-12
Aperculum. My suggestion is to format your ext drives and forget about the WD freeware.

Then install TrueCrypt and use it instead to encrypt your drives. Very easy to use and setup.  You can then install the windows version of truecrypt in your windows instances to access your encrypted drive from either OS.   This also works for USB keys or any flash media.   enjoy....

---

### Post by gdi2k on 2010-04-12
Thanks Lanser, I agree that TrueCrypt is handy for putting encrypted containers on external disks or even encrypting an entire external disk, but FDE offers a whole lot more. 

Using software-based encryption comes with a large performance penalty that hardware-based FDE does away with. I've run fully encrypted (root) Ubuntu installs for years, and it's torture in terms of performance. It's not so much the slower IO performance that annoys, it's the massive CPU hit that any IO operations cause, slowing everything else down (laggy desktop during copy operations etc). 

And if you ever exhaust RAM and started swapping with software encryption, it's reboot time. 

Phoronix does benchmarks (for Home Encryption), but they don't tell the whole story as they don't touch on overall system responsiveness or CPU load during IO operations. 
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1)

Aside from that, I would love to be able to use the encryption silicon I've paid for as part of the disk! :-)

---

### Post by ihristov on 2010-05-12
From what I am reading on the WD web site and the Trusted Computing Group web site these WD drives do not conform to the opal SSC specification.

As far as I can tell the only ones so far that do implement the spec are some models from Seagate, Hitachi and Samsung.

---

### Post by dE_logics on 2010-05-12
> Using software-based encryption comes with a large performance penalty that hardware-based FDE does away with.

Unless you're running hardware which's 5+ years old and using like... 512 bit encryption.

Use 64 bit encryption but even with 128 bit, it wont make much difference (performance). Of course I don't know about running the whole OS in an encrypted partition.

---

### Post by gdi2k on 2010-05-15
ihristov: Thanks for the info, looks like WD doesn't follow standards in lots of ways: 

I pried open the casing on my Passport Elite; they've integrated the SATA -> USB conversion circuitry straight into the drive's board, so it has no SATA connections at all. Instead it has a ribbon cable connector which connects to a bunch of LEDs on the side of the casing to indicate disk usage in Windows - doesn't work in Linux. It also has a two-pin connector to the right of the USB - no idea what this may be for. 

This also explains how they're able to make it so small - no separate SATA -> USB board required. 

So this particular drive looks like a complete non-starter in terms of Linux FDE support. Shame. Hopefully standards compliant support will follow at some stage!

---

### Post by legendbb on 2012-07-03
I just got 1T my passport and found out it doesn't work on uBuntu.

Theoretically I can understand to have virtual windows to get "WD Drive Unlock.exe" to work at least once so the encryption is unlocked. But still prefer to have more convenient ways of doing this.

I've tried to lunch "WD Driver Unlock.exe" bye wine (1.2.2), Error: " The application has encountered an unexpected error and is now exiting."

Almost two years have passed since the opening of the thread, hoping to have better solution. Personally I am now using another unencrypted USB 3.0 thumb driver as transit.

---

### Post by CorleyKinnane on 2013-05-15
Just remember folks, just because you can't use a proprietary encryption method that supports hardware, it's not a big deal. The future for fast, trustworthy hardware encryption is in Intel CPUs. Make sure you load the hardware based AES 256 encryption module before using the device mapper with AES 256 encryption and you can use any drive, SATA, USB 3.0, SSDs with ultra fast encryption that has no middle man.

---

