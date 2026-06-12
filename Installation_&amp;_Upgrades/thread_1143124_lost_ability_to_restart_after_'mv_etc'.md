---
title: "lost ability to restart after 'mv /etc/'"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by silbar on 2009-04-29
Greetings,

This is complicated and maybe only appears as interesting to certain experts in boot problems.  I am running Hardy with Gnome on a Dell Inspiron.  Because of something I must have done, I can no longer restart my machine into linux.

This is what I _think_ I did to make this happen:

After backing up my /home/silbar/ directory onto a Jaz drive, I also decided to update the copy on that drive of the /etc/ directory.  First thing I did was move the old /etc/ into the trash on that Jaz disk.  Unfortunately, that copy has since been empty from that trash.

As silbar (myself) I found I did not have permission to drag /etc/ onto the Jaz drive.  So I 'sudo su'd to become root.  I then typed, in the tty,

     mv /etc /media/disk

Oops!  This generated a whole lew of error messages.  But it did copy (some?) things from /etc/ onto the Jaz disk, however as the contents of /etc/, not as a directory icon named 'etc'.

OK, to recover from that, I then sent the many /etc/ files and directories on the Jaz drive to (its) trash.

OK, a better way (I thought) was to make an archive of /etc/ (still as root at /):

     tar -cf etc.tar etc

This worked, and I could move that etc.tar onto the Jaz drive without problem.

BUT, I now noticed that I no longer could connect to the net.  There no longer seemed to be a DNS server the machine could access.  This has happened to me before, and would be fixed with a restart.  So, I told the machine to restart.

That's when I found it can't reboot (into linux -- I can still get, I supposed into Windows XP, but I haven't tried it).  The reboot process stops somewhere along the way.

I can insert the Ubuntu 8.0.4 CD and boot up from it into a LiveCD session.  (Did need to add the 'noapc' and 'nolapic' options to the boot-up line to do so).  

The /home/ directory on the Dell is on a separate 50 GB partition (/media/disk-2) and the rest of / is on another 50 GB partition (/media/disk-3).  So, I can compare the contents of the CD's /boot/ directory with that on /media/disk-3.  They appear to be the same.

Similarly, a quick look at comparing the various /etc/rc* files in the two places shows that there are MANY differences.

OK, I am at a loss as to what to do next.  Thanking you, anyone, in advance,

   Dick Silbar

---

### Post by bowens44 on 2009-04-29
If I am reading this correctly, you moved (mv does not copy, it moves) your /etc directory off of your PC and then deleted the files that were moved. The /etc directory contains your configuration files. Your PC will not be able to boot from this installation without these files. Unless I'm mistaken, and I may be, you are pretty much out of luck. You will have to re-install if you don't have a back up.

---

### Post by silbar on 2009-04-29
[QUOTE=bowens44;7179113]If I am reading this correctly, you moved (mv does not copy, it moves) your /etc directory off of your PC and then deleted the files that were moved.

Yikes! -- I know (knew) that!

What would happen if I copied (cp) all the files from the Ubuntu into the /media/disk-3 /etc/?  There are many files there having to do with apps that I've installed after the initial installation.

Dick Silbar

---

### Post by upchucky on 2009-04-29
hopefully you have a backup of your home partition, if true the reinstall and restore the home partition

you never need to mv any system files unless you are bored and love to play hide and seek with your system.

sudo is a powerful command option and is there to protect you from your hidden self. evil laugh here.....

when you have a separate home partition all your files and system settings for each particular user are stored there, thus they are restored when you restore the home partition.

the etc folder is the core settings of linux and need not be played with unless you like that kind of thing.

it is best to re-install since there is no way of knowing exactly which files need to be fixed.

---

### Post by silbar on 2009-05-02
Upchucky was quite right.  I have now gone through the re-install process
(and downloaded 326.5 MB of updates over a slow DSL line to do so).

My self-suggestion

> **silbar said:**
> 
What would happen if I copied (cp) all the files from the Ubuntu into the /media/disk-3 /etc/? 

did not work, as my user name did not appear in the resulting /etc, just someone named "ubuntu".

Thank you both, Bowens44 and Upchucky

---

