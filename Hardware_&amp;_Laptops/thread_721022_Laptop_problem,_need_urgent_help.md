---
title: "Laptop problem, need urgent help"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by locosmurf on 2008-03-10
My friend has an HP Pavilion zd8000 laptop that was dualbooting with XP and Kubuntu Gutsy.
over spring break his laptop "screwed up bad" as he put it. heres a description as to whats going on.... I found this on a forum but to get the answer you need to pay for premium service which is not only impossible for me right now, but i view it as ethically wrong. anwho on to the problem!!!


Looking in the BIOS, I found that the boot sequence is as follows; Floppy drive (of which there is none on this comp), CD-Rom, HDD, Network. ---
Have tried numerous ways to try and test this to determine, exactly what the problem is so that we can fix the problem, all of which to this point haven't worked.
These tests have included -- Pulling and re-seating the HDD. Trying to boot a live CD (several distros). Disabling CD-ROM and Network Boot in BIOS. (When disabling network boot PXE error goes away but instead reverts to a blinking cursor line.) Resetting CMOS. 
CD-Rom drive will show initial power light , then no activity.
BIOS is also extremely limited, but not sure if this is inherent to this laptop or if new issue.

System Details:
HP zd8000
system board ID 3082
Pentium 4 3GHz
512MB RAM
BIOS Version F.32
KBC Version 36.31
OS - XP home, kubuntu gutsy

BIOS accessories for HDD is limited to a Hard Drive Self Test, which when ran does not detect IDE (it also lists Estimated Test Time as Diagnostics Not Supported).

please lend your expertise to this problem its urgent that we discover how to fix this laptop if possible.

I have scourged the forums and the net to no avail. ive tried everything ive read and cant think of anything. I was wondering if the motherboard is fried as i cant boot from cd. just a thought I had.

---

### Post by LieToPurify3 on 2008-03-11
I'm not sure I understand the problem.  What exactly went wrong with the laptop?  I see you're looking and fiddling with the BIOS to see if that will change anything, but I'm not sure what went wrong that you're trying to change.

---

### Post by locosmurf on 2008-03-11
the HDD isnt found. when I boot it I get the PXE-E61: media test failure, check cable followed by the PXE-ROM: exiting pxe rom. its as if the HDD doesnt exist.

---

### Post by 4l13n666 on 2008-03-11
Is your HDD damaged?

Also, you said that you have tried several distibutions, i trust you know the correct way to burn the DVD?

---

### Post by locosmurf on 2008-03-11
its not damaged in any way, it doesn't look burned or anything. its just acting that way.

and yes I do know how to burn iso images I've tested all the disks on my laptop before using them on his to make sure they worked and they do.

---

### Post by 4l13n666 on 2008-03-12
Alright so there are no problems with the CD's so we got that out of the way.

Some things that you might want to check out is the cables from your HDD. Are they properly connected and undamaged? 

You may also want to try to disable all boot drives except your DVD reader/writer.

You can also check if you are able to run any other startup disks such as a Windows XP installation CD. If you are able to get the installation module started using your Windows CD, then there might be a problem with the DVD reader or the CD's. There should't be a problem with the CD's since you were able to run them on your other machine.

---

### Post by locosmurf on 2008-03-12
the cables do not appear to be damaged in any way and they are all connected properly.

disabling all but the DVD drive leaves me with it reverting to the aforementioned blinking cursor line.

neither of us currently have a Windows XP nstallation CD or I would test that.

EDIT: I tested the Windows XP Installation CD and its a no go. If there is any possible way to test this further please let me know soon because in a few days we are going to have to scrap the project and just buy a new laptop.

EDIT 2: I still have the laptop in my possession so the project isn't dead, just not urgent  anymore.

---

