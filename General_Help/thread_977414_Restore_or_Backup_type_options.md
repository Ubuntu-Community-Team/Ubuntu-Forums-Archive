---
title: "Restore or Backup type options?"
date: 2008-11-10
forum: General Help
---

### Post by Jamtarts on 2008-11-10
Hi, 

Firstly sorry if the thread is in the wrong place,

I currently have a Dual Boot Desktop with three drives, Ubuntu 8.10 as my main computer installed and running pretty well on a 500gb drive, Vista installed for games on a 250gb drive, and a 120gb drive for storage.

I hope to shift the drives around now to re-organise, so as Ubuntu barley registers on the 500gb I was looking to put Vista on this as my games have pretty much swallowed the 250gb drive, I would like to use the 250gb drive as a storage drive so that my files are easily accessable on both operating systems and independant of either drive and finally install Ubuntu back on the 120gb drive as I don't need as much space for this,

I am really happy with my ubuntu set up (other than a couple of wee niggles) and if possible I would like to keep the current set up intact.  It would take a long time to get all back up to how I had it.

I  was wondering if there was any way of backing up my Ubuntu drive's files, then doing a fresh install onto the 120gb drive and restoring the backed up files to give me my old system back, would this work given the difference in drive sizes or can this be achieved using any other methods?

thanks in advance,

Richard

---

### Post by scouser73 on 2008-11-10
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by cdtech on 2008-11-10
Sure, you could use the "Live gparted CD" to copy the partition to another location.

You would need to use the "Live CD" because the drives can not be mounted during the process.

You could also use the "dd" command if you want. (check out the link in the sig)

---

### Post by geirha on 2008-11-10
Copying the ubuntu install from one filesystem to another will work, but requires a bit of editing grub config and /etc/fstab. I think the easiest option would be to boot up an ubuntu CD, run gparted and shrink your ubuntu partition. Then in windows, make a partition of the empty space and use it to install games on etc.

Make sure you backup important files from the ubuntu disk before you attempt to resize it with gparted.

---

### Post by Jamtarts on 2008-11-10
Brilliant guys!

thanks very much, I'll have a go at that,
:)

---

