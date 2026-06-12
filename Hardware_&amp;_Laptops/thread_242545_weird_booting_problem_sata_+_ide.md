---
title: "weird booting problem: sata + ide"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by autrui on 2006-08-23
hi folks,

im pretty new to ubuntu, and i'd love any help i can get on a booting issue.  

**basic setup:** 
Ubuntu is on my SATA HD; i have an additional NTFS IDE HD which is used for storage only. (once, ages ago, the IDE housed windows--about 6 months ago i removed windows from the IDE and put it on the SATA.  ubuntu replaced windows on the SATA a few days ago.)

**symptom: **
when i start the computer, i get past my dell splash screen, and no farther.  just a flashing cursor at the top of the screen.  if i hit f12 (boot menu), i have 8 options - #3 results in a successful loading of ubuntu.

here are the options, and their results:

1. normal - blank screen, cursor at top.
2. sata primary drive - "error loading operating system"
3. primary master drive - success!  happiness!
4. hard-disk drive c: - "error loading operating system"

(5-8 shouldn't matter--cd-rom; bios menu; drive diagnostics (both drives pass); & boot to utility partition--idk what that is.)

last thing i should mention is that in the BIOS setup, "primary master drive" seems to be identified as "hard-disk drive c:" and in the boot sequence, my only HD option is that one; i am unable to add anything else (like the SATA) to the list.

folks on #hardware suggest that my bootloader is on the IDE drive, and the OS is on the SATA drive, but that information hasn't really gotten me any closer to a good boot.

anyone have any idea what the heck is going on?

thanks,

autrui

---

### Post by autrui on 2006-08-24
just wanted to bump this.  perhaps someone knows in which direction i might go to find a solution?  i'm reading up on Grub, but i'm terrified of screwing it up.  (and, from what i've read, that's a reasonable fear ;))

thanks,

autrui

---

### Post by autrui on 2006-08-25
this will be the last time i bump this, so i don't get annoying.  again, any post that could point me in the right direction would be helpful.

thanks!

autrui

---

### Post by Cynical on 2006-08-25
Boot into ubuntu and install grub to the mbr.

> grub
to get to the grub prompt
> root (hd0,0)
change this to point to your ubuntu install
> setup (hd0)
To install it to the mbr
> exit

---

### Post by autrui on 2006-08-25
thanks so much for replying.  however, something funny happened when i went through your steps:

```

grub> root (hd0,0)

Error 21: Selected disk does not exist

```

from what little i know, this shouldn't happen; i was to understand that sata/ide/scsi drives were all "hd" to grub..  am i making a simple error or is there something seriously weird with my set up?  if the commands you've suggested don't work in (hd0,0), should i try (hd0,1) or something?

here's the list of hds and partitions from terminal:
```

autrui@compy:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            193034844 170727564  12501608  94% /
varrun                  517792        76    517716   1% /var/run
varlock                 517792         4    517788   1% /var/lock
udev                    517792       128    517664   1% /dev
devshm                  517792       372    517420   1% /dev/shm
lrm                     517792     18388    499404   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1            244196000 236824124   7371876  97% /media/windows

```

(and yes, i am using a lot of my HDs lol--i'm about to format hda1, so almost everything from there is also on sda1.)

thanks,

autrui

---

### Post by Cynical on 2006-08-26
If /dev/sda1 is your 2nd partition then yes I would use (hd0,1) instead.

---

### Post by LKRaider on 2006-08-26
One possible solution is to create a small partition on the IDE drive to house the /boot files and configure everything from there.

Troubleshooting SATA drives is really a PITA, as Grub sometimes doesn't list the drives in the order you see them on your system. (may be BIOS related, idk)
See this: [http://www.linuxquestions.org/questions/showthread.php?p=2283784](http://www.linuxquestions.org/questions/showthread.php?p=2283784)

---

### Post by autrui on 2006-08-27
> **LKRaider said:**
> One possible solution is to create a small partition on the IDE drive to house the /boot files and configure everything from there.

Troubleshooting SATA drives is really a PITA, as Grub sometimes doesn't list the drives in the order you see them on your system. (may be BIOS related, idk)
See this: [http://www.linuxquestions.org/questions/showthread.php?p=2283784](http://www.linuxquestions.org/questions/showthread.php?p=2283784)

it appears i've run afoul of a particular bug.  

[https://launchpad.net/distros/ubuntu/+source/grub/+bugs?field.searchtext=sata](https://launchpad.net/distros/ubuntu/+source/grub/+bugs?field.searchtext=sata)

the first two posts there (the "confirmed" ones) are the issue, i think.

the bug described is that grub mis-assigns SATA drives.  the solution given at the bottom of the first of those threads is to correct the /boot/grub/device.map; i did that, but i  still have an issue.  where i'm at with this now is pretty much the same as my last post, only now i'm better informed about it.  but what it comes down to is this:

```

grub> root (hd0,0)
Error 21: Selected disk does not exist
grub> root (hd0,1)
Error 21: Selected disk does not exist
grub> root (hd1,0)
Error 21: Selected disk does not exist
grub> root (hd1,1)
Error 21: Selected disk does not exist

```

and so on--i've tried every combination using 1-5 in both places, up to (hd5,5)--same error every time.

any tips would be greatly appreciated. :)

autrui

---

### Post by zerotwooneone on 2008-04-24
> and so on--i've tried every combination using 1-5 in both places, up to (hd5,5)--same error every time.

I seem to remember a similar problem before. It took me a little while before I found the solution I needed. When you run the 'grub' command, try 'sudo grub'. I know admin privileges are assumed when working off a live cd, but for at least this command it is necessary. 

Hopefully this will aide future seekers since this thread is terribly old.

-good luck

---

