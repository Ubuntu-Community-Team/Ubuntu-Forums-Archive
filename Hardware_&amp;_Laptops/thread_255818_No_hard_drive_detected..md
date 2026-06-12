---
title: "No hard drive detected."
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by joemacnz on 2006-09-12
G'day all,
           I am having trouble installing 6.06. Basically I can't install it because it won't detect the SATA HD. I can see the HD on the BIOS but not on Ubuntu.I don't have any windows on the system and would like to keep it that way but I am not getting very far at the moment.
Mobo   :A8V-MX
HD     :Seagate Barracuda ST3160811AS

---

### Post by lazerradial2003 on 2006-09-12
Might be worth trying plugging your hard drive into a different SATA port on your motherboard, Some motherboards have two different SATA controllers and Ubuntu has problems with a few of them (in particular the Jmicron ones on a lot of the dual core boards which also handle the IDE)..Afraid i can't be more specific than that because i don't have much experiance of AMD boards.

---

### Post by Christopher Cook on 2006-09-13
Sort of random, but if you could get use of another computer's hard drive, put it in yours, and try it that way, you could see if it's the hard drive or motherboard.

---

### Post by joemacnz on 2006-09-13
The motherboard has four SATA ports 1-4. They seem to correspond to
3rd master IDE,3rd Slave IDE,4th Master IDE and 4th Slave respectivly. I think I have been able to format the disk with seagate diskwizard but I still can't find it on the ubuntu disk.

---

### Post by tommcd on 2006-09-13
I have a Seagate SATA1 drive in my other computer (Asrock 939 Dual SATA2) and ubuntu recognized that. In your BIOS is there an option to set the SATA ontrollers to IDE compatablilty mode, or something similar? If so try that and see if ubuntu installs.

---

### Post by joemacnz on 2006-09-13
I can't find any reference to SATA in the BIOS. Infact the BIOS seems remarkably unhelpfull.The disk that came with it only seems to allow the creation of various floppy disks.

---

### Post by pravuil on 2006-09-13
I'm not sure if this would work and I would like someone to test this theory out before you attempt this. [http://wiki.debian.org/DebianInstaller/SataAtapiHowto](http://wiki.debian.org/DebianInstaller/SataAtapiHowto) It's a workaround for Debian. Though I'm not sure if it will work for Ubuntu. Can someone confirm this?

Regardless, you should be able to install it. I have a SATA harddrive and I didn't have a problem with the install at all. Have you tested the integrity of the disk itself?

---

