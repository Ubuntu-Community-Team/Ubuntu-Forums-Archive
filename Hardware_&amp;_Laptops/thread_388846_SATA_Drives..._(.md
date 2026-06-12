---
title: "SATA Drives... :("
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by nick_karstedt on 2007-03-20
Have to love more problems!  After fixing the crazy mouse issue, I'm on to my next, installing the thing........  I go to select a partition and find that there are none!  Not only that, but there are no drives to create partitions!  Is there really no SATA support?  I have a well sized fat32 partition on it...

---

### Post by futz on 2007-03-20
> **nick_karstedt said:**
> Have to love more problems!  After fixing the crazy mouse issue, I'm on to my next, installing the thing........  I go to select a partition and find that there are none!  Not only that, but there are no drives to create partitions!  Is there really no SATA support?  I have a well sized fat32 partition on it...
As long as your drive controller is supported, SATA drives are no different than PATA drives to the operating system. I haven't found one that isn't supported yet, tho JMicron controllers had some troubles for the first while.

I have had some strange troubles with SATA drives not showing up in the installer when I didn't have AHCI enabled in the BIOS. Seems most BIOSes are defaulted to have SATA drives emulate IDE. You have to go in there and change that controller to AHCI mode.

If you have windows on the drive still, changing to AHCI after the install will cause some minor troubles. The cure is to build an F6 floppy with AHCI driver on it and do a repair install of windows. A repair install won't destroy any of your data or settings, so don't panic. But a decent backup is a VERY good idea anyway, just in case something goes sour or you make a mistake.

Glossary:
AHCI = Advanced Host Controller Interface. This is what makes SATA2 work. With it disabled you don't get all the cool new features of SATA2.

SATA = Serial ATA = the new way, with thin 7 wire cables.

PATA = Parallel ATA = IDE = the old way, with 40/80 wire ribbon cables.

---

### Post by nick_karstedt on 2007-03-20
Ah, I'll give it a go once I get back tonight, thanks ;)

---

### Post by nick_karstedt on 2007-03-20
I didn't see any way to change my controller type in the BIOS, but the controller is "silicon".  Any other suggestions?

---

### Post by futz on 2007-03-20
> **nick_karstedt said:**
> I didn't see any way to change my controller type in the BIOS, but the controller is "silicon".  Any other suggestions?
It's a Silicon Image controller then. Can you give me the mainboard make/model# so I can grab a manual and have a look.

---

### Post by nick_karstedt on 2007-03-20
It's an ASUS K8N4-E Deluxe.  I'm running through my manual at the moment..

---

### Post by futz on 2007-03-20
> **nick_karstedt said:**
> It's an ASUS K8N4-E Deluxe.  I'm running through my manual at the moment..
Ah, you have two SATA1 controllers on that board. The main one, which is the NForce4 and a secondary Silicon Image SATA1 controller. Each can control four SATA1 drives. Because they're SATA1 controllers they won't do AHCI, so never mind that (I was thinking you had a more modern board).

I would think if you have four or fewer SATA drives, you should plug them into the NForce4 controller and disable the SIL. That will make your bootup faster, as the SIL won't waste time looking for non-existent drives.

Look on pages 4-24 and 4-25 of the manual for setup info for the NForce SATA controller. It's pretty simple stuff, but if you need more detailed help, just yell.

---

### Post by nick_karstedt on 2007-03-20
hmm did what you said.  It helped my boot time by a few sec, but still, same result.  Another thing I noticed is that ubuntu is not detecting a lot of my hardware, including 2 lan cards and integrated audio :(  It hates my computer...

---

### Post by futz on 2007-03-20
> **nick_karstedt said:**
> hmm did what you said.  It helped my boot time by a few sec, but still, same result.  Another thing I noticed is that ubuntu is not detecting a lot of my hardware, including 2 lan cards and integrated audio :(  It hates my computer...
How many drives? In the BIOS, does the problem drive show up in the list under Main? You're trying to install, right? Which installer - text? or live disk graphic installer?

Some hardware can be tough to get working sometimes. I've had times when the text installer wouldn't work at all, but the graphic installer did, and vice versa.

---

### Post by nick_karstedt on 2007-03-21
I have only 1 drive in this machine, and it is showing up on the list.  I run windows on a seperate partition on the drive. (160 gig drive, half ntfs half fat32).  I am using the graphic installer.  I suppose I'll try the text installer next...

---

### Post by futz on 2007-03-21
Hmm... Try putting the drive on the Sil controller and see if the installer can detect that properly?

You may have to try some of the installer command-line options (which have all slipped my mind at the moment). All I can remember is -noapic, which most likely won't help...

Ah! Here are some of them in this thread
[http://ubuntuforums.org/showthread.php?t=378966](http://ubuntuforums.org/showthread.php?t=378966)

linux noapic
linux pci=irqroute
linux pci=noacpi
linux acpi=off
linux pci=acpi
linux nolapic
linux framebuffer=false
linux irqpoll

There are others. I've never used any of the above mentioned ones, but I have used others that I can't remember right now. Oh, I remember one I've used:
linux noprobe

---

### Post by nick_karstedt on 2007-03-21
Awesome, I'll give that a shot in a bit.  I'm trying the "wubi" beta (the windows installer).  Maybe since my windows os detects the drive (Obviously) it can get it installed and all will be happy!  Hah!  We'll see.  Need sleep first though..

---

### Post by futz on 2007-03-21
> **nick_karstedt said:**
> Need sleep first though..
Bah! Sleep when yer dead! :mrgreen:

---

### Post by nick_karstedt on 2007-03-21
Well I've used some of those commands for the graphic install, I just used ALL of them and it worked!  I knew it as soon as I heard the startup sound (Internet works too!).  The windows install was a bust, but this is FINALLY working now.

I love you :P

---

### Post by futz on 2007-03-21
Excellent! Glad I could help. :)

---

### Post by Gilgad Drumheller on 2007-04-02
I have the same problem, with the exact same motherboard.  Can you clairify?  Did you just append *all* of those commands to the boot options (f6)?  It seems like some of them conflict (ex. linux acpi=off linux pci=acpi)?
Or was it a specific command that did it?
I've tried each command individually, and they either did nothing, or prevented the cd from booting (though i didn't see that one, noprobe, down at the bottom, i'll have to try that).
Sheez, i had the mouse issue as well.  After this, i still have to get the network card working, as well as the sound card.  *sigh* Ubuntu isn't doing too well in the first impression department.
But then again, if i wanted a OS that i wasn't able to/didnt' have to touch, i'd be shelling out money for a Mac or something.

---

