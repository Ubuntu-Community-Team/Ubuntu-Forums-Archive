---
title: "Hard drive crash?"
date: 2005-11-12
forum: General Help
---

### Post by BlueNoteMKVI on 2005-11-12
I think I may have f-ed up one (or both) of my hard drives, hopefully some guru out there can help me out.

Yesterday I noticed that my desktop box was running very slow, much slower that normal.  My music started to skip and I couldn't get any apps to load.  I fired up "top" to see what was going on and noticed Amarok taking up a high percentage of my CPU, and my load was up to about 2.75 (normally runs at about .2 or so).  I killed Amarok and kept watching.  The load fell a bit, but was still above 2.5.  I saw lots of things running that are always running, I didn't think much of it...then I saw that "dd" was running and taking a lot of resources.  I've used dd before to copy entire hard drives from one disk to another, I don't know of another use for it.  My paranoid self assumed that someone had found their way into my network and was screwing with things.  I powered down that box and pulled the plug on the network so that nobody outside of the building could do anything.  Since I was the only one in the building at the time, that made things pretty safe.

So then I went to turn my computer back on, and the boot screen told me I had only one hard drive.  That box has two - a 17 gig running Windows in the master slot and a 200 gig running Linux as the slave.  I powered down the box and reached inside to check the connections.  Everything seemed tight, so I powered it back on.  Now I have no hard drives.  They're both in there and spinning but the BIOS does not recognize either.  Off it goes again,  and I pulled it out of the desk to play with it.  I unplugged all hard drive connections, both power and data cables, then plugged it all back in.  BIOS recognized my hard drive but stuck at "booting to CD" - there was not a CD in the drive.

I opened the CD drive, dropped in a liveCD and rebooted.  Everything came up fine with the liveCD.  I can mount all of my partitions and browse around my hard drives.  I've run "badblocks" on both drives, neither of which came up with any errors.  I've tried fsck on the linux partitions.  Trying to fsck my Windows drive comes back with an error about "can't find fsck.ntfs" - a quick Google search seems to say it doesn't exist.  I'm rebooting now into a Windows repair CD to see if that shows me anything useful.

Scanning through the logs does not show anything useful.  I don't see any logins other than myself locally and my backup script that runs from the other end of the building.  There's nothing abnormal in dmesg, syslog or messages.  What else should I be checking?  Is there a reason for dd to be running when I did not explicity tell it to?  If my MBR is screwed up, what is the best way to restore it (assuming that disk is physically ok)?

So...it appears that at least my MBR is jacked up.  Booting to hard disk does not work, it just sits at the point where I normally see a Grub screen.  Did I break something by shutting down when I did?  I didn't just pull the plug, I shut it down normally.

---

### Post by Kuolio on 2005-11-12
I had the same kinda situation happen to me with Breezy. Or, actualy, I'm not that sure if this is the same problem because you enended up there doing very different things then I did.. I was just messing around with hdparm to find out best possible settings for my hd when suddenly after a hdparm -d1 /dev/hda my whole pc froze. Had to do a hard reboot to recover as my kb, mouse and disp were all dead.

Well, after boot when ubuntu began to load, it said that it cant find any HD's. That got me bit worried, so I inserted my Knoppix CD and *ffiiiiiuuuuu* it loaded up w/o any hickups and I could mount all my drives, edit files and folders. Then I ran the diagnostics, everything checked out OK. I moved everything important to my USB backup HD.

Then booted back to HD, and Ubuntu was still dead. Well, decided then to try the easy way out and re-install (as I was in a hurry to get my pc up and running, to do my homework). That worked. End of story.

We propably have different errors, and I dont actualy know why I'm ranting this story in your thread. Sorry.

---

### Post by BlueNoteMKVI on 2005-11-12
After running all of those checks, I could not find a single problem with my filesystem other than the missing information in the MBR.  To fix that, I booted into a liveCD, chrooted into my Ubuntu install and ran grub-install.  Here are the commands, as best I can remember:```

sudo passwd root
mkdir /mnt
cd /mnt
mkdir hdb1
mount /dev/hdb1 /mnt/hdb1
cd /mnt/hdb1
chroot /mnt/hdb1
cd boot
grub-install /dev/hda
exit
reboot

```

So far everything has come up just fine.  I tested briefly under Windows and I'm now working in my Ubuntu environment without any issues.

Can anyone explain why dd was running and what it was doing?  Did I cause the MBR to be blanked by rebooting the computer when I did?  Why?

---

