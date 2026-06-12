---
title: "Reinstalling on another HDD (best practice?)"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Ashocka on 2009-06-23
Hi,

I have some mapping problems at boot that I can't solve.  It doesn't initialize $HOME properly, but except for only some things not finding $HOME (properly), everything else is okay.  But I am going to reinstall on another HDD so I don't wipe the current install 9.04/64 so I can use the apt-cache.

I'm just wondering about best practices for managing multiple HDD... where should things be stored, what to mount, etc, etc.  

One thing I can't find is my Synaptic configuration file which stores what apps I have currently installed.  Can anyone please help me on that and how to just copy it from one install to another.

I someone can point me to some examples I'd appreciate it a lot.

---

### Post by Herman on 2009-06-23
Installed packages are stored in /var/cache/apt/archives, and you can make a backup of all the packages in /var/cache/apt/archives and paste it into another /var/cache/apt/archives in another installation of the same version of Ubuntu so you won't have to re-download the same packages again from the internet.

You might run this command in your new installation
```
sudo dpkg --list >> installedI.txt
```Now you will have a list of the software that comes with a new installation.

You might run this command in your old installation
```
sudo dpkg --list >> installedII.txt
```Now you will have a list of the software that comes with a new installation plus the software you added yourself.
Copy the installedII.txt text file you just made into the new operating system.

When you have the two text files beside each other and you want to know what apps to install, 
```
diff installedI.txt   installedII.txt >> addedsoftware.txt
```

Then,
```
dpkg --set-selections < addedsoftware.txt
```

```
sudo dselect
``` and select '**i**' for install the software. 

NOTE: I haven't tested this myself, or at least not recently, but it should work, refer to the links below,

[LIST]
[*][http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html) 
[*][http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html) 
[*][http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/) 
[/LIST]
 
[B]
[/B]

---

### Post by Ashocka on 2009-06-23
Thanks Herman,

The command line help works great.  I couldn't get Synaptic to produce the logs from GNOME though.  Doesn't matter.

Thanks
Geoff

---

### Post by Herman on 2009-06-23
'sudo dselect' didn't work for me, it gave me 'the package dselect is not installed, the following command is better,
```
sudo apt-get dselect-upgrade
``` > I couldn't get Synaptic to produce the logs from GNOME though. Oh, you want the Synaptic configuration file which stores what apps you have currently installed? Okay, you mean you're looking for a GUI method? 
:-k Hmmm . . . (thinking) . . .

---

### Post by Ashocka on 2009-06-23
Thanks.  Doesn't matter about GUI if I have the right command line info:-)

---

### Post by Herman on 2009-06-24
Oh, okay, good then.
> I'm just wondering about best practices for managing multiple HDD... where should things be stored, what to mount, etc, etc.  All I can say for sure is "Different things suit different people", and it depends on what you use your computer for.

Personally, I like to multi-boot so I can use the current up-to date version of Ubuntu while testing the newest version which is still under development and hasn't been released yet. 
At the same time, I'm reluctant to delete my older versions until they're really old and outdated. I also have a couple of other distros, Debian and Mint installed, just to compare the differences.  
I have two hard drives with just operating systems in them, and two hard drives containing only data so that I can easily access all of the same data from any of my operating systems.

One tip is to set labels on your file systems if you have more than just one or two partitions so you can identify which partition is which.
Setting a file system label is possible in GUI mode now, and it's quick and easy. Just open Gnome Partition Editor in your Ubuntu Intrepid Ibex and later Live CD and right-click the partition you want to set a label for and click 'Label', and give your file system a name. You can find Gnome Partition Editor in your Ubuntu Live CD under 'System'-->'Administration'-->'Partition Editor', and you can install it in your Ubuntu operating system with 'Applications'-->'Add/Remove (Programs)'.

The file system labels you set are useful for mounting purposes because the icons you see on your Desktop for mounted partitions will be named according to your file system labels. I have one partition labelled 'data' on one hard disk, and 'backups' in a different hard disk. Each of my Linux installations are labeled according to which distro or Ubuntu version is in the partition. The next version of Ubuntu, codenamed 'Karmic Koala', will have the newer version of GRUB, which will is able to read the file system labels at boot time from CLI mode, (if you have a few operating systems and you want to know which partition to chainload and boot).

It's a good idea to keep your backups on a separate hard disk from your data. I have a couple of different friends who I have installed new hard disks for. Hard disks can be damaged in laptops from accidental falls or user abuse. Even in Desktop computers, I have seen hard disks that just went dead because an electronic part under the circuit board suddenly fried. 

If you want, you can have your data partition mounted automatically at boot-up by listing it in /etc/fstab, [Edit /etc/fstab Method for Mounting]("http://members.iinet.net.au/%7Eherman546/p10.html#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu"). That's not as important these days as it used to be. With the modern versions of Ubuntu we only have to go 'Places'-->'Removable Media' and click on an icon to mount a file system. Before that we always needed to use Linux commands, but you still might find it convenient to edit /etc/fstab anyway.

I suppose I could sum up by saying your data partition can be automatically mounted by editing /etc/fstab if you like and your backups should be stored in a separate hard disk, or at least that's what I like to do.

That's all I can think of for now,
Regards, Herman :)

---

### Post by Ashocka on 2009-06-24
Hi Herman,

Thanks, this is really helpful. I've seen multiple boots, and the rest of it, but haven't delved into it because although I have used Linux on and off for a long time, I have never wanted to get caught in the complexities, and sometimes got myself into situations I couldn't get out of in the past.  These days, I think I can meet Linux in the middle, as it has come a long way and I'm prepared to set up a system where I can dual boot.

Unfortunately I can't abandon Windows as my Sony IC Recorder is only Windows compatible (and some other devices), but it is amazing what Linux recognizes these days.

I tried to reinstall Ubuntu 9.04/64 on another hard drive but it kept coming up with sector overflow errors, which puzzled me as this HDD seemed okay.  I could partition this drive, but I am going to get another large SATA drive and do some fresh installs on them.  I need to run CentOS from time to time to emulate my server on the net.

What I gather is you manage to put your /home data on another partition and configure all your distros to look for that at start up to initialize that as home.  Which makes things much more interesting.

---

### Post by Herman on 2009-06-25
> What I gather is you manage to put your /home data on another partition and configure all your distros to look for that at start up to initialize that as home. Which makes things much more interesting.No, nothing that fancy at all, I just have a simple data partition in a separate hard disk. All of my operating systems are installed in one partition each with their own /home directory, not a separate /home partition. I either click on the icon to mount my data partition when I want it, or I have in mounted on boot-up by a line in /etc/fstab.

I don't know anything about Sony IC recorders or sector overflow errors.

Anyhow, I'm glad you're enjoying Ubuntu. You're right, Linux has come a long way in a short time. Things have improved a lot since Ubuntu first started. It's getting easier and more user friendly all the time.

---

### Post by Ashocka on 2009-06-25
Great, I'll look at a few approaches to this.

> **Herman said:**
> Anyhow, I'm glad you're enjoying Ubuntu. You're right, Linux has come a long way in a short time. Things have improved a lot since Ubuntu first started. It's getting easier and more user friendly all the time.
Yes it has.  Been using RH/Fedora for a long time but it has become to clunky for my liking.  I used to have a Debian machine a log time back and it worked great... until I tried to install Java on it... this was back in the old days.

Nowadays there enough support both online and by the improved kernel detection of devices to make it much easier.  I was able to get my sound card going through a lot of searching and command line, so it's much easier these days.

Amazing the other versions growing out of ubuntu too, like Mint, MEPIS, Studio64, etc

---

