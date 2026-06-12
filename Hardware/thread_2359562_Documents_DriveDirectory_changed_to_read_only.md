---
title: "Documents Drive/Directory changed to read only"
date: 2017-04-25
forum: Hardware
---

### Post by Jonners59 on 2017-04-25
In the last 3 days my Documents folder has suddenly changed to read only.  It worked fine before, for many years.  The directory is on a separate partition on a hard drive and is in NTFS so that it can be accessed by my Windows 10 install which is on a separate directory and option in GRUB.

The Directory is accessed via mount point [HTML]/home/baronipc/Desktop/Documents[/HTML]
I have tried the usual ```
sudo chown baronipc:baronipc -R /home/baronipc/Desktop/Documents
``` and ```
sudo chmod 777 -R /home/baronipc/Desktop/Documents
```

I have also created a temp mount point so I could change the [HTML]/home/baronipc/Desktop/Documents[/HTML] mount point permissions separately, but that, I find is already set to the above, 777 and baronipc:baronipc and makes no difference.

I have looked in fstab and made changes there following various blogs, inc changing NTFS to NTFS-g which I am not sure about as it may impact access via my Windows 10, though not sure how - perhaps someone could confirm that too, please?

Here are all the options in fstab I have tried:
```
#Entry for /dev/sda3 :#in Media - temp
#UUID=2104697C2776893B	/media/Documents	ntfs	defaults,uid=baronipc,umask=000,windows_names	0	0


#####in Desktop/Documents
#UUID=2104697C2776893B	/home/baronipc/Desktop/Documents  ntfs        defaults,uid=baronipc,umask=000,windows_names	0	0


#UUID=2104697C2776893B	/home/baronipc/Desktop/Documents  ntfs        defaults,nls=utf8,umask=007,gid=46                     0      0


#UUID=2104697C2776893B	/home/baronipc/Desktop/Documents  ntfs        auto,users,permissions                                          0      0


UUID=2104697C2776893B	        /home/baronipc/Desktop/Documents  ntfs-3g   defaults,uid=baronipc,umask=000,windows_names	0	 0


#UUID=2104697C2776893B	/home/baronipc/Desktop/Documents  ntfs-3g   defaults,nls=utf8,umask=007,gid=46                      0      0


#UUID=2104697C2776893B	/home/baronipc/Desktop/Documents  ntfs-3g   auto,users,permissions                                           0      0

```

Linux baronipc-System 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Can anyone help me, please????

---

### Post by yancek on 2017-04-25
If it had been working for some time it should continue unless some change was made or you are having a hardware failure.  Do you notice any other problems which might be related to a hardware problem?  Did you make any changes prior to this happening, particularly to the parent directories?  Very non-standard location for a windows partition mount point.  Usually this is done in /mnt or /media.   Windows filesystems do not use or understand Linux permissions. You need to use umask/dmask.  Did you leave windows hibernated before booting back into Ubuntu?

---

### Post by ajgreeny on 2017-04-25
It is possible, I think, that there has been an update to your Windows system, particularly if Windows 10, that has turned fastboot or faststart back on after you had turned it off in the BIOS/UEFI settings.

Check that first, though it will normally mean that the ntfs partition is completely inaccessible to Ubuntu not just read-only.

---

### Post by Jonners59 on 2017-04-25
Thanks guys.....

Just tried this, in fstab.  Gives all the right messages and ownership, but still does not work.  Says that the directory is "Read only".
```
UUID=2104697C2776893B	/home/baronipc/Desktop/Documents   ntfs-3g rw,uid=1000,gid=1000,dmask=0002,fmask=0003 0 0
```

yancek
Nothing changed and nothing unusual, well, that said Dropbox stopped working and so did my Virtualbox, but I suspect that is because the directory is not working/RW even though it says it is.  And yes, for some it is, but it puts it inside what appears to be home.  Works or did work for me.

[COLOR=#000000]ajgreeny[/COLOR]
> [COLOR=#000000][INDENT]**It is possible, I think, that there has been an update to your Windows system, particularly if Windows 10, that has turned fastboot or faststart back on after you had turned it off in the BIOS/UEFI settings.**

Check that first, though it will normally mean that the ntfs partition is completely inaccessible to Ubuntu not just read-only.
Now, that is interesting, and may have some possibility, though, when that first happened it affected GRUB and would ONLY boot in to W10, until I went in and changed it.  But I have had a few updates/upgrades there, so worth checking.  What does worry me though is that I took a snapshot and Save state of one of my virtual machines using W10, and maybe that has locked it.  That is VERY worrying if it is the case as it won't open since the situation.[/INDENT][/COLOR]

---

### Post by Jonners59 on 2017-04-25
> **ajgreeny said:**
> It is possible, I think, that there has been an update to your Windows system, particularly if Windows 10, that has turned fastboot or faststart back on after you had turned it off in the BIOS/UEFI settings.

Check that first, though it will normally mean that the ntfs partition is completely inaccessible to Ubuntu not just read-only.

BRILLIANT.  That was the answer.  I booted up the Windows 10 from GRUB and changed in settings, when I went back in to Ubuntu it was PERFECT again...  THANK YOU!!!!!

---

