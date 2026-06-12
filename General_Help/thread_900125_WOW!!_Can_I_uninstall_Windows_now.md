---
title: "WOW!! Can I uninstall Windows now?"
date: 2008-08-25
forum: General Help
---

### Post by Kelly Roberti on 2008-08-25
I have just installed Ubuntu 8.04.1 using WUBI. Is there a way that I can uninstall Windows XP completely and keep my Ubuntu intact?

---

### Post by Orlsend on 2008-08-25
I am thinking is not possible using "Wubi" since its needs windows to work.

---

### Post by ad_267 on 2008-08-25
From: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> 
How do I migrate to a real partition, and/or get rid of Windows entirely?

Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

As an alternative, the following script can be used with Wubi 8.04.

Download wubi-move-to-partition

Open a terminal and run:

sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10

Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually. 


After you've done that I think you could then remove your Windows partition and resize your Ubuntu one to fill the whole drive. I haven't tried this myself though.

---

### Post by Kelly Roberti on 2008-08-25
I will give it a look...thanks for the response.

---

### Post by Crafty Kisses on 2008-08-25
Sure, Administration > Partition Editor.

---

### Post by forger on 2008-08-25
Since you have just installed it.. why not boot from the live CD and install it again? Saves you a lot of trouble :)

---

### Post by Kelly Roberti on 2008-08-25
I want to save all of the customizations I have done...and just move on without MS XP...I have no CD...I did a download wubi

---

### Post by forger on 2008-08-25
Then you haven't *just* installed it (no offense)
I'd still go by reinstalling normally if I were you, unless you don't want to download and keep a useful CD

---

### Post by forger on 2008-08-25
I can give you this hint though, if you want to keep your customisations:
1) keep a backup of the contents of /home/yourusername folder ("your home" folder) :)
When you're done installing the new user (preferrably the same username), just copy the contents of the folder back in home.
Note: Press CTRL+H in nautilus(=the file explorer program) - it will show you the "hidden" folders with customisation files for programs

2) do this command in terminal (Applications > Accessories > Terminal):
```
dpkg -l | grep '^ii' | tr -s ' ' | cut -f 2 -d ' ' > /tmp/pkgdump.txt
perl -e '$splitevery = 30; open(F,"/tmp/pkgdump.txt"); @a=split(/\n/,join("",<F>)); $x=0; $b=""; foreach $i (@a) { $b=$b." $i"; $b =~ s/^\s//; if ($x == $splitevery) { push(@final,"$b\n"); $x=0; $b=""; } $x++; } open (DEST,">/tmp/pkgdone.txt"); print DEST @final;'
cp /tmp/pkgdone.txt ~/packagefiles.txt
```

It will create a packagefiles.txt in your home folder, which contains all your package applications that are currently installed

You can save that file and use it later to re-download your applications with this command:
**[COLOR="Red"](WARNING: Can break stuff!)[/COLOR]**
```
sudo aptitude install `cat packagefiles.txt`
```

---

