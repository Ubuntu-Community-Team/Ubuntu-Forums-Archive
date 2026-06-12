---
title: "New SATA harddrive clicking"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by maltman on 2007-09-05
I have a new machine build. I installed Feisty on a single SATA harddrive. A Western Digital Caviar SE WD2000JS 200GB 7200 RPM SATA 3.0Gb/s to be exact. The installation went fine. However, now that I'm actually using the machine and doing some multitasking, I noticed that a clicking noise will occasionally emit from the harddrive. It's a single loud click, and then the system seems to stop responding. I can still move the mouse around, but the apps are unresponsive. But then several seconds later I'll hear that same loud click again and everything returns to normal. Once this starts happening it continues back and forth.

Now, I've read other messages on the forum about issues with SATA drives in laptops and power management issues in Ubuntu, but didn't know if there was any similar type issue in desktops. Or if you think it may actually be a hardware failure?

Please let me know your thoughts, or ways I can test the drive...some diagnostics software perhaps? Because it's extremely frustrating at best and completely unusable at worst.

Thanks!

---

### Post by svtfmook on 2007-09-05
i have 3 WD drives that some times one of them will click upon boot.  but if i tap on it once, it stops.  it in no way hinders my performance though (ie nothing freezes, etc)

---

### Post by dulbirakan on 2007-09-05
I do not know what it means to you but a clicking hard drive is a baad baaad omen to me....

It all began when the HD with my almost finished term paper started clicking... and then, there was no term paper, no nothing. 

I tell you brother; beware; take care. For it might be a hw failure.

And for the diagnostics use [UBCD]("http://www.ultimatebootcd.com/") it has every thing one needs.

---

### Post by maltman on 2007-09-05
Yeah, a clicking drive is not a happy drive...that's why I'm posting. :-?
I don't really have much data to lose since it's a fairly new install. But just sucks if I have to go through everything all over again with a new drive.
I just want to get to the bottom of it for certain. Is it definitely a bad drive? Is it possibly a configuration issue?
I'll run the diagnostics provided by Western Digital tonight and see if that says anything about it.
Is there anything within Ubuntu that I can run to check the discs and run diagnostics?

---

### Post by maltman on 2007-09-05
Poo-burger!
Well, I ran the bootable CD Data Lifeguard Diagnostics tool that I just downloaded from Western Digital.
I first just tried running the quick test, and it returned right away with the message "TEST COMPLETED WITH ELEMENT FAILURE DUE TO HANDLING" and an Error/Status code of 0008.
I looked that up, and it's bad juju. Says the solution is to replace the drive.
Not happy. :frown:
We'll see how good Western Digital is at honoring their warranties.

---

### Post by LT1Caprice57L on 2007-09-06
One word: Seagate.

Good luck w/ the HDD.

---

### Post by wieman01 on 2007-09-06
Solution posted here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

And here:

[http://ubuntuforums.org/showthread.php?t=536673]("http://ubuntuforums.org/showthread.php?t=536673")

No more hard disk "clicking".

---

### Post by maltman on 2007-09-06
> **wieman01 said:**
> Solution posted here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

And here:

[http://ubuntuforums.org/showthread.php?t=536673]("http://ubuntuforums.org/showthread.php?t=536673")

No more hard disk "clicking".

Right, but I think those are laptop specific solutions with how the power management is being configured for the drives.
Unfortunately, after running the diagnostics, I think the drive itself actually is bad.

---

### Post by vacman1 on 2007-09-06
Do you have another hd with different file system installed?  only reason i ask is b/c i once had the same problem after installing a FAT32 slave drive to a XP NTFS master... sounds crazy, but the Maxtor (FAT32) worked perfectly until I conncected it and booted the system... the first boot would not load the OS and after rebooting it starting clicking... needless to say after that the Maxtor was trashed (totally inaccessible, even with fdisk and partition magic) and XP booted.  Now when I hook the drive up to anything it sounds like someone is murdering it! lol :)

and yes i had them both configured (master-slave jumpers) properly.

---

### Post by dabl on 2007-09-06
I've had 4 Western Digital SATA drives running in my Linux system for a year.  They click, they clack, they hum, and they buzz.  I don't believe much in "interpretations" of hard drive noises.  You'll know if it breaks, and if it's not broken, then it's working.

Worry about your power supply!

 :lolflag:

---

### Post by notwen on 2007-09-06
Generally clicking is not a good thing to hear, but I would be concerned about the temporary freeze.  WD is generally good about replacing drives, but I myself have had bad luck w/ them, I have had good experience with their customer service and they have replaced any of my WD drives which have gone bad.  I tend to stick w/ Maxtor and/or Seagate.  Hope you get your HDD replaced. =]

---

