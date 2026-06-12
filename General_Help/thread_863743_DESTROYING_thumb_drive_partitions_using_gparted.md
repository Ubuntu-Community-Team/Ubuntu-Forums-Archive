---
title: "DESTROYING thumb drive partitions using gparted"
date: 2008-07-18
forum: General Help
---

### Post by earthpigg on 2008-07-18
i purchased one of these

[http://www.amazon.com/SanDisk-Cruzer-Titanium-Flash-Drive/dp/B000N4Z4JK/ref=pd_bbs_sr_3?ie=UTF8&s=electronics&qid=1216425845&sr=8-3]("http://www.amazon.com/SanDisk-Cruzer-Titanium-Flash-Drive/dp/B000N4Z4JK/ref=pd_bbs_sr_3?ie=UTF8&s=electronics&qid=1216425845&sr=8-3")

my intention was to remove all the software crap it came with and format it to FAT-32

but the 2nd partition seems to be hiding or something. i cant see it in gparted at all.

when i put it in, TWO devices are mounted - the expected 4 gig fat32 one, and one that has a CD icon and is described as "U3 System" on my desktop.

it doesn't show up in gparted, i have no idea what is going on.

i've seen plenty of threads in the forums of the manufacturer about how to do it in windows... but that doesn't help me so much :)

ideas?

---

### Post by earthpigg on 2008-07-18
the reason i am so determined to destroy the 'hidden' partition, btw, is because i want to put this in the USB stereo we have at work and play MP3's... but the hidden partition seems to be confusing it :)

---

### Post by A. J. Rimmer on 2008-07-18
Here is a link to the official U3 uninstaller:

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

If you click on the "Remove Launchpad" link it will take you to a short questionnaire and then to a download page where you can download the executable.  Unfortunately it appears to be a Windows program, but maybe you can find someone with a Windows box who will let you run it to remove the U3 partition.  Sorry, that's the only way I know to do it.

I bought a U3 drive a while back and thought it was a neat idea (I dual boot XP and Ubuntu) but after a while it just became a nuisance, especially when I mounted it on the Ubuntu side.  Since I have dual boot capability (my wife still uses XP!) it was no problem to run the uninstaller.

I got my revenge, though.  That U3 drive is now configured as a "Live USB Drive" with Gutsy Gibbon so that I can demo Ubuntu for others on their computers.  Kinda slow to boot, but runs a heck of a lot faster than the live CD!

---

### Post by earthpigg on 2008-07-18
ok, well i wanted to avoid starting my windows partition cuz my uptime was so sexy... but i did it cuz i was sick of waiting - and it worked :)

so i guess "solved" :)

---

### Post by tobydeemer on 2008-07-22
I had this also, and how I did was to run a format command. Gparted wouldn't completely remove it. 

My command was like this:

sudo mkdosfs fat32 /dev/sdb

(I think that was it. You'll have adjust it for your device location of course, but I'm at work [shh...] and I don't have my "commands I've used" notes in front of me. Hope this helps.)

EDIT- sorry I replied before I saw the solved part... anyway, it was a useful command for me, and for future reference, right? ;)

---

### Post by A. J. Rimmer on 2008-07-22
tobydeemer --

That's pretty interesting and good to know.  When you get a chance, please let us know the exact command.  Sounds like a good thing to know about.  I had the same experience as earthpigg and couldn't get rid of the U3 partition without resorting to Windows.

---

### Post by A. J. Rimmer on 2008-08-01
Something new in U3, maybe?  Don't know if this is a new development in U3 or is particular to this manufacturer, but is sure makes removing U3 easier:

I just bought a Sandisk Curzer 2 GB USB drive.  It came with U3 and was also clearly marked as supporting Linux (for storage only -- clearly stated).  Tux was even featured on the package!

Anyway, I was going to remove the U3 partition and software, so I downloaded the uninstaller and then booted into Windows.  When the drive mounted the first menu that came up had an option for "I don't want to use U3."  I selected that and found that the CD auto-run emulation feature had been turned off, and the U3 files (including a re-enable U3 executable) were located in the root directory where they could easily be deleted if desired.

I looked at the drive with Gparted and noted that there was an unallocated 4MB at the front of the drive.  Perhaps if U3 was to be re-enabled that would be used for the auto-run function?

Anyway, I divided the drive into two roughly equal FAT32 partitions, did an install-mbr and syslinux, put the Hardy Heron live CD files on the first partition, made the necessary renames, and now I have a bootable "Live USB Stick" that also includes a mountable 1 GB partition.  Files created or downloaded while running the Live version can be saved to that partition for portability.

NB -- I followed the "Manual Approach" from this link after first doing install-mbr p1 /dev/sdx (replace sdx with your USB drive):

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Krupski on 2008-08-01
> **A. J. Rimmer said:**
> Here is a link to the official U3 uninstaller:

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

Yup that's the ticket!

I have lots of Sandisk Cruzer USB sticks and the FIRST thing I do when I get a new one is wipe out the U3 stuff.

---

### Post by Krupski on 2008-08-01
> **A. J. Rimmer said:**
> tobydeemer --

That's pretty interesting and good to know.  When you get a chance, please let us know the exact command.  Sounds like a good thing to know about.  I had the same experience as earthpigg and couldn't get rid of the U3 partition without resorting to Windows.

The U3 stuff is not on the USB stick itself, but rather in it's FIRMWARE. That's why even a complete zero-fill doesn't get rid of it.

The "official" U3 removal tool MUST be used to fix the Sandisk Cruzer. What you're actually doing is modifying the Cruzer's FIRMWARE.

All the zero fills in the world won't get rid of it!  :D

---

