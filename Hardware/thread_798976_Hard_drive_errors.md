---
title: "Hard drive errors"
date: 2008-05-18
forum: Hardware
---

### Post by notmatt on 2008-05-18
I've been having a few wierd errors over the past few days.  I think I've managed to track a few of them down (Firefox being
hideously slow and networking problems (my NIC an RTL8111 can be disabled quite easily it seems)) however the one I really can't figure out is the
seemingly hard drive related reboot yesterday.

I was using my system quite normally when it froze up.  When it all came back the filesystem was mounted read-only.  I had to reboot and run fsck to
get it all to come back.  My first thought was that I'd filled it up (I've done this before) but there was acres of space.  I've run a few
diagnostics commands, but I'm not quite sure what they mean and would like some help so I can find out what is happening.

I've attached the output of lspci and smartctl -a /dev/sda -d ata.  I also ran bonnie++ and I've attached the output from that.  Any of that mean anything?  I'm not really sure how to interpret it all.  There are some odd messages in/var/log/meesages, which aare attached.

---

### Post by notmatt on 2008-05-21
I've also run memtest overnight and it's shown no errors what so ever, so I can pretty much rule out ram.

---

### Post by Patb on 2008-05-21
Notmatt, you are not getting much response on this one.  A pity.  

Sorry but I'm a little confused.  Can you boot normally now?  Are the "weird errors" continuing?  If so, can you describe them?  Was the freeze just a one-off event?  

Sorry if I'm missing something.  

Cheers, Pat.

---

### Post by sdennie on 2008-05-21
Based on the data in smart.txt and tail.txt, it sounds like your disk may be dying.  Your disk is reporting reasonable values to smartctl but, it then starts to say that basic checks are generating errors.  That, accompanied with the errors in tail.txt (dmesg) make me think it's a disk problem.  The disk says it's been turned on for 5658 hours (235 days) which seems like a VERY short time for a disk to die in (especially when basic diagnostics from smartctl say the disk looks fine) but, it's impossible to tell how old the machine is so, maybe it's just dying of basic mechanical failure from old age.

---

### Post by notmatt on 2008-05-22
Thanks for the analysis guys.

The errors were basically the system being very slow and unresponsive, programs wouldn't start, even if they did they weren't usable.  It boots fine now after the very odd reboot and mounting the filesystem read only.  I think a lot of the system slowness was to do with Firefox 3 as I've switched back to Firefox 2 and it all works much better now.  Also I've stopped using the System monitor as that causes xorg to thrash the cpu.

---

### Post by sdennie on 2008-05-22
Bringing up the system monitor is dreadful on Hardy (see [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851) and look for High CPU usage in system monitor).  It looks nice but my guess is that every time it's run, Heisenberg rolls in his grave.

---

