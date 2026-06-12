---
title: "Install 9.04 on fresh HD"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by draco48 on 2009-10-19
I had Ubuntu 8.10 installed on my notebook with Windowes XP adn it worked fine. I wanted to take the pluge to Ubuntu alone so I formatted my HD.  I then  downloaded 9.04 and created an ISO disk. I am trying to install the OS on my notebook with theclean HD, but  I am unable to do that since system cannot detect the CD as a start up disk.
Question:  Is it possible to install Ubuntu 9.04 without any Windows? If so, can yo direct to SIMPLE instructions and what else do I need to get before I can do that.

Many Thanks,

draco48

---

### Post by Mark Phelps on 2009-10-21
You said you "created an ISO disk".  Does this mean you copied the ISO file to the CD?  If so, that's the problem.

You need to BURN the ISO to the disk, using a feature in your CD burning program that burns image files.  That will then create a bootable Ubuntu CD with lots of files on it, not an ISO file.

---

### Post by draco48 on 2009-10-23
I used a disk burning program and burned the downloaded file to a CD.  I actually used the "infra recorder" program that I downloaded.  I have the following folders showing on the CD
.disk
casper
dists
install
isolinux
pics
pool
preseed

PLUS THE FOLLOWING FILES:

autorun
md5sum
README.diskdefines
wubi


Please note that when I put the CD in my current machine that has Windows XP running, I immediately get the 'install" menu from the CD asking me to install the program.  I believe the program I downloaded is made to be run from and/or with Windows.  Of course if I knew for certain I would  not be asking some simple questions.

Any help??

Thanks

draco48

---

### Post by Cybie257 on 2009-10-23
> **draco48 said:**
> I had Ubuntu 8.10 installed on my notebook with Windowes XP adn it worked fine. I wanted to take the pluge to Ubuntu alone so I formatted my HD.  I then  downloaded 9.04 and created an ISO disk. I am trying to install the OS on my notebook with theclean HD, but  I am unable to do that since system cannot detect the CD as a start up disk.
Question:  Is it possible to install Ubuntu 9.04 without any Windows? If so, can yo direct to SIMPLE instructions and what else do I need to get before I can do that.

Many Thanks,

draco48

Not knowing what laptop you are using, most give you the option to select F12 during the BIOS POST screen and select a boot device. Otherwise, get into your BIOS and see if the CD-ROM is setup as a boot device and put it as the first boot device. This is the only thing(s) I can think of to help you out here. 

And, yes, you don't need windows to install Ubuntu. Linux is it's own OS and doesn't rely on Windows being present to install. 

-Cybie

---

### Post by draco48 on 2009-10-24
I have a Winbook notebook and it has run Ubuntu before as I mentioned in my first message.  The BIOS sends the system to the CD okay but then the message comes

NO BOOTABLE CD found in XXXX.

So the issue is that the software on the CD that I have somehow is not recognizable by the system or it does not contain the necessary files to make it  "BOOTABLE",

Question: how do I make the CD bootable so the system can recognize it. I probably have to reburn the image on a bootable CD disk;

How do I do that?  Hel

Thanks

draco48

---

### Post by Cybie257 on 2009-10-24
If you downloaded the ISO image and burned it, it should work just fine. I've never come across one that didn't, so I'm thinking maybe you burned it incorrectly????  Try burning another one, and I'd even suggest redownloading the image. As for a specific 'bootable' cd, no such thing. Your bios searches the root directory of a CD for specific files to boot from. if they aren't there, then it can't boot. Let me know if you need further assistance and I will see what else I can suggest. 

-Cybie

---

