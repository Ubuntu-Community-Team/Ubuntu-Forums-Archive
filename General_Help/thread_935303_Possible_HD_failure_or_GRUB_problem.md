---
title: "Possible HD failure or GRUB problem"
date: 2008-10-01
forum: General Help
---

### Post by ks07 on 2008-10-01
Hi everyone,
I dual boot Ubuntu and Windows XP. I got Ubuntu 8.04 about 2 weeks ago along with a new HDD to install it on so there was no chance of breaking my XP install with re-partitioning. Everything was working fine until yesterday when on selecting to boot in XP I got a 'Disk Read Error'. I restarted and got a registry error, so next boot I went into Ubuntu. From there I could not mount the hard disk. 

After that, I restarted again and got into Windows. I thought everything was fixed, but just to be sure I enabled SMART in the bios to check my drives. No errors reported, a small utility I downloaded showed 100% health (unlike my new drive :s). Anyway, I used both XP and Ubuntu succesfully for the rest of the day, until I booted up this afternoon. I got another read error when booting XP, so I restarted, got in and ran a chkdisk /f. It found some corrupted files and fixed them, restarted the PC and then XP worked fine... until I rebooted to go into Ubuntu. 

My PC will not load GRUB anymore. It just displays Grub Loading Error Stage 1.5 (or something similar). I managed to load GRUB and get into my Ubuntu install using the Live CD and choosing "Boot from first hard disk". Ubuntu cannot see the original HD anymore in "Computer" or using fdisk -l.

Is this bad news - a.k.a hardware failure? Or could I have overlooked something really simple? Luckily, I have a fairly recent backup of my personal files. Unluckily, this PC is a package PC and comes only with a hidden restore partition and a restore disk. Have I lost Windows for good now? DX Anybody have any advice on saving the system? 

(Just realised I wrote an entire essay. :P)

---

### Post by briandu on 2008-10-01
i would first boot up ubuntu and open a terminal session and run update-grub. Start from there.

---

### Post by ks07 on 2008-10-01
I can now boot into Ubuntu normally, awesome! Thanks for that. My XP partition is now showing, but unmountable (the still in use error). I'll try booting XP now, see if it has fixed itself. XD

---

### Post by briandu on 2008-10-01
there is an issue that comes up every now and then with Win XP if accessed from Linux. Are you doing this?

---

### Post by ks07 on 2008-10-01
Yeah, I've been copying files across from XP to Ubuntu every now and then. I guess that wasn't the brightest of ideas.

---

### Post by briandu on 2008-10-01
you can and it is ok to do so. make sure u have ntfs-3g installed and u can mount the file system. I do all the time.

note: i mean open terminal then paste:

sudo apt-get install ntfs-3g

inset password and good to go!

Hopefully your XP is working?

---

### Post by ks07 on 2008-10-01
Okay, XP booted succesfully :) so I'm just gonna hope it stays that way. I think I'll leave the Windows partiton alone in Ubuntu from now on. It's easier that way, imo.

Thanks for the advice, appreciate it! :D

---

### Post by ks07 on 2008-10-02
Scrap that - XP was working fine, until it froze while I was browsing the web. I had to hard reboot it, and I came back to where I started. Yet again I can no longer boot into XP and I cannot mount the Windows drive.

Anybody else have any ideas? I'm starting to lose hope now :(, but at least I can boot Ubuntu (most of the time). :-|

---

