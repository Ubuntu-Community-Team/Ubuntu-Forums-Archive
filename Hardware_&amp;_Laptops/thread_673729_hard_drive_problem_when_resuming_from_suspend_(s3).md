---
title: "hard drive problem when resuming from suspend (s3)"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by Electricboots on 2008-01-20
First, here's what I'm using:

[LIST]
[*]Mythbuntu 7.10 Gutsy
[*]Biostar TF7050-M2 motherboard (with latest BIOS)
[*]AMD Athlon 64 X2 4400+ Brisbane
[*]Seagate Barracuda 500GB
[*]2 GB RAM
[/LIST]

When I suspend (S3), it seems to work okay.  Computer goes to sleep and I don't hear any fans or the hardrive, and the screen goes blank.

When I resume, it *seems* wake up okay, until, I think, it tries to wake up the hard drive.  Then all I get on the screen are errors like these:

```

ata1 soft reset failed
ata1 COMRESET failed
device sda5 XFS metadata write error block <bunch of numbers>
Buffer I/O error on device sda1, logical block <some number>
Remounting filesystem read-only

```

All I see are error messages like above scrolling... it doesn't seem to stop until I poweroff the computer, wait a few seconds, then poweron and it boots normally.

Do I need to modify something in the acpi-support file?

I've been "googling" for a few hours now... I can't seem to find any solutions... :(

---

### Post by Electricboots on 2008-01-21
I just installed the 'uswsusp' package, but I'm having other kind of problems with it.

If I tried to do 'sudo s2both', I get the following error:

```

s2both: Could not stat the resume device file. Reason: No such file or directory

```

I get the same error with the --force switch. s2disk gives out the same error also.

My /etc/uswsusp.conf looks okay to me:
```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = UUID=fd2bda55-025b-489c-90a0-8e7059f6a412
splash = y
compress = y
early writeout = y
image size = 854830202
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

---

### Post by Electricboots on 2008-01-21
I enabled/uncommented the following two lines in "/etc/default/acpi-support":

DISABLE_DMA=true
RESET_DRIVE=true

...but the problem persists. :(

---

### Post by Electricboots on 2008-01-22
Last night I tried to follow the instructions [HERE]("http://zechs.dyndns.org/wordpress/?p=234") to get s2both and s2disk to work.

When I tried Suspend, nothing seemed to happen at first.  I was still seeing the desktop on the screen, the mouse cursor was still moving.

So I rebooted.

What followed is one of the worst hard drive problem I've ever saw! :(  It said that /dev/sda1 has way too many errors and that it'll only mount read-only so that I can run fsck manually.  Then it gave me a root shell prompt.

I ran fsck, there were many many inode and block errors about this and that.  I was feeling pretty bummed out so I just answer 'y' when it would ask me if I wanted to fix the problem.

The computer then rebooted again, and everything seemed to run normally.  I tried all different programs and things (to see if any important files had been damaged), but everything looks okay.  (Phew?)

I still can't seem to get suspend to work though... :(

---

### Post by yankcrime on 2008-02-06
What follows is a total guess.  I just installed s2disk and s2both and originally had troubles.  It seems my troubles were because for some reason s2* couldn't find the swap partition.  I ran
```
sudo dpkg-reconfigure uswsusp
```
and configured to the best of my ability.  I chose the /dev/sda2 instead of the UUID default (your drive will not likely be /dev/sda2, but chose the one that is /dev/*something* instead of a long string of alphanumerics).
That would be my best guess.  Also, surprisingly, my computer requires s2* be run by sudo (or root) because otherwise  /dev/mem denys permission... hmm. weird.  Perhaps I don't have the answer, but maybe we can work through it together.

---

