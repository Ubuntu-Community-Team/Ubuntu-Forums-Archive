---
title: "YAKUFT: Yet Another Karmic Upgrade Fail Thread"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by werdberd on 2009-11-08
So as of a few minutes ago I have a freshly upgraded and newly non-functional Ubuntu 9.10.  Grub loads and then usplash comes up, but instead of the pulsing white Ubuntu logo you'd expect it's just like a static image with no animated pulsing.  After about 30-45 seconds usplash disappears and all that's left is a blinking cursor in the upper lefthand portion of the screen.  No hard drive activity, it just sits like that forever.

Loading a kernel in rescue mode gets me to a text-based login prompt where I can login and attempt to start gdm.  When I do this I'm told gdm is started/running only gdm never actually comes up and it's not in the list of running processes.  Anyone have a clue what's going on here?

edit: Okay so I just tried 'sudo /usr/sbin/gdm' for the heck of it and gdm came up.  Before I was trying 'start gdm' which did not a whole lot.  I logged in and aside from sound being muted (still works after unmuting, thank goodness...) everything was pretty much in working order.  But why on earth is usplash seemingly hanging the boot process and gdm not coming up when using 'start gdm'?

edit 2: In trying to get my system to actually boot properly using the default kernel entry, I thought it might be a good idea to get the kernel command line as close as possible to that of the one used in the rescue mode.  So the only real difference is that when I remove 'resume=UUID=7ae6109b-6d75-4e93-93d4-0466804c97b4 resume_offset=557056' from the line of kernel parameters the system boots up normally and when it's not removed it just hangs at usplash.  None of this makes much sense because I was using Grub2 on Jaunty before I upgraded to Karmic and everything was fine.  Now unless or until this is fixed I can't resume from hibernate...

---

### Post by werdberd on 2009-11-09
edit 3:  Booting with the resume= related options but without 'quiet usplash' produces some output before things hang.  If anyone knows how I can reproduce that for the thread, it might be helpful.  Looking through the log files there doesn't seem to be any one log that has everything that I saw.

sd 4:0:0:0: [sdb] Attached SCSI removable disk
sd 4:0:0:1: [sdc] Attached SCSI removable disk
sd 4:0:0:2: [sdd] Attached SCSI removable disk
sd 4:0:0:3: [sde] Attached SCSI removable disk

The last thing to be printed on the screen is that stuff and then things hang, but there were other messages I've never seen before.  I suspect they might be upstart-related.  Is upstart activity logged anywhere?

---

### Post by werdberd on 2009-11-09
edit 4: While sitting in front of the hung system attempting to manually transcribe what I was seeing onto a sheet of paper, lo and behold, after about ten minutes or so the boot process continued normally.  The very next thing printed to the screen when things pick up again is this message:

[  644.440694] PM: Starting manual resume from disk

So can anyone help me figure out why the boot process stalls for such a long time when I attempt to boot using those resume= kernel options?  And perhaps how to fix it?

---

### Post by werdberd on 2009-11-09
Just tried resuming from hibernate, and technically it does work although with the ten minute boot process stall described earlier...  Still can't figure out what about having those resume= options on the kernel command line could be causing the system to take ten minutes to boot.  Anyone?  Help?

---

### Post by werdberd on 2009-11-10
Bump...no one has any idea what's happening to cause this ten minute boot delay?

---

