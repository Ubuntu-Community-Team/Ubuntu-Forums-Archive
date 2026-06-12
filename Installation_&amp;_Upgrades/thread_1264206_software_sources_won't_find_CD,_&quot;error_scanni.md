---
title: "software sources won't find CD, &quot;error scanning the CD&quot;"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by junaigr on 2009-09-11
Hi, I'm new to Ubuntu and Linux in general.  I installed 9.04 on my laptop inside of Windows (so it dual-boots) and would like to install some packages from the cd, as the computer does not have an internet connection currently.  I do:

System -> Administration -> Software Sources -> Third-Party Software -> Add CD-ROM...

And I keep getting the error "Please insert a disk in the drive:"

When I hit enter, I get a screen saying "error scanning the CD, E:Failed to mount the cdrom".

Any help would be greatly appreciated!  Thanks in advance.

---

### Post by thegreatsnafu on 2009-09-12
Hi,

Try mounting a different CD. If it doesn't work, then your CD-ROM drive might have some problems with Ubuntu.

---

### Post by leonbravo on 2011-03-15
I have the same issue even though, my cdrom is mounting with the command mount -o loop. Yes, it is not an actual CD. I'm following the instructions to upgrade with Upgrading Using the Alternate CD/DVD. 

It still tries to connect to the internet!

---

### Post by Bill Gates Foundation on 2012-03-03
12.04

> Open up Synaptic Package Manager
    Settings > Repositories > Other Software, then add the following:
    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main
    “Reload” the package list
    Find “pm-utils” then go to Package > Force Version.. and select 1.3.x
    Install the downgraded package
    Find “pm-utils” again, go to Package > Lock Version

when i hit add, it says 

error scanning the cd

can nopt find suitable cd

---

### Post by oldos2er on 2012-03-03
Please start a new thread for your question; and if it's about 12.04, post it here: [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

