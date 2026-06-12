---
title: "large number of hard disk errors--crashed system"
date: 2017-04-10
forum: Hardware
---

### Post by Peter_Brandon on 2017-04-10
Here's a mystery.  One day, my laptop wouldn't restart.  I got kicked out to an emergency command line and used fsck to correct a large number of errors on various partitions.  I got back into my system, but kept having to run fsck on reboots / crashes (usually crashes).  fsck seems to eventually corrupt my software, so I end up with segmentation faults on everything and can't use the system (though my personal files are unaffected according to a checksum test).

It's an old laptop, so maybe the hard disk or memory are going.  I spent  a whole day running the disk and memory diagnostics from the laptop manufacturer (accessible at startup).  This turned up nothing.

So, I figured the problem probably isn't the hardware and decided to do a fresh install of the latest version of ubuntu (16.10, yakkety), erasing and reformatting the /boot and / partitions, though leaving my /home files intact.  I'm mostly using the Mate desktop (hmm, and these hard disk problems started around the time I switched to Mate from KDE).  Anyway, even on startup after a normal shutdown, I get kicked to an emergency command prompt and again find a large number of hard disk errors with fsck.

Any thoughts on what I should try next?  Or should I be looking for a new laptop?

---

### Post by Autodave on 2017-04-10
Unless someone else has a miracle cure for you, sounds like the hard drive is calling it quits.

---

### Post by Peter_Brandon on 2017-04-10
Thanks Autodave!  Yup, that's a real possibility.  On the other hand, if the problems w/ the HD are so overt, you'd think the 3 hours of testing I did on the disk drive would have turned up something.  I wonder if there's a more thorough test I could do.

---

### Post by deadflowr on 2017-04-10
Not sure what tests the Machine's diagnostics run, but look at running a smart test:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

---

### Post by Peter_Brandon on 2017-04-10
Thanks deadflowr!  I'm currently running the long smartctl test (short test showed nothing):

sudo smartctl -t long /dev/sda

I also looked at smart stats using the GSmartControl tool (no problems, though the log shows two 'identity not found' errors in standby mode over the lifespan of the drive, which I suspect is nothing or attributable to the Ubuntu kernel).

If my smartctl long test doesn't work,I might try the following, which is actually something I should have started with.  It's a read / write non-destructive test of the entire drive that can sequester bad sectors.

e2fsck -c -c /dev/sda

The problems seem to be growing w/ my newly installed 16.10.  Programs are crashing and web pages that are already displayed suddenly disappear and show an 'Aw, Snap!' error, which makes no sense to me.  Almost feels like malware.

---

### Post by efflandt on 2017-04-11
In my case I had Linux at the far end of the drive, and when I got into Linux Steam and started downloading games filling up the end of the drive I began to run into problems with a 3 year old Seagate drive. Sectors are physically smallest at the end (center) of the drive, so that is where issues might tend to show up. The initial symptom was that suddenly I could not save files in my own home directory because when Linux senses too many drive errors it remounts the drive read-only. I had another system on an old SSD that I could boot to e2fsck my hard drive, then at some point when I repeatedly had to do that I used the e2fsck options to find and lock out badblocks. The Win7 partitions were not affected and since I needed more room for games, I used Window's own Disk Management to shrink its partition and cloned that to a new drive before reinstalling Linux and copying my home dir from the failing drive. There were only a few game files with messed up textures, but Steams Verify Integrity of Game Cache replaced those files.

So far I have not had any problems with the Western Digital drive I replaced it with, but I have a gaming laptop that will not turn on, so I am currently running 16.10 from mSATA SSD card in a SATA adapter and I still have 14.04 on the hard drive. I could not run 16.04 due to some strange issue with this computer only such that no text shows up during boot, so no BIOS splash screen or grub menu until I got to something that did graphics (blank screen until gui login). 16.04 desktop worked fine, just could not see BIOS or grub to boot anything else.

---

