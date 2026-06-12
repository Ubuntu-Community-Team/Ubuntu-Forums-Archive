---
title: "Unclean Shutdow - Duplicate or Bad Block in use"
date: 2009-11-23
forum: Hardware
---

### Post by patmartha on 2009-11-23
Hi, I could really use a hand. I'm in China, and I don't have a CD to reinstall my OS, nor do I know much about how to work out this issue. My computer has had problems shutting down recently, so I've been doing it manually; holding down the button until it shuts off. This was fine, until it started scanning drives. Usually I just pressed "esc" to skip the drive scan. However, now it forces scan and I get these error messages and I am unable to get to start up the computer.
 
The computer will begin to load, but stops at 70% (stage 1/5, 2259/2259)
 
if I load from recovery mode, I get to following:
 
 
Unclean shutdown; checking drives 
/dev/dsa6 contains a file system with erros, check forced.
Duplicate or Bad Block in use
 
I've messed around a little and also discovered these error messages:
 
Could not start the X server (your graphical environment) due to some internal error. Please contact your system admin or check your syslog to diagnos. Please restart GDm when the problem is corrected. 
 
and 
 
 
/dev/sda6: (There are 2 inodes containing multiply-claimed blocks.)
 
/dev/sda6: File /patmartha/.snes96_snapshots/Alien 3.001 (inode #26565507, mod time Thu Nov 19 20:12:19 2009)
 
has 1 multiply-claimed block(s) shared with 1 file(s); /dev/sda6: /patmartha.tomboy/addins/Tomboy. addins (inode #26738793, mod time Nov 19 19:47:42)
 
/dev/sda6: Unexpected Inconsistency; run fsck manually (i.e., without -a or -p options)
fsck died with exit 4 status
File system check failed. A log is being saved in /var/log/fsck/checkfs if that location is writable. Pease repair the file system manually.
A maintenance system will now be started.

---

### Post by prezbedard on 2010-02-20
I know this is a few months old however I believe I just experinced the same thing. It happened after booting back to Ubuntu from XP. I have a dual system Ubuntu 8.04 LTS and XP. I ran the fsck as it said and it clicked Y to fisk or clear at all the prompts. My system is now back up and running. I'm still not sure what happened. I have been going thorugh the logs but nothing stands out.

---

