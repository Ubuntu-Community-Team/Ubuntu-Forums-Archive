---
title: "Ubuntu to recover files?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by fighter36 on 2009-04-06
Hello,

My wife's laptop crashed on the weekend and I tried everything to get it going again. It had Win XP on it. The main concern is she didnt backup recently and she needs several important files of the harddrive. after all recovery efforts failed a friend reccomended Ubuntu. 

He told me to run it off the CD and go in and manually get the files. It booted up successfully, but i got an error when i tried to access the hard drive. It said it couldnt mount the hard drive as it was unproperly shut down last time windows was run. Seeing how I cant shutdown properly is there anyway around this?

If I install Ubuntu on the harddrive will it delete all the old files (format)?

Thanks for any info. This is a cool little OS.

):P

---

### Post by upchucky on 2009-04-06
there is a utility package in linux called libntfs it has a program called ntfsfix that will get the windows shutdown problem fixed.

ntfsfix does not actually fix inconsistencies but it cleans the NTFS filesystem Journal which enables the partition to be mounted again and able to read/write with ubuntu.

Also Knoppix is an awesome repair live cd that can rescue windows systems that are taken down either by viruses or the self destruct mode that microsoft thinks should be there. 

all her files will be there, don't panic don't install anything until you have recovered the files.
good luck

---

### Post by fighter36 on 2009-04-06
wow. great advice. thanks for the info. :)

---

### Post by fighter36 on 2009-04-06
any idea on a Linux Live CD that has the utility with it? I tried Knoppix and couldnt find it or anything similar. 

THanks again for your help. I am actually glad this happened, I had no idea these little operating systems where out here. I have been having fun checking them out :)

---

### Post by Bearly Able on 2009-04-07
OK, I'm not an expert on this, but the packages you want seem to be on the Ubuntu Live CD.  I'm running Ubuntu 8.04 Hardy Heron, and happen to be using the Live CD at the moment because of another problem.  libntfs is showing as installed, as is a package called ntfsprogs, which says it includes ntfsfix.  Unfortunately, I've never used these utilities, so can't advise you how to do so; I'd guess you need to run them from a terminal.  (Applications > Accessories > Terminal).

To see what software is installed in Ubuntu, go to System > Administration > Synaptic Package Manager.  Items marked with a green square are already installed on your system; in the case of a Live CD, I take it that these are available to run.

Sorry I can't be more help to you, but at least you can stop looking for the utilities - you already have them.

---

### Post by fighter36 on 2009-04-07
thanks very much! I will take a look.:p

---

### Post by fighter36 on 2009-04-07
I found them! 

but not sure how to use them. hehe. any ideas?

i tried exec ntfsfix but nothing happened. sorry. i am a noob at linux.

---

### Post by tlois on 2009-04-07
When you try to access the hard drive and it tells you it wasn't shut down correctly, there should be instructions under it showing you how to force mount in terminal I think.  Did you try that?  Also, I think Unetbootin may have some restore software too.  I'll check and get back.  We were def able to get at our hard drive though when a windows machine crashed doing the force mount.

---

### Post by tlois on 2009-04-07
If all else fails I just remembered how I got my stuff from an accidentally formatted backup hard drive (doh!).  It says for accidentally deleted, but would maybe work for that too.  At least bookmark it- these are great tools to know about.


[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)


Editing to say:  and tomorrow install Ubuntu permanently on at least a partition of that drive!

---

### Post by tlois on 2009-04-07
More- go to the section where he shows how to force mount. this worked for us for sure and we were able to back all important docs up to flash drives.  


[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

---

### Post by iponeverything on 2009-04-07
> **fighter36 said:**
> I found them! 

but not sure how to use them. hehe. any ideas?

i tried exec ntfsfix but nothing happened. sorry. i am a noob at linux.

Identify the partition with the command "sudo fdisk -l"

Say your NTFS partition shows up as /dev/sda1,
repair it with: 

"sudo ntfsfix /dev/sda1"

---

### Post by fighter36 on 2009-04-08
awesome! thanks guys. appreciate all the help!

---