### Post by Peter_Brandon on 2017-04-11
Thanks efflandt--it's good to hear I'm not the only person running into problems.  My drives or mostly only 60% filled, so I suspect I'm not running into the kinds of issues you did.

So, some results.  The long smartctl test (drive read test) turned up nothing (well, a couple errors over the lifetime of the drive, but errors I suspect have more to do with a kernel that isn't quite right for this hardware, but otherwise nothing).  The e2fsck -c -c /dev/sda? test couldn't be run on the whole drive (which contains swap and windows partitions), but so far I've run it on my /boot and root partitions (still running on /home).  Found absolutely nothing--which I guess I should have expected from the smartctl test and what drives do these days.  e2fsck uses a random pattern, so I guess it doesn't test every bit, but given the scale of the problems I've been having, you'd think a random sample of every block would turn up something.  Yet, nothing.

I did discover something interesting which is that programs like chromium are trying to access non-existent devices.  The devices look like things chromium might set up for external communications, which could explain why I have web pages suddenly going belly up.  Maybe these devices were left in the settings / cache info from my previous version of the OS (the one I replaced to get away from such problems).  Or maybe there's something erasing these devices after they're created.  Not sure how any of this could happen--maybe I should check the integrity of the hard disk swap partition.  rkhunter found no malware.

---

### Post by Peter_Brandon on 2017-04-12
The e2fsck on my /home folder finally completed and no errors found.

So, I reformatted my swap drive as ext2 and ran e2fsck and then formatted back to swap.  No errors found, but this reformatted my swap partition, which may have corrected something(?).

Then, I went back into my system and deleted user data folders for Firefox, Chromium, and Chrome.  Reinstalled Chrome and Flash.  I've now used the system for one evening and have encountered no errors.  Hopefully it'll stay like that!  It may be that it just *looked* like I had hard disk problems, but this was due to my system crashing repeatedly (it never liked the 16.04 kernel), corrupting the drive and user data files used for communication on my browsers.  At least I can hope :) .  

I've looked at new computers and don't see that big of an advantage over what I have now (bought in 2011!), though of course I haven't experienced the new systems.

---

### Post by Bashing-om on 2017-04-12
Peter_Brandon; Hey ...

Additional thoughts ... SATA controller ??
Do you have a IOMMU option  in bios ? and is it enabled ?
Do you have a AHCI option in bios and is it enabled ?
SSD drives ? -> my bios requires raid to be enabled - this a factor in your system ?

Been there done all that - system write I/O errors - Maybe Now I am solid .

