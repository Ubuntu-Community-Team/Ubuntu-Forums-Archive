---
title: "Can't boot to different HDD"
date: 2009-01-23
forum: Hardware
---

### Post by bigstiffy on 2009-01-23
The new computer I got before christmas had nothing installed on its hard drive, so I installed ubuntu on it, now, after I installed it, I took out the hard drive and hooked up my old hard drive that had XP, but my pc would not boot to it. I didn't think much of it so I hooked up my ubuntu drive again and didn't mess with it for a while. Well today I had taken some time to work on it and hooked up both hard drives, went into my bios settings, and set my xp hard drive as the first in the boot sequences, closed out of bios and started to boot up, but my pc started with my ubuntu drive. Confused, I went back into bios and disabled my ubuntu drive so it would boot to XP, but then it booted to ubuntu again. Even more confused, I went to the boot menu at startup and selected my XP drive... and it booted to ubuntu. After that I was tired of trying through bios and boot menu so I logged into ubuntu and saw that my old hard drive was visible and I could read all the files in it. So, any idea why I couldn't boot to my XP drive, or how I can boot to it?

---

### Post by sowelie on 2009-01-23
Sounds like the MBR on your windows drive is gone.  I would recommend setting up grub so you can select XP.  I can't remember exactly how to do it, google ubuntu dual boot grub or something along those lines.

EDIT:

Searching for ubuntu grub add windows yields better results, such as:
[http://ubuntuforums.org/showthread.php?t=192435]("http://ubuntuforums.org/showthread.php?t=192435")

---

### Post by bigstiffy on 2009-01-24
Well, I tried adding it to the grub menu using the example as reference, [IMG]http://ohsnap.freezoka.com/ddddd/23.jpg[/IMG], however, when I tried booting to it, I got this [IMG]http://ohsnap.freezoka.com/ddddd/24.jpg[/IMG] I wasn't too sure what this was so I didn't try to continue, but I had to press 'N' 4 times before it would exit.
This is what I had added to my menu file:

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

So, is there something I can add that could resolve this issue?

---

### Post by sowelie on 2009-01-24
You need to figure out which disk / partition windows XP is on.  I would guess that your issue is that it is not finding the correct drive.  Run this command to find the correct drive.

```
sudo fdisk -l
```

In your menu.list for windows xp, you denote the drive by hd0,0.  This would be the first drive, first partition.  hd0,1 would be the first drive, second partition, hd1,0 is the first drive first partition etc.

---

### Post by caljohnsmith on 2009-01-24
I think it would help to first get a clearer picture of your current setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by bigstiffy on 2009-01-24
> **sowelie said:**
> You need to figure out which disk / partition windows XP is on.  I would guess that your issue is that it is not finding the correct drive.  Run this command to find the correct drive.

```
sudo fdisk -l
```

In your menu.list for windows xp, you denote the drive by hd0,0.  This would be the first drive, first partition.  hd0,1 would be the first drive, second partition, hd1,0 is the first drive first partition etc.

I tried what you said and this was my result:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59917   481283271    7  HPFS/NTFS
/dev/sdb2           59918       60801     7100730    7  HPFS/NTFS

```

I also tried caljohnsmith's suggestion and ran the boot info script, this was the result:

```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```
So instead of having the root as "(hd1,0)" I should have it as either "/dev/sdb1" or "/dev/sdb2"?
EDIT:
I added this to my grub menu in hopes that it would work:
```

title                Windows XP Professional
root                (hd1,0)
savedefault
makeactive
chainloader        +1
map (hd0) (hd1)
map (hd1) (hd0)

```
but like my previous edits, it gave me the same "BootSector Write!! VIRUS: Continue (Y/N)?" error, I tried continuing anyway, and I got another error. "NTLDR IS MISSING PRESS CTRL-ALT-DEL TO RESTART" Then I just about got stuck not being able to boot to ubuntu since it went to that message before the grub menu, but I went into bios and set my ubuntu hard drive as the first in the boot sequence and that fixed it. Now what should I do?

---

### Post by sowelie on 2009-01-27
I think you have it right, hd1,0 should be correct.  Although, I'm a bit confused, why are your linux partitions not showing??

I think the issue you need to focus on is the "BootSector Write!! VIRUS: Continue (Y/N)?" message.  A quick check in google would lead me to think you need to check your bios settings and disable virus checking in the BIOS.  Then, I'd recommend running a virus scanner once you finally do get into Windows.

---

### Post by bigstiffy on 2009-01-30
> **sowelie said:**
> I think you have it right, hd1,0 should be correct.  Although, I'm a bit confused, why are your linux partitions not showing??

I think the issue you need to focus on is the "BootSector Write!! VIRUS: Continue (Y/N)?" message.  A quick check in google would lead me to think you need to check your bios settings and disable virus checking in the BIOS.  Then, I'd recommend running a virus scanner once you finally do get into Windows.
My linux partitions did show in the result, I only copied the windows part of the results. I did, however, go into bios and look for anything that controlled virus checking, but I couldn't find anything. I'll have to look again, but the bootsector write error wasn't the worst error.
"NTLDR IS MISSING PRESS CTRL-ALT-DEL TO RESTART" is the real problem as it prevents me from doing anything but restarting. A little googling revealed that its a problem from trying to boot from a non-bootable source, so now I've gotta make a boot disk or put the bootable files onto my drive with xp on it.

---

