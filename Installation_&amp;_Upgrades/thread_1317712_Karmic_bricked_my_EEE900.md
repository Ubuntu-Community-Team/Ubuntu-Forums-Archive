---
title: "Karmic bricked my EEE900"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by trey333om on 2009-11-07
I'm not trying to sound dramatic. I'm not a newbie. My EEE900 is bricked because of trying to install Karmic. This is a version of Bug 387272 in Launchpad made extreme by my persistence in trying to to get Karmic installed.

The problem: my two SSD drives are locked or dead. Fdisk and gparted in Crunchbang 9.04 doesn't even see them. Crunchbang and Ubuntu 9.04 install partitioner can "see" the drives, but I get I/O errors when it tries to format for install. Even a live USB of Gparted only sees the USB drive it's booting from.

The history: Tried installing Karmic NBR. All sorts of errors on reboot.  Third reboot GRUB error. Reinstall on the 16gb drive. Same errors on GRUB after a reboot or two. Try again. Try installing Jaunty, then upgrading. Same problem. Now I am where I am.

Where I am now: my $500 computer is a doorstop right now. This is entirely Karmic's doing. This is not a preexisting hardware issue. Karmic or its kernel did something fundamentally evil and seemingly permanent to my hardware.

Other issues: Launchpad still doesn't think this is a big problem. No one in the Ubuntu IRC channel had any interest in helping. This is more than disappointing, this is infuriating. How can a bug this big make it to release?  Am I really out the cost of two new SSD drives to get my computer working again?

---

### Post by kerry_s on 2009-11-07
did you try to zero them?

```
dd if=/dev/zero of=/dev/?
```

replace "?" with the drive, use "fdisk -l" if you don't know.

---

### Post by sgosnell on 2009-11-07
$500 for a 900???   :eek:

Have you tried removing and reinstalling the SSDs?

---

### Post by trey333om on 2009-11-07
sgonsnell: a last resort has been to take them out and getting them somehow connected to my desktop (SCSI-USB adapter maybe?)... but I've never really touched the insides of a laptop before. How would taking them out and back in fix anything that a BIOS flash wouldn't? I'll try it anyway - it couldn't possibly be more broken. BTW, it was $500 the week it came out in Hong Kong.

Kerry_s, fdisk doesn't work. Using my best guesses:
> crunchbang@crunchbang:~$ sudo dd if=/dev/zero of=/dev/sda1
dd: writing to `/dev/sda1': No space left on device
1016905+0 records in
1016904+0 records out
520654848 bytes (521 MB) copied, 4.37777 s, 119 MB/s
crunchbang@crunchbang:~$ sudo dd if=/dev/zero of=/dev/sdb1
dd: writing to `/dev/sdb1': No space left on device
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0013325 s, 0.0 kB/s
crunchbang@crunchbang:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: writing to `/dev/sdb': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 1.41622 s, 0.0 kB/s
crunchbang@crunchbang:~$ sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.146045 s, 0.0 kB/s

---

### Post by sgosnell on 2009-11-07
Resetting the connectors might fix a poor connection.  Not likely, but possible.  The SSDs in the the 900s are cheap, and they have been problematic for a lot of people.  Mine pretty much died, and I replaced it with a 32GB SSD from Newegg for not a lot of money, and I'm happy with it.

---

