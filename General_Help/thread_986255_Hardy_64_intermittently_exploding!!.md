---
title: "Hardy 64 intermittently exploding!!"
date: 2008-11-18
forum: General Help
---

### Post by cathuria on 2008-11-18
As a background to this trauma, I should tell you that a day ago, I had some faults come up on my period fsck on boot -- I did as it told me and ran it manually -- there was a bunch of stuff to 'fix' -- what did I know? I told it to fix everything...

Things went smoothly thereafter, although one of my Firefox bookmark directories was renamed (??).  But after this morning's update, things went sour fast.

First, OpenOffice refused to start, saying that the interface language could not be determined.  I thought perhaps the install was borked and thought about reinstalling or checking dependencies, so I started up Synaptics, which asked for my password and immediately shut down.  But a STOP sign (red circle, white dash) was showing in my norification bar.  Every time I click it, the Upgrade window shows very briefly and vanishes...

Tried to start Firefox to look up similar problems on this forum, and it wouldn't run -- got this in the terminal:

```
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 416: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!
```

I copy & pasted that just now but thought I wouldn't be able to -- 'cause then Nautilus refused to mount any other volume and then refused to start entirely.

After yet another reboot in this process, I can start both OO and Firefox normally (at least so far), but that darn Stop sign is still showing in my notification bar....

At the moment, I'm willing to ascribe all this to martian gremlins, for all the clues I have...
I'd appreciate some better clues -- thanks.

---

### Post by cariboo on 2008-11-18
Check Lost+Found to see if there are any important files in there. You can usually open the files iwth a test editor to see waht they are. You will have to be root to access Lost+Found so press Alt-F2 and type;

```
gksu nuatilus
```

It seems like some important files were corrupted.

Jim

---

### Post by cathuria on 2008-11-18
thanks -- but my lost+found directory is empty.

I've tried a couple reboots, and things happen differently each time.  Sometimes I am able to start OpenOffice, sometimes I get the same 'inconsistency' message. Sometimes I can open Synaptics/Update Manager, other times I cannot.

I am preparing myself mentally for a hard reinstall -- if anyone has any other ideas, I'd be grateful.  Hmm -- try Hardy 64 again, or go with Intrepid 32 and hope stuff works??

---

### Post by cathuria on 2008-11-18
Sorry -- additional information in case it is illuminating to anyone...

On my first reboot after my first post, when I logged on I got a dialogue box proclaiming "Your session lasted less than 10 seconds..." etc.
The details window showed errors for some sort of Invalid Param for every process Gnome tried to start.

...went back to recovery mode and ran dpkg, just in case, and then booted normally.  Well, except for things not working now & then... :(

---

### Post by cathuria on 2008-11-18
hmmm -- on a related note, during one of those sessions when I *can* start the Update Manager, would it be safe to reinstall/upgrade from there -- or am I better off using and installation iso?

---

