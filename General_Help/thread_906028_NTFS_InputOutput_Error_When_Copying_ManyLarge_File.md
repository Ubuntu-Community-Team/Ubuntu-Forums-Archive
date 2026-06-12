---
title: "NTFS Input/Output Error When Copying Many/Large Files"
date: 2008-08-31
forum: General Help
---

### Post by Altay_H on 2008-08-31
I've been having a strange issue with my external hard drive. I backed up most of my personal files to this drive before switching from XP. I can read and write from the drive without an problems at all in Vista. In Linux, I can also read and write to/from the drive without any problems after it auto-mounts.

However, when I attempt to copy large files/folder from it, partway through the process it fails with an Input/Output error. When I attempt to access a location on the drive with Nautilus (after the error) it also gives me an Input/Output error. My device no longer appears in /media, but it remains mounted (and its icon remains on my desktop). I can remove it with sudo umount /media/SimpleDrive despite the fact that Nautilus shows no such location.

After unmounting, if I unplug the drive and plug it back in it automounts to /media/SimpleDrive_. I can copy about 800 MB per mount (though it varies considerably), but this makes it quite painstaking to transfer all 50 GB of my files. Any suggestions or help is greatly appreciated.


Note: This problem only happens when copying files from the drive. I've watched some movies that I have stored on the drive without any issues at all. Also, using the cp command in the Terminal results in the exact same problem (I/O error).


It looks like [this thread]("http://ubuntuforums.org/showthread.php?t=821876&highlight=NTFS+input+output+error") has a similar problem.

---

### Post by Exry on 2008-12-09
Hi Altay_H!

I just experienced the exactly same problem while I wanted to backup some data from my home dir. My external drive is a NFTS drive with lots of file son it, so I can't re format it without loosing old, but still not unusable.

So my question to you is: Did you find any solution on this?

Best regards,
Exry

---

### Post by Altay_H on 2008-12-11
Hey Exry.

I'm afraid I haven't found a solution. I was just forced to copy the files part by part. I still haven't finished copying them over, actually. If I find a solution I'll post it here, but I don't have many ideas.

I wonder if it might be hardware-specific. Is your external hard drive a SimpleTech too, or is it a different brand? I have two external hard drives now, so I'll test the newer one and see if it has the same problem.

I have final coming up this week, so I probably won't try it out for another week or so.

---

### Post by hhhzzz on 2009-01-18
i am having the same problem. i suspect it has something to do with corrupted source hard drive.

i wonder if there's an option to force copy and ignore errors?

thanks

---

### Post by dtm32236 on 2009-05-15
I'm having the same exact problem and have tried everything I've found out there. I've read that disabling ACPI may work, but that didn't fix it.

Has anyone found a solution to this?

---

### Post by at78rpm on 2009-06-01
Same problem here.  I thought it might be restricted to Intrepid, but I formatted the ext hd in jaunty, and tried copying both from an Intrepid box and from a Jaunty one, with the same effect: can't copy larger files.  It seems to stick somewhere around 25 MB, and then the icon for the drive disappears.

This is the kind of thing that keeps the general public away from Ubuntu.

---

### Post by zjagannatha on 2009-07-11
I'm having the same issue trying to copy files from an older CD with a few backup files on it.

I tried the normal:
```
cd /media/cdrom/folder
sudo cp * ~/folder
```
When that didn't work I tried to force it:
```
sudo cp -f * ~/folder
```

When I used 'ls -l' to list the contents of the directory, it listed them, but I was unable to open one of the text files with gedit. It gave me this error in terminal:
```
** (gedit:6072): WARNING **: Hit unhandled case 0 (I/O error) in parse_error.
```

I tried copying the files with 3 other computers. All computers could access the CD-Rom, but not the subfolder, they seemed to just hang when I opened the subfolder. (I tried it on Mac OS, Windows XP sp 3, and my own computer, Ubuntu Jaunty 9.04)

The fact that all three computers could not open the same files makes me think they were corrupted, but the fact that I could list the specifics of the files made me suspicious that it was some other problem.

Any help appreciated,
Thanks

---

### Post by Cl0ud9 on 2009-07-11
I suggest making sure the problem isn't with the cp command. Try using rsync
```

rsync -av source destination

```

---

### Post by zjagannatha on 2009-07-11
> **Cl0ud9 said:**
> I suggest making sure the problem isn't with the cp command. Try using rsync
```

rsync -av source destination

```

I tried using rsync as you suggested. It gave me the same Input/output error as before:
```
rsync: read errors mapping "/media/cdrom0/Docs+Settings/.../file": Input/output error (5)
```

---

### Post by spxavales on 2010-06-26
Same problem here.
I have an external ntfs hard drive and i want to make a backup in my /home folder.
I tried to copy and paste(manually/using terminal/...) all the folders that are stored in my external hd, unsuccessfully.
Then i tried [THIS]("http://ubuntuforums.org/showthread.php?t=35087") but for some files i get the "Input/Output Error".
For some reason these files can't be copied and i don't know why!
Please HELP!

---

### Post by zjagannatha on 2010-06-26
I eventually decided my files were corrupt and gave up on it. This was also almost a year ago, so I don't even have the CD anymore.

You might want to be sure there are no disk errors on the hard drive.
*fsck* is the program to do that, but you'll need to find out what the device you want to check is. Something like "/dev/sda1" or "/dev/hda0"

then run:
```
fsck /dev/sda1
```
or whatever the device was.

---

### Post by zzarko on 2010-08-14
I had similar problems (copying big files from/to external drive) several years ago, but the problem was manifesting in both Linux and Windows on 3 out of 4 computers I tried (strangley, it worked fine on one computer). It was external drive made by Intex. I returned the drive, got another one - same problem. Then I returned that one too, and asked for another manufacturer. I got Coolink (or something like that), and no problems at all since then. I guess that was hardware problem and back then there were several manufacturers that used same electronics in their external drives (with same problems). I also have good expiriences with Chieftec and Transcend external drives. Western Digital should be OK too.

---

