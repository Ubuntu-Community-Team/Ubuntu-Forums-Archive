---
title: "Upgrading from Windows 7 to Ubuntu 9.04"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by MajorBurton on 2009-06-30
Alright. so I'm installing everything, everything is going fine, but I have one snag- when making the partitions for the drive, it says it'll delete windows vista (loader), which is 363 something gb's. What I'm wondering is if you can upgrade from windows to ubuntu without having any of your files deleted, but rather have them transferred from one OS to the other- and if this is possible, how would you go about doing it?

---

### Post by zoomy942 on 2009-06-30
depends.  are you wanting to keep your windows install and dual boot?  are you wanting just a ubuntu PC?  answer that and everyone will have several different approaches for you

---

### Post by MajorBurton on 2009-06-30
Ubuntu only- my version of windows seven expires tomorrow, and I've been waiting for an excuse to make the change to ubuntu only

---

### Post by zoomy942 on 2009-06-30
Fair enough.  Ubuntu thinks it has a migration assistant but i have never had it work right.  What i do personally, is boot into windows, copy everything from my c:\users\<name> folder onto a thumbdrive and the just install ubuntu and move everything into the appropirate folders in ubuntu.

its funny becasue i went from windows 7 to ubuntu 9.04 also.

[http://ubuntuforums.org/showthread.php?t=1200677]("http://ubuntuforums.org/showthread.php?t=1200677")

---

### Post by MajorBurton on 2009-06-30
I would do that, but my main problem is I'm using up 310 gb's of my 400gb hard drive- I suppose I could take what I really need, and then redownload everything that I've already downloaded, but that would be quite the bitch

I'm also confused because I'm doing the demo of ubuntu 9.04 right now, and HP (My main hard drive) shows up on the desktop- I think maybe I'll try to just drag and drop and then install as I normally would

---

### Post by zoomy942 on 2009-06-30
wow!  thats a ton of data.  how much of that is programs and things like that?  or is the vast majority of that actual files like movies and pictures and music?

---

### Post by MajorBurton on 2009-06-30
I've got about 25gb of music, a couple gigs of pictures, and like 80 or 90 moves at 700mb a piece, so about 60gb of movies- and 100 something gigs of programs and program data- I can redownload all the programs, considering I downloaded them in the first place, but a lot of them took several days to complete- maybe I'll write a bunch of it to disks and transfer it that way

maybe I'll try using or downloading a migration assistant, or something to that degree

---

### Post by zoomy942 on 2009-06-30
well, with those programs, why keep them?  they arent going to work in ubuntu anyway.

---

### Post by MajorBurton on 2009-06-30
that's true- I'm mainly concerned about all my music, movies and documents- everything else is sort've pointless

but the problem with all of that is the massive amounts of each of those that I have

---

### Post by AoSteve on 2009-06-30
Personally, best bet in my opinon.  Get another drive.   What you do from there is run the windows drive as a slave and install ubuntu on your new master.  I have a working copy of WinXP in a virtual box for my "window needs" and with guest additions it's a seamless window.   You could use that to get to your files through network sharing and sharing folders.  :)

You already have a TON of data on that drive, why run the heck out of it and risk losing it all when it could be sitting there idle most of the time? :)   I won't build another system without a storage drive to store all my important stuffs.

---

### Post by merlinus on 2009-06-30
You can shrink your current windows partition to make room for installing ubuntu.  Since it is probably formatted as ntfs, linux can read and write to it.

If you do so, delete the paging file (if one even exists in win7) and then defrag several times, and use its disk management tool to shrink the partition.

Then after installing ubuntu you can delete the registry and other system files from windows, and will have even more room.

---

### Post by MajorBurton on 2009-06-30
too late now- I saved all my important files and have started formatting and partitioning the new drive

if it's true that you need to delete something 7 times to permanently erase it from the hard drive, I may be able to recover files that I lost- I've done it before with windows drives, and managed to recover some of my old files off an old, formatted and corrupt hard drive- so hopefully it all works out in my favor

---

### Post by Mark Phelps on 2009-07-01
> **MajorBurton said:**
> if it's true that you need to delete something 7 times to permanently erase it from the hard drive ... 

Actually, if you're talking about MS Windows filesystems, "deleting" a file does not removes its contents from the disk, no matter how many times you do it.  What it does is mark the filesystem so that the space used by the file is available for reuse.

If you actually want to "remove" the contents of the file from your disk, and be sure that it's gone (as in not recoverable), you need to use one of the disk utilities that incorporates "wiping" (which is sometimes referred to as shredding).  These claim (which I haven't verified) to use a DES algorithm to overwrite the file contents repeatedly such that even forensic analysis tools can not recover it.

---

