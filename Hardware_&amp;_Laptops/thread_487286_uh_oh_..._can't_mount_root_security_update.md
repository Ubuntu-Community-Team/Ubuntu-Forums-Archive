---
title: "uh oh ... can't mount root security update"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by ChrisC on 2007-06-28
[update: in the subject I meant to say "can't mount AFTER security update"; help!]

Howdy folks -

I posted this in the General Help forum (at [http://ubuntuforums.org/showthread.php?t=486689](http://ubuntuforums.org/showthread.php?t=486689) ), haven't gotten a response there, so I thought I'd try here.  It seems like a filesystem problem.

I've been on Ubuntu for a couple years now, sticking to LTS releases so I'm currently running dapper, awaiting the next LTS release. This morning the computer froze up, so I did a hard reboot, and now it doesn't seem to get past the mounting of the root partition.

I do get the grub menu so I know that the hard drive hardware seems to work. If I let it go through the default entry (2.6.15-28-k7), it gives me the Ubuntu splash page and:

Loading essential drivers ... ok
Mounting root filesystem ...

... and that's where it usually hangs. After a while it sometimes proceeds further to a text-mode screen that said "Reading files needed to boot ..." and hangs there.

If I select the "2.6.15-28-k7 recovery" option on the Grub menu, I get a text mode screen showing the drivers loading and drives mounting, and then it hangs with the following messages coming in very slowly:

[transcribed, not exact]
hda dma_timer_expiry: dma status = 0x61
hda dma timeout error status 0x23
device fault index error
opcode was unknown
dma disabled
ide0 reset success

and that continues with similar mesages for about a minute, then a big flurry of messages including fun terms like "I/O error" and "kernel panic". Once it hung there after "kernel panic" and once it threw me into a BusyBox shell.

While I was composing this and I was rebooting it again to see what the messages were exactly, it actually sucessfully booted. Yay, maybe I dodged a bullet! So I immediately started to back up my files to DVDR, and halfway throug the DVDR write it froze, just like the original freeze that started all this.

I said in the subject of this post that it did this after security update, but that may be a red herring. I did do a regular weekly security update a few days ago, but it did not include any kernel updates or anything else requiring a reboot, and it didn't ask me to reboot, so I didn't. I just had to reboot this morning when it froze, so the update may have nothing to do with it. On the other hand, someone in the other thread has said this EXACT SAME THING HAS HAPPENED TO THEM (6.06, security update, now won't mount root) so there may be a serious general problem here!

Note that my reboots are failing in a couple different ways, so I suspect perhaps flaky hardware or some weird corruption. Every time I reboot I seem to be rolling the dice on what's going to happen.

Can anyone recommend any troubleshooting steps before I spend all weekend rebuilding this machine? I'm not a fan of rebuilds, preferring to keep it down to just once every 5 years or so

My latest periodic (weekly) backup files exist in my home partition. Assuming that partition is OK, and I've got the BusyBox shell, what exactly would I do to write those backup files (directories, actually) to DVDR, via command prompt commands?

Finally, note that my sig says I WILL PAY FOR HELP.

Thanks!

- Chris

---

### Post by ChrisC on 2007-06-29
Anyone?

---

### Post by ChrisC on 2007-06-29
Anyone?

---

### Post by ChrisC on 2007-06-30
One more bump before I dismantle and rebuild this computer and hope the /home directory merge goes smoothly.  I wasn't planning on doing this kind of overhaul until the next LTS release ...

Help?

---

### Post by ChrisC on 2007-07-01
Just following up in case someone else has a similar problem.  I dismantled the computer today and took the two redundant hard drives off the RAID controller and removed the controller.  I then hooked up just the primary HD and the boot problem remained exactly as before.  I hooked up just the secondary HD and the machine booted normally!  I quickly made a current backup of my files before continuing.

It could very well be that this was just a simple hard drive failure.  Both HDs were purchased and installed in Dec 2004, and the secondary actually failed just a couple months ago (and was immediately replaced).  So it looks like the primary just to a little longer to go down the same path.

The RAID controller was set to write to both HDs but READ only from the primary.  Apparently the primary was failing to read properly but the RAID controller didn't recognize this.  I downloaded Hitachi's drive test utility ("Drive Fitness Test", bootable CD ISO) and ran it on both drives and the primary HD failed pretty badly.  Lots of corrupted sectors, and it made the most godawful sounds when it was testing those sectors.

I've placed my order with NewEgg for a replacement hard drive, will arrive Tuesday ...

It's too bad that this RAID controller (ArcoIDE MicroRAID) can't read randomly from BOTH HDs and go ahead and fail over if one of them starts giving weird reads.  I had an older model RAID controller that did that.  If I get time this week I'll call them up and ask them about this.

So, anyway, the moral of the story for this audience (Ubuntu users/admins) is that this is what it looks like if you get corrupted sectors in your root partition.  I still think there might have been something weird with the last security update, but there were no responses to this thread so maybe not ...

---

