---
title: "Hard drive issues after upgrade to Jaunty"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by vetch101 on 2009-04-25
Hi everyone,

Bit of a problem here...

I've upgraded my Ubuntu Server 8.10 to 9.04...
It's running on a "HP ProLiant ML115 G5 - Micro tower - 1-way - 1 x Third-Generation Opteron 1352 / 2.1 GHz - RAM 512 MB - HDD 1 x 250 GB - DVD-RW - Gigabit Ethernet - Monitor : none"

Following that, on the default kernel (2.6.28.11 - if I remember correctly), it came up with the message that I needed to run fsck manually...

I did that and it came up with a huge number of errors - e.g. 

Inode 80173 has compression flag set on filesystem without compression support. Clear <y>? no

Inode 80173 has INDEX_FL flag set but is not a directory.
Clear Htree index<y>? no

HTREE directory inode 80173 has an invalid root node.
Clear HTree index<y>? no

Inode 80173, i_size is 8608480567731124087, should be 0. Fix <y>? no

Inode 80173, i_blocks is 131354989131639, should be 0. Fix<y>? no

Then these errors start again with Inode 80174...
Always i_size and i_blocks is the same number...

Also, I get:-

Inode 80395 is in use, but has dtime set. Fix<y>? no

Inode 80395 has imagic flag set. Clear<y>? no

Inode 80395 has a extra size (30583) which is invalid
Fix<y>? no

Then back to Inode 80396 is in use, but has dtime set....
And these continue for ages too....

Seems like every inode has at least 3-5 problems...

As you can see, I said no to the fix...
After rebooting and coming back in with an older kernel 2.6.27.11 (I think) it is a bit happier...
It still says that there are problems and prompts for the fsck to be run manually... it seems to think there are problems with /dev/sda...
This is a bit odd, because I'm using fake raid so i don't normally access the /dev/sda directly...
Everything is on /dev/mapper/sysvol_x

Plus my /home partition no longer automounts... and when it's manually mounted, it's seen as a ext2 rather than an ext3...

It seems that all the data is ok, and fsck claims that /dev/mapper/sysvol_home is clean...

On a more positive note, the 3 servers running in KVM under the main host seem to be fine...

So - does anyone have any suggestions?

I'm tempted to fsck /dev/sda, but I don't know how that will impact all the lvms on the device - or the RAID array...

I'm tempted to use fsck to "fix" the problems that the latest kernel sees, but it seems like it must be the kernel rather than the data if it's not broken on the earlier kernel...

Should I just uninstall the latest kernel and work from the earlier one?

What are the chances or there being a fix released for the latest kernel before 9.10? As I understand it, no new versions are released between Ubuntu releases - just security patches... Is that correct? Or would bug fixes be likely to be forthcoming?

What's the next step in diagnosis?

Any recommendations gratefully received!

Jx

---

### Post by vetch101 on 2009-04-25
Hi everyone,

Just to follow up, I've found that when I try to mount the home drive as ext3, it returns 

ext3: No journal on filesystem on dm-8
mount: wrong fs type, bad option, bad superblock on /dev/mapper/sysvol-home, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

So when loading the 2.6.27.11 kernel, the main problem appears to be related to the missing journal on /dev/mapper/sysvol-home...

Does anyone have any idea how that could have happened?

Cheers,

Jx

---

### Post by vetch101 on 2009-04-25
Hi all,

ok after running a 

# tune2fs -j /dev/mapper/sysvol-home

and then an #e2fsck /dev/mapper/sysvol-home, the problem with mounting seems to have gone...

I am, however, wondering what I should do about the 2.6.28.11 kernel...
Should I uninstall it? Should I set the default to be 2.6.27.11 so that when there are updates, I can test it again...?

Each time I try booting with the 2.6.28.11 kernel, it writes errors to the filessystems...

Also, kvm on the 2.6.27.11 kernel has started throwing up info messages that I wasn't getting previously, but I'll raise that in another thread...

Cheers,

Jx

---

