---
title: "Problem with external hard disk"
date: 2011-01-08
forum: Hardware
---

### Post by Kalamaius on 2011-01-08
Sorry for bad english i'm italian. I have a problem with my hd 1tb... I have ubuntu 10.10 but i can't mount my hd 1tb. I used the hd with windows 7 but know I've only Ubuntu. when i try to mount my hd, it appears the following error: Failed to mount '/dev/sdb1': Argomento non valido
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
I try to use my hd on windows 7 from a friend and it works fine. In my ubuntu doesn't works. I try also with the comand line sudo mount -t ntfs-3g /dev/sdb1 /media/elements -o force, but the result is negative. I'm reading a lof of guides, forums etc. but I don't find a good solution for my problem. Someone suggest me a formatting, but i have a lot of very important files on my hd and i would like to avoid this drastic method. Someone please can help me with a good explanation and a detailed one?

---

### Post by oldfred on 2011-01-08
Linux & gparted will often not mount a NTFS partition that needs chkdsk. I had no trouble booting my XP which was on sda, but gparted would not even see sda at all. I ran chkdsk and then it worked. So I would try chkdsk from windows repairCD first.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If your sdb1 is the full 1TB it may take a very long time.

---

