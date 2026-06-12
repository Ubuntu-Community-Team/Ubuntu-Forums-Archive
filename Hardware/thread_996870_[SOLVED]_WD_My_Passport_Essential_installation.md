---
title: "[SOLVED] WD My Passport Essential installation"
date: 2008-11-29
forum: Hardware
---

### Post by Pablo W on 2008-11-29
Hi, I'm a 100% newbie, no idea of Linux at all, and just having my first steps with Ubuntu. I have Ubuntu 8.1. I bought an external My Passport Essential drive of 250 GB. I plugged it and I got a message saying that that drive contains auto executable software and it asks if I want to run it. I've aswered no, and then I see the  drive which already contains a series of files and folders such as autorun, WDsync, etc.

I want to use this drive for backup and for sharing files with computers at work which run on Windows.

 Here come the questions:

1: Should I delete all those out of the box files?

2: Will I be able to use the files I save in the Passport drive from my Ubuntu at home when I try to see them in Windows PCs and vice versa (will I be able to save files from Windows and open them at home with Ubuntu) or there is any kind of formatting I should do before storing files? 

Thanks for your help,
Pablo.

---

### Post by Pablo W on 2008-11-29
Hi, I'm a 100% newbie, no idea of Linux at all, and just having my first steps with Ubuntu. I have Ubuntu 8.1. I bought an external My Passport Essential drive of 250 GB. I plugged it and I got a message saying that that drive contains auto executable software and it asks if I want to run it. I've aswered no, and then I see the  drive which already contains a series of files and folders such as autorun, WDsync, etc.

I want to use this drive for backup and for sharing files with computers at work which run on Windows.

 Here come the questions:

1: Should I delete all those out of the box files?

2: Will I be able to use the files I save in the Passport drive from my Ubuntu at home when I try to see them in Windows PCs and vice versa (will I be able to save files from Windows and open them at home with Ubuntu) or there is any kind of formatting I should do before storing files? 

Thanks for your help,
Pablo.

---

### Post by ugm6hr on 2008-11-29
I got my Passport last year, so I presume this applies now...

WD Passports are formatted as fat as default, so work fine on Windows / Mac / Linux.  No need to do anything special.  Tryt and make sure you unmount before unplugging though.

Your choice whether you keep the WD autorun software.  I deleted them.  They are only useful if you want to use the WD Windows backup software.  If you want, you could just put that software within a folder to prevent it from annoying you each time you plug it in.

---

### Post by Pablo W on 2008-11-29
> **ugm6hr said:**
> I got my Passport last year, so I presume this applies now...

WD Passports are formatted as fat as default, so work fine on Windows / Mac / Linux.  No need to do anything special.  Tryt and make sure you unmount before unplugging though.

Your choice whether you keep the WD autorun software.  I deleted them.  They are only useful if you want to use the WD Windows backup software.  If you want, you could just put that software within a folder to prevent it from annoying you each time you plug it in.

Thanks, ugm6hr.
 That answers my question; very useful. I will start saving files from my Ubuntu at home then, and come back in case I have problems on Monday opening them from the work PC runing on Windows ;)

Cheers.

---

### Post by Pablo W on 2008-11-29
I again,

Now that I know there is nothing special I should do before storing files in the Passport drive, I have two further related questions (being so happy with the quick reply I got, I left them out of my previous post):

1: Is there any easy-to-use back up application that I can run in my home PC running Ubuntu 8.1? Again, I'm a newbie.

2: The wire provided with the Passport drive is quite thick, but very short. Since I cannot use it (it's too short and I would leave the drive hanging from my computer), I am using a similar wire which came with my Canon camera. This wire is longer, but also thinner. Is there any danger in using such a wire instead on the original one?   

Thanks for your patience,

Pablo.

---

### Post by finito on 2008-11-29
> **Pablo W said:**
> I again,

2: The wire provided with the Passport drive is quite thick, but very short. Since I cannot use it (it's too short and I would leave the drive hanging from my computer), I am using a similar wire which came with my Canon camera. This wire is longer, but also thinner. Is there any danger in using such a wire instead on the original one?   



if you are talking about the USB wire, then there is no problem.

as for back up try this [HTML]http://andri.dk/en/tech/linux/usb-backup[/HTML]

---

### Post by ugm6hr on 2008-11-29
USB cables are interchangeable (as long as all pins are connected - which will be the case for one that came with a camera).

Backups in Ubuntu: There is no easy answer to this, since there are numerous options.

I use grsync, which is a simple GUI for rsync.  Unfortunately, it doesn't allow scheduled backups.

Many people use rsync alone (with or without cron to schedule regular backups).

The benefit of rsync-based methods is that no compression is used, so retrieving individual files is easy.

As far as I know, most other options use compression.

The s in sbackup stands for "simple" - but I have never tried it.

There are other options too, but I can't remember them all - try googling backup ubuntu.

EDIT: I have just looked at finito's link - it looks like an automated rsync script.  If it works, it looks like an excellent solution.  I don't know enough about scripting to check it out myself, but the comments look positive.

---

### Post by Pablo W on 2008-12-03
> **ugm6hr said:**
> USB cables are interchangeable (as long as all pins are connected - which will be the case for one that came with a camera).

Backups in Ubuntu: There is no easy answer to this, since there are numerous options.

I use grsync, which is a simple GUI for rsync.  Unfortunately, it doesn't allow scheduled backups.

Many people use rsync alone (with or without cron to schedule regular backups).

The benefit of rsync-based methods is that no compression is used, so retrieving individual files is easy.

As far as I know, most other options use compression.

The s in sbackup stands for "simple" - but I have never tried it.

There are other options too, but I can't remember them all - try googling backup ubuntu.

EDIT: I have just looked at finito's link - it looks like an automated rsync script.  If it works, it looks like an excellent solution.  I don't know enough about scripting to check it out myself, but the comments look positive.

Thanks ugm6hr and finito for your useful answers. As for using the Passport in Windows and Ubuntu, I had no problem whatsoever. I've saved files in my Ubuntu at home and opened them at work from Windows with no problem. I could not open my back-uped pst files in Windows , but I think that is not relevant for this thread.

As for the backup, I'm afraid finito's useful suggestion goes way beyond my knowledge of Linux. Being a beginner, sentences like "Download the two files and put them in the appropriate places" make not sense at all yet. So I started by taking ugm6hr's suggestion (grsync). By the way, I also found [this thread]("http://ubuntuforums.org/showthread.php?t=35087") on ubuntu backup (it has 77 pages!) that I will read carefully.

---

