---
title: "Laptop won't boot after install (11.04)"
date: 2011-06-23
forum: Hardware
---

### Post by grw on 2011-06-23
Hi,


My problem: The computer hangs when I try to start it up. I have a fresh install of Ubuntu 11.04 (64 bit). Only sometimes will it boot. I have a brand new laptop, a Thinkpad E420 - Core i5 processor, 500GB harddrive, 4GB RAM

I tried some things from this post: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
I even thought I'd solved my problem by editing /etc/default/grub , uncommenting gfxmode=680x480. The computer started normally. (I then tried to get the wireless going....)

Finally, I shut down and tried to restart. The computer wouldn't boot at all. Not even in recovery mode. I gave up after 7 or 8 attempts. I am using a Knoppix live cd to write this...

When I try to startup in recovery mode, the computer often hangs at this line:

eth0: no IPv6 routers present

Or at this line:

type=1400 ..... apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=781 comm="apparmor_parser"

This is driving me nuts. A laptop that won't start isn't much good. If anyone can help, I'd really appreciate it.

Note: I first posted my problem under Installation and Upgrades here:
[http://ubuntuforums.org/showthread.php?t=1785387](http://ubuntuforums.org/showthread.php?t=1785387)

---

### Post by owiknowi on 2011-06-23
have more or less same troubles with a hp dv6:
after a fresh install of ubuntu 11.04 -64 it boots just fine but wireless (ralink 3090) doesn't start.
after wired updating the laptop sometimes doesn't boot or is unable to shut down...

i realize this doesn't solve your problem but i've read similar troubles on other penguin forums too.
maybe something with new hardware / chip sets?

---

### Post by rvchari on 2011-06-23
i too went for fresh install in t500 thinkpad. i could get everything work out of box (gnome shell / unity / classic)
i have a buggy unity panel... nothing more.

firtstly my laptop refused to go beyond login screen. i simply shut out and restarted a couple of times and natty fired up...
it seems absurd but true...

---

### Post by grw on 2011-07-09
Ok. Been away for a bit. 

I reinstalled Ubuntu - actually I first installed fedora 15. I then installed Ubuntu 11.04 (using the alternate install CD). I followed these instructions for installing with Logical Volume Management (LVM): [http://www.linuxbsdos.com/2011/06/20...ioning-scheme/](http://www.linuxbsdos.com/2011/06/20...ioning-scheme/)

On the Fedora install, I installed Grub to the MBR, then overwrote it with Grub2 when I installed Ubuntu. I got an error during the Ubuntu installation saying Grub couldn't be installed. But it actually seemed to install OK, given that the Grub menu appeared on startup and I could then boot into both distros. For a while, at least...

The computer started up fine in both distros a couple of times. (I fiddled, added a logical volume (partition), edited fstab....) But now I can't boot at all. In Ubuntu, it hangs at the same place as in my first post.

In the Fedora forums, someone suggested reinstalling the BIOS. The problem is that my BIOS is a later version than the latest version I can find on the internet - I have Lenovo BIOS version 1.12 (UEFI BIOS 8HET30WW), while the Lenovo website lists 1.10 (8HET28WW) as most recent version for my Thinkpad E420. All a bit confusing. SHould I downgrade my BIOS?

What am I to do to get my laptop going? Can anyone help?

Gwyn
Edit/Delete Message

---

### Post by srs5694 on 2011-07-09
The fact that you've got UEFI firmware creates both new complications and new opportunities. My *suspicion* is that you've installed in BIOS mode in some way that uses block lists, which tend to break when files move or are updated. If so, re-installing GRUB might fix the problem, at least temporarily; or you could re-install in a way that doesn't require block lists but that still uses BIOS; or you could convert to a UEFI boot method. Each approach has its advantages and disadvantages, but to provide good advice, more information is required.

Please download the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/), run it from an emergency disc or the Ubuntu installer in its "try it now" mode (or whatever it's called), and post the RESULTS.txt file that it produces here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That will show us how your disk is partitioned, and perhaps give us some clues about how it's currently set up to boot (although the last I checked, the Boot Info Script didn't properly identify some key UEFI boot features, so if you're currently using UEFI mode, its information will be incomplete).

---

### Post by grw on 2011-07-09
I booted in with a Knoppix live CD and ran the Boot Info Script. Not quite sure what you mean by code and /code tags, so I'll just attach the RESULTS.txt file
gwyn

---

### Post by srs5694 on 2011-07-09
It looks like a fairly normal BIOS-style installation, at least for a two-Linux-distribution dual boot. I'm not sure what the "??" means in the following, though:

```
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

```

It could be that's what's causing the failure -- perhaps the GRUB 2 post-MBR code has become damaged or something else is causing it to fail. If so, the best solution, certainly in the short term, is to re-install GRUB 2. The way I'd do this is to boot Ubuntu using [Super GRUB 2 Disk](http://www.supergrubdisk.org/) and then type "sudo grub-install /dev/sda" in a terminal window. It's also possible to re-install GRUB 2 from an Ubuntu install disc, but I don't recall the precise instructions offhand.

---

### Post by grw on 2011-07-09
I made a Super GRUB2 disk, then booted with it in the CD drive. I expected it to list the OSs installed on my computer, but it didn't. There were a number of other options, however.

This is what I did:

Detect any OS: "No OS found", it told me.
Then I enabled GRUB2's LVM support.
Still no OS found.
Then I asked it to List devices/partitions: it detects everything, I think, but lists all as ext2 (all are ext4).
Then I ran Detect any GRUB2 installation and got: "Load /grub/core.img from (hd0,5)". I did, and got to the GRUB screen I normally get when I try to boot. This lists Ubuntu, Ubuntu recovery mode, memory test, and Fedora. I tried Ubuntu recovery mode and it hung, as usual.

I will see if I can work out how to install GRUB2 from the Ubuntu install disk.

---

### Post by srs5694 on 2011-07-10
I'm afraid I misunderstood the nature of your problem. My apologies. I doubt if re-installing GRUB will do anything useful, since GRUB has long since finished doing its job by the time you encounter your problem.

I'm afraid I don't know what might be causing those hangs; however, I have a vague recollection of hearing of an AppArmor problem that causes boot failures, but I don't recall the details. You could look into this further, though.

Another thing you might do is to boot using an emergency disk and examine the ends of the log files on your normal installation. Perhaps one of them will have a clue in the form of an obvious error message.

---

### Post by grw on 2011-07-10
Ok, so if I understand correctly, GRUB is working fine and my problem starts once the linux distro takes over. I'll see what I can find out about AppArmor etc. 

Is there a particular linux forum I might go to for help with my boot problems?

Thanks srs. I appreciate your help.

---

### Post by srs5694 on 2011-07-10
Yes, once you start getting messages about such-and-such subsystems starting, the Linux kernel has already taken over and the computer is running the many startup scripts that launch all the little things we take for granted and hardly notice -- unless something goes wrong!

My guess is that the "General Help" forum is most appropriate for this problem. The error messages you related in your first post are the most critical. The GRUB and Boot Info Script stuff was all a wild goose chase, I'm afraid -- *except* that there's a very very slim chance that you'll have better luck booting in UEFI mode than in BIOS mode. I don't think this will make any real difference, but if all else fails, you could try reconfiguring the system to boot in UEFI mode. The odds of this doing any good are so slim, though, that I don't recommend pursuing this option unless you can't get a better solution after posting a new thread in "General Help."

---

### Post by bolwara on 2012-05-07
Hi,
 
I know this is an old thread and I will completely understand if no-one responds.
I was given a cute little Sharp Mebius laptop - kind of a pre-netbook.  Running Windows XP but with small RAM and small hard drive.  The laptop worked perfectly well except it was in Japanese and I was not able to alter the language set up.  I wanted to install an older version of Ubuntu (10.01 I think) on it in any case - for the greater functionality.  I elected to intall the dual boot option.   During the install I saw a warning saying there was not quite enough memory and asking if wanted to live dangerously [not in so many words].  Being foolhardy and optimistic I elected to go ahead.  
 
The installation completed but following reboot all that happens are flashing battery lights.  I know that I have done a bad thing. I had visions of using this great, lightweight laptop instead of the cheap Android tablet I have been using for various tasks I undertake on the way to work.  I still hope to install Ubuntu or maybe Xbuntu.  But the issues are:
 
The laptop does not come with a CD drive.  The CD I used was by cable and is not recognised for boot purposes.  Some code advice to install again  would be greatly appreciated.
I anyone is familiar with the Sharp Mebius even better.):P
 
Sorry for my verbosity.

---

### Post by grw on 2012-05-10
Can't really help with code for a reinstall. You could try Lubuntu though, lighter than Xubuntu. Or Bodhi linux.

Here's a link to a thread I started after this one. Some ideas there perhaps: [http://ubuntuforums.org/showthread.php?t=1801878](http://ubuntuforums.org/showthread.php?t=1801878)

Good luck

---

