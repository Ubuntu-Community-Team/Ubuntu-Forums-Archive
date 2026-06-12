---
title: "OH SHNAP CD/DVD drive stopped working on HP Laptop"
date: 2009-02-20
forum: Hardware
---

### Post by J-Morris on 2009-02-20
The CD/DVD drive in my HP Laptop has disappeared. When I put a disk in, the amber LED comes on, and the drive spins up, but ubuntu does not mount the disk, or even register that it exists. I can't even boot off a live CD! OH noes! I'm comfortable with the command line, but my only great accomplishment was getting my wireless working, so just assume I don't know anything, 

Plese hlep!:popcorn:Tanks!

---

### Post by sancho panza on 2009-02-20
Help us to help you. Always provide more detailed info about the circumstances of the problem. In this case, please tell us:

Do you have this problem when you are trying to boot off of the Live CD, or does it happen even when you are accessing the cd drive via WinXP/OS?
Have you tried if it reads other discs correctly?
Do you have any other bootable disc (say WinXP install cd or such)?
Was the drive working fine before? Was it working in Ubuntu or Windows?

Answers to these questions might help us a lot in understanding where the problem lies.
Cheers!

---

### Post by J-Morris on 2009-02-23
Ok, the drive used to work in ubuntu. It is possible I disabled it somehow, but the only thing that I did was to install the libraries to read DVD menus, and my friend used my laptop to play mp3s off a usb drive and didn't do anything use use amarok. It is difficult that these unrelated things would somehow disable 

The drive does not read any type of disc at any time. There is a /cdrom0/ folder in my /media/ directory, but even with a disc in, there is nothing. The drive spins up and the light blinks with nothing to show for it. The BIOS doesn't seem to see the drive, but I'm not sure how to properly check. 


Thanks for your help!

---

### Post by sancho panza on 2009-02-23
Do you have any other operating system on the laptop with which to test if the CD drive works? 
When the computer boots up, try and enter the BIOS to confirm if it sees the drive.
If the BIOS sees the drive, set the system to try and boot first from it using some bootable disk, to make sure the hardware works ok. If you cannot boot any bootable disk off the CD drive, then its likely to be hardware issue. Else its an OS issue. 

Hope this helps, Cheers!

---

