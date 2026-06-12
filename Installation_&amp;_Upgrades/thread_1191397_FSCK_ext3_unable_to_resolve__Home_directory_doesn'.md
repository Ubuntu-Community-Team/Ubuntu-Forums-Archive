---
title: "FSCK ext3 unable to resolve : Home directory doesn't appear to exist : dmrc ignored"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by ProgressionMurph on 2009-06-18
Hello Everyone,

I'm having a few of problems.

    This is how the problem started.  I had ubuntu installed on my machine but I wanted to dual boot.  Prior to uninstalling ubuntu I used simple backup restore and used the recommended settings.  However, instead of saving it to the recommended folder I saved it to my external Hard Drive.  When the backups were complete and on the hard drive I was unable to access them due to permissions.  Unfortunately  my hard drive had to be reformated.  I reformated my hard drive and installed vista.  I than installed ubuntu.  After installing ubuntu I used add/remove programs and acquired backup restore.  I used the program backed up the files.  After that I restarted my computer and encountered the following problems.
 
"Fsck.ext3: Unable to resolve 'UUID=206fb5e0-5c86-4719-a61a-a98519a93a9f'
fsck died with exit 8 status
file system check failed
checking filesystems....
147"
 
**I have to use control D to continue to try to fix the problem.  And I can only use Failsafe Terminal, the Failsafe session doesn't work**
 
"Your home directory is listed as: '/home/alex' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session."
 
"User's $Home/dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users."
 
 
  I appreciate any insight from anyone into were to begin.
 
Cheers,
Murph

---

### Post by quixote on 2009-06-19
When you say you used "simple backup system" do you mean you used the program called "Simple Backup"?  If so, it backs up all your files as "root" which means when you're an ordinary user, eg logged in as "alex", you can't do much with them.  Which kind of defeats the purpose of backup :( .  Also, your home dir is owned by the user, but since SB is trying to do everything as root, that sets up conflicts too.  The long and the short: don't use SB if that's what you're using.

If you recover the system so that you have a desktop again (see next point) you should be able to access previous SB backed up files as root.  Try ```
gksudo nautilus
``` and see whether that helps to get at them.  If it does, the next step is to change ownership on them, but first let's see whether it helps.

To solve the more important fsck problem:  That error 8 means the bootloader can't find the kernel (the guts of the operating system that it needs to boot).  Possibly, the reason is because that interminable UUID is wrong somewhere.

Follow the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to help grub find things again.  

If nothing helps, can you post the output of: ```
sudo fdisk -l
``` that's "l" as in list. (If you're running from the recovery, ie root, console, you don't need the "sudo".)  That lists your drives and partitions.

I suspect the problem isn't as bad as it looks.  Everything looks like it's there, just the OS can't find it.  All we need to do is point it in the right direction again.

---

### Post by quixote on 2009-06-19
More info from a search on your error message found [here]("http://kubuntuforums.net/forums/index.php?action=printpage;topic=3098172.0"):> When you format a partition, it changes the UUID number.

So, you need to run
Code:

sudo blkid

and then fix /etc/fstab 

Again, you don't need the "sudo" if you're running from the recovery or root console.  "blkid" lists the UUIDs for the various partitions.

Then run ```
sudo nano /etc/fstab
``` and VERY CAREFULLY make sure the UUIDs from blkid match what's listed for the given partitions.  Don't make any typos because it'll cause problems a lot like the ones you have now.

Nano is a command line editor.  No mouse.  You have to use the arrow cursor keys to move around.  When you're ready to save, it's Ctrl-x, and then "y".

---

### Post by ProgressionMurph on 2009-06-19
Much Appreciated!  I'll give it a try and respond with the progress =)

---

### Post by ProgressionMurph on 2009-06-19
I no longer receive the fsck died with exit 8 status.  I have a MBR problem that I'm going to attempt to fix.  I can log in now and see the desktop.  All my files from my backup are on this computer however the desktop remains to look like a brand new fresh install and when I go to add/remove programs it shows a list of my previously installed programs from my backup however, when I try to find them under applications they cease to be there.

---

### Post by hbost on 2009-08-01
I have same issue and have tried the solutions on this forum and not much success.  I have fixed GRUB (both with tty and GUI from live CD) and have updated Ubuntu packages with apt-get.  

I have two 750G Seagate drives running raid 1 on an old Dell Optiplex. All was fine until I rewired my house and the Dell sat idle for 2 months.

On reboot, I get the same FSCK.ext3 died with error status 8 message.

When I run blkid, I get ID numbers for sda1, sda2, sda3 and md0.  However, when i try to edit /etc/fstab, the only ID numbers are md0, md1, md2, etc.

Clearly, I have a partition and/or GRUB problem, but not savvy enough to figure it out.

One data point that may be material is that I originally had an Ubuntu 8.04 LTS install and was using PC as a desktop.  I bought a new PC and moved the Dell to a file server and installed Xubuntu to save resources.  When it worked, it was the cheapest, fastest file server around.  However, I think this double install has screwed up GRUB.

I guess I could do a full new Ubuntu install, but I am very nervous about my files (pictures and songs) and settings and worried that I may overwrite them. 

Any help appreciated.

---

### Post by hbost on 2009-08-01
I hope that the problem is solved.

After chasing my tail for two days, I grabbed the original Xubuntu SERVER (I didnt realize it was the SERVER version) disk, booted it up, selected "rescue broken system", went through a couple of setup screens and simply re-installed GRUB.  No partition issues, no FSCK issues, booted right up.

I guess it helps to understand exactly what you have loaded on your system!!  I also should have known that I was using the incorrect LiveCD as the other CDs did not have the "rescue broken system" option...

Thanks for help.

H

---