[INDENT][INDENT]could be this
[INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Peter_Brandon on 2017-04-14
Thanks Bashing-om:

Am not sure what to do to test / replace / whatever the SATA controller.  Thoughts?

AHCI is definitely active on my system.  IOMMU is part of intel VT, which my chip has.  Can't imagine the manufacturer didn't have this on in the BIOS and don't believe I've ever fiddled with the BIOS for anything that affects this.  I guess it's possible for an old system to have settings change at random.  Will check the next time I reboot.

I've got no SSD drive.

---

### Post by Bashing-om on 2017-04-14
Peter_Brandon; Hey !

Like you I have an old old system ( AMD dual core ) that I am very fond of .
However, since hardware upgrades I too experience un-explained freezes. When it freezes there is no logging .
Not having any hints on what is not taking place makes trouble shooting a hit and miss affair. I only pass on to you what I know and have tried .

My system: - maybe I have it .. maybe not.
[INDENT][INDENT]see what the day brings
[/INDENT][/INDENT]

---

### Post by samuelfcampbell on 2017-04-14
Wow! This is so like what I'm just going through with an recently acquired upgrade Laptop from my normal old Dell Computers:
*** Dell Latitude D630 -** 14.1-Inches Laptop (Core 2 Duo Dual Core 2.0GHz, 2GBRam, 80GB HDD, DVD Player, Windows XP), Grey, Dell. 

*** Dell Latitude E6400 Notebook PC** - Intel Core 2 Duo 2.4GHz 4GB 160GB Linux 60bit
Linux Version 3.19.0-32-generic (build@lgw01-43) (gcc version 4.8.2-19ubuntu1) #37-14.04.1-Ubuntu SMP Thursdqay Otc 22 09:41:40 UTC 2015 
Updated 
Latitude E6400 4.4.0-53-generic #74-UbuntuSMP Fri Dec 2 15:59:10UTC 2016 x86_64 X86_64 X86_64 GNU?Linux 
 
*** Dell Latitude Workstation -T3400 DeskTop Tower** Linux .
3.13.0-37generic #64Ubuntu SMP Monday Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
These Are my normal machines 

On **my new Laptop** I started out with ***video playback freezing*** until, I started using VLC instead of Video Ok! VLC no freeze. Fine! Still thought I could live with it for a while. Then I get happy with my new found memory, storage, and download speeds. After a night of downloading movies and music I reboot and get kicked into the*** initramfs ***command line due to certain incomplete, and corrupt downloads, too many to mention!  I researched resolutions for both issues the freezing and the **initfamfs command line** all leading to suggested CD or jump drive Live reinstall, so I then started to use the Gparted check process in hopes of cleaning up and repairing the corrupted partitions if any found . Now! Due to my upper line of Linux associates, they have decided to take the Laptop back and put it back on the bench. Put another operating system on it and test the Hardware ie... CPU operating temperatures and other components for proper operations by way of a through process of elimination till the freezing issue is resolved if it can be resolved. Even if not resolved, if the process is completed in a timely manner the Laptop may still be able to be returned to the seller.  Keep on Keeping on, Living and Learning the Linux Systems. The learning stages, we can be our own worst enemies.
                        ;)   Fingers Crossed **~ Samuel F Campbell **

---

### Post by Peter_Brandon on 2017-04-22
Well, I think I've identified my problem.  I ran memtest86 which found very consistent errors in 1.1 MB of memory.  This could help explain why my OS and hard disks have gotten corrupted in the absence of any evidence of hard disk problems.

I've sought to fix the error using memmap, for now--I'm interested in getting a new machine after AMD Ryzen processors make it into laptops, which is probably 9 months away.  memmap tells the linux kernel to avoid a specific range of memory.  I cut out 2MB around the problem area identified by memtest86.

I couldn't find much by way of clear instructions on using memmap with GRUB2.  So far, I've done a temporary fix that places the memmap command in /boot/grub/grub.cfg after UUID=... ro .  It works--free -m shows a reduction of exactly 2 MB of RAM.  I also ran a memory tester after getting into the OS and it found no errors.

---

### Post by Peter_Brandon on 2017-04-22
And now I've found a way to make the memmap change permanent.  In /etc/grub.d, I altered 10_linux .  There are a couple places where you can find:  ro ${args}  .  These lines generate the grub.cfg lines that control boot-up.  I changed these two places to:  ro memmap=2M\\\$2357M ${args} .  grub.cfg now generates with memmap=2M\$2357M inserted in the right place in all linux entries.  So the next time the kernel upgrades, this should be taken care of automatically.  The backslash is an escape character that gets 'used up' as every program pass processes it, which is what it starts as \\\ and winds up with \ in the menu (and then disappears entirely when actually run).

I also seem to have taken care of another potential source of corruption in my system by updating to Yakkety 16.10.  Pre-4.8 kernels crashed  every few days on my laptop (complete system freeze requiring a hard reboot)-- despite the fact that the laptop came out in 2011 and the Ubuntu hardware guide has claimed for years that the laptop works with Ubuntu.  Also despite the fact that I reported this problem years ago and it was not resolved until 4.8 came out (Canonical's approach to fixing the problem was to keep asking me to try mainline upstream kernels rather than actually fixing the problem).  If it takes six years to update the OS so it doesn't crash a fairly common laptop, I suspect not many people will stick w/ Ubuntu.  I love the Ubuntu environment, but wish that it really was plug and play rather than a hassle.

---

