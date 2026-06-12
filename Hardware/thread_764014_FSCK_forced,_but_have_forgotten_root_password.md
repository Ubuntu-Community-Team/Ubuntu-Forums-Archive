---
title: "FSCK forced, but have forgotten root password"
date: 2008-04-23
forum: Hardware
---

### Post by potatan on 2008-04-23
Hi,

My laptop has a bit of a dodgy hard drive, and I get the message

```
an automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted
.
.
.
Give root password for maintenance
(or type Control-D to continue): 

```

Trouble is, I do not know the Root password.  I'm not even sure I ever set it, and I have only ever used "sudo" to perform admin tasks before.

Is there some way to perform an fsck using some sort of recovery CD, and to then reset the root password so I don't get stuck in the future?

Many thanks in advance

---

### Post by Patsoe on 2008-04-23
If you boot in recovery mode (should be in the GRUB menu), you automatically get a root shell, no password asked. From there you can run fsck, then reboot.

(by the way, this is sort of a bug - the system asking for a root password that should not be defined on a standard Ubuntu install. You might want to report it)

---

### Post by potatan on 2008-04-23
Thanks - I've tried booting in recovery mode, but it kinda goes through the same steps, disk errors, forcing fsck, then asking for root password.

The laptop is about 5 years old (HP Pavilion dv5xxx series), so I suspect the HDD may be on the way out, but it has managed to recover before.

Is there perhaps an option to run s file system check of the hard disk, by running a Live CD, perhaps?

Thanks in advance.

---

### Post by Patsoe on 2008-04-23
Yes, I think you could do that with pretty much any GNU/Linux LiveCD.
E.g. SystemRescueCd comes with a lot of recovery tools.

But what happens if you just hit ctrl-D like it says? Can't you continue booting then and run the fsck from there?

---

### Post by potatan on 2008-04-23
No, hitting ctrl-d just restarts the machine

I'll see if i can figure out how to mount the drive, and fsck it using my live-cd.

thanks

---

### Post by ajgreeny on 2008-04-23
You can't run fsck on a mounted partition so you will not be able to boot into ubuntu and then run fsck at all.  You could try using the terminal and typing ```
sudo touch /forcefsck
``` then rebooting, which will force a system check at that boot, but it sounds as if that's basically what the system is forcing anyway, so it may not make any difference.  If it doesn't work, boot into a live CD and then run ```
sudo fsck /dev/*d*
``` using the partition device name in place of the *d*, but make sure it is unmounted first.

However, I do suspect that you may be right and your hard disk is on its last legs, so now would be a good time to backup everything onto a USB hard drive from the running system, either using the live CD you use for fsck, or the install, if you can get it up and running.

---

### Post by potatan on 2008-04-24
Well it's fixed, and the laptop lives to see another day (until the next time the hard disk decides to throw a wobbly).

I booted from a live CD, ran
```
sudo fsck /dev/hda2
```

then got:
```
/dev/hda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

Error reading block nnnnnnn (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>? yes

Force rewrite<y>? yes
```

and it ran to completion and allowed me to reboot.

Now I'm back in, I'll reset the root password for the next time this happens.  Actually, I'll do the same on the other two desktop machines in the house also.

The laptop was my first excursion into Ubuntu about 6 months ago, following repeated failures of Windows, probably due to the hard disk error.  I was impressed enough with the setup and configurability, and particularly the support on this forum and elsewhere, that I converted both desktops and have since persuaded friends to convert theirs too.

Next up, Hardy Heron!

Thanks for your help folks.

---

### Post by potatan on 2008-04-24
How can I mark this thread solved? I don't see the option in thread tools any more.

thanks

---

### Post by Patsoe on 2008-04-24
Happy it's resolved.
You probably want to backup your data, like ajgreeny says, and also check integrity of the backed-up files (if you have a dying hdd, you might be backing up errors rather than the real file content).

The e2fsck tool has a -c option (specify twice for read/write test) to mark bad blocks (see the man page). Good luck with the disk!

---

### Post by potatan on 2008-04-24
So, if I'm reading this correctly, running e2fsck will mark and bad blocks so the machine is less likely to freeze up in future?  Soudns like a good plan!

I can't quite figure from the Man page, specifiying the -c option twice - is it:

e2fsck -c -c /dev/hda?
or 
e2fsck -cc /dev/hda

Thanks

---

### Post by Patsoe on 2008-04-24
"-c -c" will definitely work, I think "-cc" means the same though.
Oh yeah, note that this will take a serious amount of time, because it's going to flip every bit on your hard disk around.

---

