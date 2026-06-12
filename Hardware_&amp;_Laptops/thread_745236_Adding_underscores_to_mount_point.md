---
title: "Adding underscores to mount point?"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by Jayferd on 2008-04-04
I have a 250G Toshiba external USB drive named "OM".  It's been working fine, but lately it's been mounting at "/media/OM_" and "/media/OM__", "/media/OM___", and just this morning, "/media/OM____" (note the underscores).  I admit I haven't been very good about unmounting the drive before I unplug it, which I'm thinking could have caused the problem; but I haven't done an unsafe removal since it first mounted at "/media/OM_".

I tried setting the mount point to OM in the Properties menu (also tried using gconfig-whatever it was).

As a disclaimer, I'm running hardy beta, but I don't think this is an issue with hardy.  Also, I've had the drive for several months, and it works perfectly (it still mounts, after all).

Ideas?

---

### Post by itix on 2008-04-04
Could you post the output of ```
ls /media
```

---

### Post by Jayferd on 2008-04-04
Sure thing - the relevant entries are 

OM
OM_
OM__
OM___
OM____
OM_____
OM______

They're all there, but it won't mount to the same place twice.  ...and it adds a new one every time I boot.

---

### Post by itix on 2008-04-04
If it is every time you boot I suspect it is a bug. You see, the mount point specified to your device is most probably OM. Every time you shut down your computer, there is supposed to be code that removes the folder that your external drive was mounted to which is *media/"mount point"* where "mount point" is the mount point specified in the drive settings (right click => properties => volume tab => settings arrow => mount point). You can manually remove those folders by navigating to /media in the terminal ```
cd /media
``` and do ```
sudo rmdir OM
``` plus the specific number of underscores. 

The fact that it doesn't remove your mount points at shutdown is disturbing though. It might just be a bug in Hardy, but my western digital external hard drive works just fine. The mount point of my western digital is External, and if I add a folder to /media called *External* I'd b getting the underscore too.

What file system is your hard drive? Mine is ext2.

---

### Post by Jayferd on 2008-04-04
I think you're right here - I unmounted the drive, deleted all of the OM dirs (including OM itself), and remounted again.  It mounts to /media/OM, as expected.

Then I restarted, without manually unmounting the drive, and it mounted to /media/OM_.
It only "forgets" to delete the directory on shutdown, though, because if I unmount it now, the "OM_" folder disappears.

And the drive is formatted ntfs - I have a dual-boot setup, so I need Windows to read it, too.

---

### Post by itix on 2008-04-04
I understand, and fat32 is out of the question because of it's really old and useless specs. Is this a new problem? I mean, have it worked before on Ubuntu and if so, when did the problems occur?

---

### Post by seditiousmonkey on 2008-04-04
hey guys this is not much help but I am getting the same problem in hardy.  it seems to have only started recently for me.  can´t be specific but in last fortnight perhaps.

I have partitions labelled MediaDisk and BackupDisk and on restart they are mounted as MediaDisk_ and BackupDisk_ respectivly. 

Have tried manually deleting the original mount point ie. MediaDisk, however this only solves it for one reboot.

I´ll keep searching the forums/wiki for advice and get back to you if I solve this.

---

### Post by natedawg on 2008-04-04
I can confirm that this is a hardy bug. The problem started about two days ago right after an update. For now the only solution I have is to manually delete the folder before you shutdown. 
Hope this gets fixed soon.

---

### Post by Jayferd on 2008-04-04
@natedawg: Is there a launchpad URL for this yet?

@mods: there's probably a better location for this thread, but I'm not sure what it is.

---

### Post by noynac on 2008-04-04
Same problem here. For example, I have a USB flash drive named FLASH and the media directory contains:

FLASH
FLASH_
FLASH__
FLASH___
FLASH____

I also have two external USB hard drives with FAT32, NTFS, and EXT3 partitions, and the situation is the same with them. I never had this problem before.

---

### Post by Jayferd on 2008-04-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/212085](https://bugs.launchpad.net/ubuntu/+bug/212085) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Filed a bug on Launchpad.

---

### Post by bren on 2008-04-05
i get something similar to this when i mount my IPOD to amarok multiple times in Gutsy

---

### Post by itix on 2008-04-05
Why is mine the only drive that works here??
I have tried to understand lauchpad, but I haven't really understood it yet, so if someone could check it for me, I'd appreciate it.

---

### Post by itix on 2008-04-05
Great. Then it will probably be fixed soon.

---

### Post by itix on 2008-04-05
Uuuhh.... Do any of you guys have write properties to your drives??
I can't create folders except via the terminal, and I cant paste files either. In other words, I have no write properties unless I use sudo via the terminal. Without sudo, the terminal gives me 'permission denied'-error.

---

### Post by Jayferd on 2008-04-06
no write permissions?  That's really weird.  I think they updated gnome-mount and a bunch of weird stuff happened.  I think there's a way to give yourself write permission with sudo chmod, but I'm not sure how...  Anyone?

---

### Post by itix on 2008-04-06
It's really no major problem... I don't need it right now, but I will need it in the near future when my Asus Eee finally arrives.

---

### Post by p.herewini on 2008-04-08
Yes I have the "appending underscore" problem too! 

For me this only came about after manually setting the volume label in the command line with e2label. I did this because I couldn't find anywhere to do this in gnome gui. Before manually setting the label it (exernal USB ext3 HDD) was mounting to *disk* or *disk-1*, depending in what order i plugged in my drives and I needed a consistent mount point for Rhythmbox.

Also on Hardy Beta, but again... this only started after setting volume label.

UPDATE:
I just checked the folders under /media/ and there was in fact "appended underscore" folders for a volume which I hadn't labeled manually.

---

### Post by itix on 2008-04-09
Ok... this is sick. I just updated and thought: yes, they've must have fixed my problems with the external, but instead it added your problem to those I already have.

I posted a lauchpad bug report about my wrtite properties problems and the underscore problem.

---

### Post by noynac on 2008-04-09
The workaround in post 15 of the following thread is a temporary solution:

[http://ubuntuforums.org/showthread.php?t=744469](http://ubuntuforums.org/showthread.php?t=744469)

This issue is being worked on and has a "high" importance:

[https://bugs.launchpad.net/ubuntu/+bug/101845](https://bugs.launchpad.net/ubuntu/+bug/101845)

---

### Post by itix on 2008-04-09
Does that give me write properties to or is it just a workaround for the the mount points??
Appreciate the effort though. Thanx.

**EDIT:** No need to answer. Found out the answer myself.

---

### Post by dngpng on 2008-04-11
This bug is filed here: [https://launchpad.net/bugs/212278](https://launchpad.net/bugs/212278)

---

