---
title: "Trust, but verify..."
date: 2013-01-15
forum: Hardware
---

### Post by Karl10 on 2013-01-15
Hi everyone

I'm in the process of backing up everything to an external hard drive (1TB), and all "appears" to be going smoothly, but... I'm suspicious by nature, and I'd like to be dead certain that the files that appear to be on this drive ARE on this drive, and not in some cache somewhere, waiting to be actually written.  It'll be too late once I've nuked my install and upgraded to the newest version of Ubuntu, only to find a blank formatted disk, or just a few cryptic files.

I've tried to mount SmartMonTools, but it won't install (the resource is no longer there, system can't find the files, not in Synaptic Pkg Mgr, or in Ubuntu Software Ctr, nor in Terminal), so I can't use IT to verify a good, true write.

Tried to hook it up to an (eccchhhh) Win7 machine, but it won't display the drive in WinExplorer or anywhere else other than in Disk Manager;  It indicates it's existence, but that's it.  Can't do anything but display properties.

Too nervous to proceed until I can ensure the files will be there to be retrieved after upgrade.

Any suggestions?

---

### Post by ahallubuntu on 2013-01-15
Hmm.  What version of Ubuntu are you using?  I use SmartMonTools almost daily to check hard drives and have recently been doing new Ubuntu 12.04 LTS installs and have had no issues installing it.  I use the GUI interface called GSmartControl into SmartMonTools.  Close Ubuntu Software Center, synpatic if you have it installed, open a terminal, and type:

```
sudo apt-get update
sudo apt-get install gsmartcontrol
```

Of course, if you are using an unsupported, old version of Ubuntu, the repositories may no longer be accessible and you may not be able to install.  You could always download the source and build it yourself (I have done that).

And with an external hard drive you'll most likely need to issue extra options like

-d sat

and/or

-T permissive

to smartctl to get it to find the USB drive.

Still, SmartMonTools only checks the S.M.A.R.T. health of a hard drive - very useful, but that does nothing to check the file structure, which is what you probably are most worried about here.  If the partition is ext3/4 you can always un-mount it and run

```
sudo e2fsck /dev/sdb1
```

(replace "sdb1" with whatever your partition really is on the external drive) You can force a check of the filesystem if it says "clean" but beware that this could take a while to run.

Finally - try rsync in "dry-run" mode to compare the original that you copied and the new:

rsync -av --dry-run /original/directory  /media/EXTERNAL/directory

(replace "EXTERNAL" with whatever the mounted name of your external drive is)

This doesn't copy anything but shows you what would happen if you wanted to (get rid of the --dry-run switch to copy for real).   If you copied everything correctly, you shouldn't have any files listed by rsync at this point.

Depending on how you copied the files, the file creation times may not match between original and the copy.  You can issue the option --size-only to compare without checking times.

---

### Post by Karl10 on 2013-01-15
Oooofff... yeah, that would have been a useful piece of information.  Running 10.10.  

Did the "sudo apt-get install" thing (after running sudo apt-get update).  Claims it can't find some of the repositories, though it does find a lot in general.  It can't find the repositories for SmartMonTools.

The e2fsck command lectures me on correct usage.  Dumped that after five or six tries, using different switches (options).  Disk Utility pronounces the file system clean (almost instantaneously).

Hmmmm... there should be a way to verify data integrity on a drive... more google is in order.

---

