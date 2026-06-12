---
title: "fstab: One or more of the mounts listed in /etc/fstab cannot yet be mounted"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by [=Vion=] on 2009-11-06
Just upgraded to 9.10. After nice little white ubuntu logo nothing shows up...just a black screen.
If I go to recovery mode this shows up..
Help!

---

### Post by jwmuelle on 2009-11-06
I receive this for my partitions encrypted with luks.  After my upgrade, I'd get prompts for each of the encrypted partitions and these messages would repeat every few seconds until the underlying luks devices were accessible (opened via luks).  I ended up adding secondary encryption keys (via a key file) on the non-root partitions and saved the keyfiles on root so I don't have to manually enter the passwords for each.  Now, I get prompted once for the encryption password (for /  ) then I get a series of the messages you reference until luks has opened all the partitions and they can be mounted by fstab... about 2-3 seconds for each partition.

I've also received these while automated fsck processing was being performed.

If this isn't similar to your situation, are there other messages displayed prior to or during these?

jw.

---

### Post by jstalnak on 2009-11-06
RT @jwmuelle -- you actually have time to type in the password?  On  boot, for me, I get the 'enter passphrase' prompt, but almost immediately text is output at that prompt "One or more of the mounts listed in /etc/fstab cannot yet be mounted:" and things grind to a halt. If I simply key in the passphrase and press ENTER nothing happens for at least 90 seconds (!) and then I get an invalid passphrase error and the same passphrase prompt appears. I enter again and press ENTER and still nothing happens. The encrypted partition is quite valid. I can boot into a LiveCD and cryptsetup luksOpen /dev/sda3 /dev/mapper/cryptohome (enter passphrase) and then mound /dev/mapper/home /mnt/dir and /mnt/dir is exactly what it should be.  It's as if the startup process is interfering with my ability to accurately enter the passphrase when it displays its output (!?).

How did you do what you're doing with the key stuff??

---

### Post by jstalnak on 2009-11-06
Updated behavior -- I see:

* cryptohome (starting)
Enter passphrase to unlock disk /dev/sda3 (cryptohome): One of more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/home: waiting for /dev/mapper/cryptohome

I entered the passphrase and pressed RETURN

After about 15 seconds I saw:

Command failed: No key available with this passphrase.
Enter passphrase to unlock the disk /dev/sda3 (cryptohome):

I entered passphrase and pressed RETURN

Nothing happened. I pressed RETURN again

I got:

Command failed: No key available with this passphrase.
Enter passphrase to unlock the disk /dev/sda3 (cryptohome):

I enter passphrase and press REUTRN *one time*

The blinking underline cursor is still at the prompt and it's now been well past five MINUTES.

---

### Post by jwmuelle on 2009-11-06
For auto-unlocking... I essentially followed these instructions:  [http://howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)   being sure to add a new key.  On my partitions, key 0 is my manually entered pass-phrase and now key 1 is the keyfile.

I'm a recent convert from Fedora and was spoiled by their process that, after I enter the first pass-phrase, it automatically tried it for other luks partitions.  The link above was next-best option I found.  I don't really like having the encryption keys in files... but was quite irritated by needing enter my pass-phrase to unlock several partitions with every boot.


jw.

---

### Post by hawklion on 2010-03-17
Dear All,

Have you solved the problem with luks partition mounted during startup (password prompt). I have the same behaviour for freshly installed Ubuntu 9.10. I read bug reports and found out that cryptsetup has to be updated from "proposed" repository, but ultimately, it didn't helped much. They suggest to add bootwait to fstab. When I add it I get exactly the same behaviour as described here

---

