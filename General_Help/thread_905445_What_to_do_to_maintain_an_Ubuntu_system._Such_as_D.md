---
title: "What to do to maintain an Ubuntu system. Such as Disk Defrag/Scans/Cleanup/Etc."
date: 2008-08-30
forum: General Help
---

### Post by _Atreides_ on 2008-08-30
Hey guys, now that I have my ubuntu system for the most part up and running I was wondering what general maintenance tasks one does for a linux system. I know Linux is not Windows but I am just trying to cover all the tracks. For example on Windows you had:

[LIST]
[*]Disk Defrag
[*]CCleaner
[*]or Disk Cleanup
[*]Etc.
[/LIST]

Thanks!

---

### Post by fjgaude on 2008-08-30
The way Linux manages files it doesn't require defragging. Just don't load the disks to more than about 90% full. It is especially true if you have huge files, like movies. A small amount of fragmentation is okay.

Also keep the Trush empty as much as possible.

That's really it. Even viruses don't seem to show up.

---

### Post by exploder on 2008-08-30
You can clean up your apt cache by using this command.

sudo apt-get clean

Enter your password.

---

### Post by RequinB4 on 2008-08-30
ubuntu's default partitioning system doesn't have the same errors windows does (In windows, it picks any random slot of memory, and when it is erased, you have sections of writeable memory you can't use between ones in use) hence you don't need to defrag it. (more technically, some can occur, but it is handled more efficiently...)

But that's in case you cared.  The answer is that you DON'T have to defrag the drive if you're doing normal desktop operation :) But if you *really* want to, and risk breaking stuff, here you go: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

The default ubuntu installation automatically checks your primary partition for integrity every 30 boots or 30 days.

Don't worry about antivirus in linux: there is clamav if you're running a mail server or something that does a LOT of automatic filesharing with a lot of windows boxes. iptables (frontend Firestarter) provides a firewall you won't need unless you open a port in your box (but might be good to have just in case if you can spare the cycles)

Basically, the best thing you can do is to update your system to remove security vulnerabilities, and don't do generally stupid things with security :lolflag:

---

### Post by oldos2er on 2008-08-30
> **_Atreides_ said:**
> Hey guys, now that I have my ubuntu system for the most part up and running I was wondering what general maintenance tasks one does for a linux system. I know Linux is not Windows but I am just trying to cover all the tracks. For example on Windows you had:

[LIST]
[*]Disk Defrag
[*]CCleaner
[*]or Disk Cleanup
[*]Etc.
[/LIST]

Thanks!

 If you use ext3, defrag is not needed, as long as your partitions are less than 90% full. I don't know what "CCleaner" does, could you explain?

 The contents of /tmp are automatically deleted on reboot. Also, fsck (file system check) is run every 20 - 30 boots, to make sure your FS is healthy. You can run it manually in the meantime if you choose.

 There is a program in the repositories called "fslint" that can check for bad symlinks, bad IDs, empty directories, etc., that you might want to have a look at.

---

### Post by mb_webguy on 2008-08-30
As the others have said, Linux does pretty much everything for you.  

The ext3 filesystem doesn't get fragmented, so there's no need to defrag.  

Linux doesn't really get viruses, though there are virus scanners available (including clamav and [AVG Free]("http://free.avg.com/ww.download?prd=afl")) if you're worried about spreading them to Windows computers.  

You can run "sudo apt-get autoremove" occasionally to remove packages that are no longer needed and free up (a small amount) of drive space (though if you need to do this, you will be informed of it when you install a package using apt-get).

You should update your system regularly, but the Update Manager will automatically check for updates for your system and installed software, and let you know when they are available.

And... um, that's about it.  Linux is really not anywhere near as high-maintenance as Windows.

---

### Post by Vivaldi Gloria on 2008-08-30
See my post here:

[http://ubuntuforums.org/showthread.php?t=903493](http://ubuntuforums.org/showthread.php?t=903493)

---

### Post by WRDN on 2008-08-30
For routine maintenance, I just run the following commands:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

```

For conveniance, I put them all in a shell script, so I only have to enter my password, and the cache is cleared, then the package information is updated, the packages are upgraded and any unneeded packages are removed.

---

### Post by HermanAB on 2008-08-30
You should not need to do anything at all.  Linux can be zero maintenance.

Most Linux problems are caused by upgrades, so I don't upgrade my machines either.  Once they are working I leave them alone and install a new version of Linux after a year or two.

Cheers,

Herman

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by gabhla on 2008-08-30
Been eight years since I had Windows - but, gosh, I hated the fluff I had to go through just to maintain the system.  Only maintenance required is the keep the system updated, keep the trash emptied and occasionally do an apt-get autoclean.

---

### Post by Ms_Angel_D on 2008-08-30
> **WRDN said:**
> For routine maintenance, I just run the following commands:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

```

For conveniance, I put them all in a shell script, so I only have to enter my password, and the cache is cleared, then the package information is updated, the packages are upgraded and any unneeded packages are removed.



Could you share the script that you use sounds like a good idea but I don't know anything about scripts..lol..

Thanks,
Angel

---

### Post by WRDN on 2008-08-30
> **MetalHellsAngel said:**
> Could you share the script that you use sounds like a good idea but I don't know anything about scripts..lol..

Thanks,
Angel

Sure. This is the script:

```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```

Just save that in a file called [name].sh (you can replace [name]).
It performs the maintenance jobs, and finally, removes the sudo privileges (sudo -k). Now, right click on the file, select Properties then the Permissions tab. Finally, select "Allow executing file as program".
This can also be done in the Terminal, by typing:

```
chmod +x [name].sh
```

---

### Post by Ms_Angel_D on 2008-08-30
Thanks a bunch :) WRDN!!

---

