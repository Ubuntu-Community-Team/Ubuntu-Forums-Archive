---
title: "Formatting USB disk with Fdisk"
date: 2015-06-26
forum: Hardware
---

### Post by A Traveller on 2015-06-26
Hi all.

[http://ubuntuforums.org/showthread.php?t=267869](http://ubuntuforums.org/showthread.php?t=267869)

I have been following the instructions at the above link to format a new USB hard disk. When I try to copy/cut and paste a file onto the new disk, the 'paste' option is greyed out, so I assume I need to follow the following steps as outlined in the thread.

You may need to make a single folder in the new drive and give it your user permissions:
cd /media/sda1
sudo mkdir afolder
chown you:you afolder

Where you insert your username and desired folder name as appropriate.

Before I carry out the above, I am unclear about what this means. Firstly, I assume my username is the name I log onto my PC with. If this is correct, does this mean that I will only be able to access files/save files on the drive from my own current PC?

Thanks.

---

### Post by yancek on 2015-06-26
Formatting drives in a Linux system requires root privileges which is why the 'paste' option is greyed out now.  If you run the commands suggested to make a directory or directories then change ownership, you should be able to use it.  The 'chown' command also needs to be preceded by 'sudo'.  The user name is the primary user you created when installing the system.  As to accessing it from other computers that will depend on which operating system and filesystem you use on the other computer(s) but you should be able to use it.  You may need to make similar changes on the other computer.

---

### Post by sudodus on 2015-06-26
If you run Ubuntu (desktop) as indicated by the Ubuntu flag of this thread, you have a graphical desktop environment, and ***gparted*** is much easier and therefore safer to use compared to fdisk (and parted and other command line tools). 'You see what you do' :-)

gparted is directly available in the Ubuntu live alias install systems, and you can install it to an installed system via the Ubuntu Software Center or

```
sudo apt-get install gparted
```

Run it from the dash or with the command line

```
gksudo gparted
```
or
```
sudo -H gparted
```

---

### Post by A Traveller on 2015-06-26
Thanks for your reply yancek.

I pressed Alt+F2, typed 'gksudo nautilus' and then tried to copy the file to the USB disk and surely, the 'Paste' option appeared and I was able to paste the file onto the USB disk, however, I am now unable to remove the file (using 'Cut') from the USB disk. It is telling me I don't have permissions. I then tried to delete the file but it is telling me I don't have permissions and I also cannot delete the .Trash-0 folder it has created. If sudo has allowed me to put a file on, why can't I remove it?

I have formatted many disks before but I have never had to make a folder/allow user permissions before. Is this because this is a USB disk and the others were internal?

Are there any other steps that I could have done during the formatting process that would have meant I didn't have to carry out the extra step of making a folder and allowing user permissions?

When you say that I would need to make similar changes on the other computer, what do you mean? I don't intend to use it on any Windows PC but what would I need to do if I plugged it into another Ubuntu PC which has a different username or change my username on my pc?

Sorry for the many questions but I am very confused.

Thanks.

---

### Post by sudodus on 2015-06-26
What file system is it?

Linux has 'full control' of linux file systems, but Windows file systems, FAT and NTFS, get the permissions for files and directories when mounting, and cannot be changed without re-mounting with other permissions. Often, but not always, if you unmount or 'eject', unplug and re-plug a USB drive, it will automount in a consistent way, so that you can write and delete either with normal privileges or with superuser privilegss.

What do you want in this case?

Maybe you should change the permissions of the 'mother' directory, where it automounts, and those permissions will be inherited. Different versions of Ubuntu behave slightly differently.

---

### Post by A Traveller on 2015-06-26
Hi sudodus. Thanks for your reply.

I'm using ext4.

I do not want the disk to automount as I will do that via the software which I will use to encrypt it.

Thanks.

---

### Post by sudodus on 2015-06-26
I think the solution depends on the software which you will use to encrypt it. Maybe it is worthwhile learning the command lines (in a terminal window) for making things work, and keeping those commands in a file, a ***shell-script*** file. Then you just run that file every time to prepare for the system.

---

### Post by A Traveller on 2015-06-26
Hi sudodus. Possibly VeraCrypt.

---

### Post by oldfred on 2015-06-26
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Whenever I create a new ext4 partition I run both chmod & chown commands. My example mount is /mnt/data, but mount can be anything you want if manually mounting. The /mnt will not directly be shown in Nautilus left panel, so you may want /media. I use /mnt for my data and do not want it Nautilus, so I have to drill down from computer to mnt to my data.


 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by A Traveller on 2015-06-26
Hi oldfred.

Thanks for your reply. Unfortunately, the info provided is beyond my knowledge at the moment.

I ended up trying the original chown instructions and got an 'Operation not permitted' error.

---

### Post by A Traveller on 2015-06-26
Thanks for all the replies.

I couldn't get it to work using fdisk so tried Disk Utility instead and everything seems to work fine now.

---

