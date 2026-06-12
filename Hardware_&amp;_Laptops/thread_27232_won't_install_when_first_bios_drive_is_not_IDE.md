---
title: "won't install when first bios drive is not IDE"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by IndieRockSteve on 2005-04-15
ok, first I had an issue where I can't tell GRUB to put the MBR on my SCSI drive. Then I tried LILO and it SEEMED to install ok, but I got the "99 99 99 99 99..." error. Now I tried to unplug all my IDE harddrives and the installer gets stuck in the middle of loading the scsi driver stuff.

now, I've had about 4 distro's and about 8 total versions of linux installed on this machine, none with this problem. If someone can help me figure out why Ubuntu has any of these issues and help me fix them I'd be greatly appreciated.

I have a ECS K7S5A v.1 motherboard with 1 ide harddrive on the mobo and 2 cdroms (on secondary). a U320scsi card with 2 harddrives on it and ATA100 card with 4 harddrives on it. I want to install linux on one of the scsi drives and have the MBR on that same drive. GRUB will place it on /dev/hda and LILO let me choose to put it on /dev/sda but in both instances if I try and boot off the scsi drive I get the 99 99 99 99 error and if I use GRUB and boot off the /dev/hda GRUB gets an error.

Thanks!

---

### Post by Bob D. on 2005-04-15
> Now I tried to unplug all my IDE harddrives and the installer gets stuck in the middle of loading the scsi driver stuff.
Wow, this was the solution I used to see if I could even install Warty, prior to my move to Fedora, as I noted in your other thread. With just my SCSI drive in the system, Warty installed fine and I could boot both Ubuntu and XP. However, I have an older Tekram U2W card, but I would expect Ubuntu to support a U320 card without any problems.

No answer, but at least you get a bump out of me.  ;-)

Bob

---

### Post by IndieRockSteve on 2005-04-15
yea, I have the Tekram U320 card, and if I unplug all the ide drives it gets stuck in the middle of loading the scsi driver, which is really odd, but what happens. I'm guna try Kanotix right now, and if that fails, I'll just reinstall Mandrake, which sucks, I want a debian based distro on my server.

i'll keep playing with it...

---

### Post by IndieRockSteve on 2005-04-15
got it. weird solution:
moved ata100 card to slot3 from 2 and scsi card from 1 to 2. works fine now...

---

### Post by Jad on 2005-04-17
I have same problem now, but both of my HDD are IDE based...
any solution ?

---

