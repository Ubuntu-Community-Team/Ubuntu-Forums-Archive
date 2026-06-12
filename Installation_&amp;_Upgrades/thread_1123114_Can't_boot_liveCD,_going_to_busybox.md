---
title: "Can't boot liveCD, going to busybox"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by bomber991 on 2009-04-11
Well, when I try to boot the live cd it throws me into BusyBox.  I've read up to page 10 of this thread [http://ubuntuforums.org/showthread.php?t=765195&highlight=busybox](http://ubuntuforums.org/showthread.php?t=765195&highlight=busybox) and I just don't have the time to read the other 26 pages of it right now.

Anyways, these were the suggestions that I've tried already:
Change sata mode from achi to raid in bios - Didn't Work
Check CD for Defects - No defects, so problem still exists
Alternate Install CD - Couldn't detect / mount my cd drive during install so I dont know what to do
AMD64 version - Still went to the busybox screen

And here's suggest I'm going to try now:
pci=nomsi on alternate boot?
irqpoll on normal boot
all_generic_ide
all_generic_ide floppy=off irqpoll
nolapic acpi=off irqpoll 

Any other ideas on what to try?  I've installed ubuntu before a few years ago and it never gave me problems then.

Now here's my hardware:
Asus Motherboard... I'm not quite sure of the model so if it's important tell me and I'll figure it out.
AMD Athlon 64 3700+
Two IDE hard drives, one as master and one as slave
One SATA hard drive
PCi express GeForce 7800gs

And the hardware I have a slight suspicion is causing this problem for me:
One Sata DVD Burner and no IDE cd/dvd drives.

Ok, I'm gonna go ahead and start trying those things to add to the boot menu now and see if they work.  I'll report back here with the results.  Also any help is greatly appreciated and let me know if you need more information from me and what you need.  Thanks.

---

### Post by bomber991 on 2009-04-11
Well I tried adding all_generic_ide floppy=off irqpoll to the boot options and I got past the Busybox screen.  In fact I got as far as a beige screen with a mouse cursor on it.  I waited 10 minutes and never got past that.  I couldn't move the mouse.  So I tried the same options again but going with the install option, this time I got to a black screen with a X in the middle of it.  I think it's that mouse cursor that's shaped like an X.  Anyways, same story.  I waited a few minutes and nothing happened.

I've got no more time to work on this problem tonight, so I'll be back either tomorrow or monday trying to figure it out.

---

