---
title: "[SOLVED] Post-Intrepid (8.10) upgrade thoughts and experiences"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by akelsall on 2008-12-17
I recently upgraded to 8.10 and wanted to share some of my experiences related to the upgrade. Before you start the upgrade, I **strongly** recommend you backup the following files (as these are files that you woud have typcially modified on your existing install and would want to restore after the upgrade):

```
~/.bash_aliases
~/.bash_profile
~/.bashrc
/boot/grub/menu.lst
/etc/resolv.conf
/etc/fstab
/etc/network/interfaces
/etc/dhcp3/dhclient.conf
/etc/vbox/interfaces  (this one only applies if your using VirtualBox)
/etc/udev/rules.d/20-names.rules  (this one only applies if your using VirtualBox)

```

In addition to this, if you don't have a separate $HOME partition in your existing install, you will want to backup all the files in $HOME (or at least those you can't afford to lose). Finally, you will want to backup the list of all installed packages so they can easily be restored. I wrote a script to do this and will post in the next couple of days (basically, it involves using the command "dpkg --get-selections", but there's more to it than that). 

Ok, now that you've backed up your important files, onto the install. During the initial part of the install, you 
will enter basic info such as language and time zone. Shortly after that is where the fun begins, with the partition 
editor (but no fear, it's pretty straight forward). This is where the output of /etc/fstab comes in handy:

> In the partition window, you will see all your existing partitions, but the labels won't be there. You will 
need to recreate the mount points manually for each partition you have on your existing system. Either highlight 
the partition you need to mount and click Edit, or just double-click it. A window will pop up giving you the option 
to specify the filesystem type (typically ext3, unless you need to create a Windows-compatible partition. In that 
case, you can format it as NTFS. I left all mine ext3, because in Linux, you can access a Windows drive and open 
files on that drive with no problem). In this same window, you will also have the option to format the partition. Do 
**NOT** check this box unless you need to format the partition. The only partition that I felt I really needed to format 
to get a clean install was my root partition (which in my case was /dev/sda1). It will automatically format the /swap 
partition. 

>  When you are creating your existing partitions, make sure you put the "/" in front of the partition name. For example, I had existing partitions of music and photography. While in the partition window and defining the mount point, I entered /music and /photography. Remember...everything starts from the root directory. If you forget to do this, you will get an error message, so don't worry too much. 

The first time I did the upgrade, I didn't set the mount points for my existing partitions during the install phase (noted above), so I had a slight "oh sh*t" moment when I first booted to my desktop, opened Nautilus, clicked on an existing partition, and didn't see any files. I then ran gparted and could see that several gig of each partition was in use, so I knew the data had to be there. It was then that I realized I hadn't defined any mount points for my existing partitions. So, I went back and did the install again, this time creating the mount points (as described above). 

Once you have everything set in partition window, just look over all the info displayed in the partition window and double-check EVERYTHING one more time (your partitions, the names assigned to the partitions, which partitions you've selected to be formatted, etc). Once your sure you have configured everything correctly, click OK (or it might say FORWARD) and it will create the mount points. Note that once you set all this up and click Forward, you will be given one final opportunity to abort the process, so don't sweat it too much.

> Sidenote: You will typically want to rebuild the mount points exactly as they were before (e.g. if /dev/sda7 was /music, then mount /dev/sda7 under /music). There are a couple of reasons to do it this way. First, chances are you defined a partition for a reason (to hold you music files, or photos). Second, you defined it with a specific size. If you reassign partitions during the upgrade, your files may not all fit in that partition). If you don't need some of the partitions you were using, now would be a good time to delete them&#8212;just highlight the partition and click Delete.

Once you boot into the new version of Ubuntu, you will probably want to restore all the files mentioned previously. Before doing this, backup the existing files you will be replacing so you have a way of falling back to the original files. 

> 
**[COLOR="Red"]WARNING[/COLOR]**: Make sure you modify the kernel version referenced in the file /boot/grub/menu.lst so that it references the new kernel image name.

---

