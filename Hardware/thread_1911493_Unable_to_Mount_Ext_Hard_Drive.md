---
title: "Unable to Mount Ext Hard Drive"
date: 2012-01-19
forum: Hardware
---

### Post by PicoDeRyo on 2012-01-19
I'm having difficulty mounting an external hard drive I have plugged in via USB. I am getting an error saying "Unable to mount 750GB Filesystem Not Authorized" I have searched the forums and have been unsuccessful. Your help is greatly appreciated. Below is what I have running

bourne@JonesMash:~$ sudo parted /dev/sdb print
Model: Ext Hard  Disk (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  750GB  750GB  primary  ext3

bourne@JonesMash:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b3cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       19458   156039169    5  Extended
/dev/sda5              32       19458   156039168   8e  Linux LVM

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732574552+  83  Linux
bourne@JonesMash:~$ 


Thank in advance

---

### Post by carl4926 on 2012-01-19
Are you actually using
Ubuntu 8.04 Hardy Heron  				 				 				 				 				?

---

### Post by PicoDeRyo on 2012-01-19
No I am using 10.04 Lucid, I tried to change my profile, but for some reason it wouldn't let me edit it.  It has been awhile since I used Ubuntu. I experimented with Hardy for awhile, and then had to go back to windows because I couldn't live without excel, but now I have a spare computer and I am trying to use it as a media server. This is the only problem I haven't been able to resolve by a search of the forums. any suggestions are very much appreciated

---

### Post by carl4926 on 2012-01-19
It should just mount on the fly.
Though it's some since I used 10.04
Test a new user login, just to make sure it's not some crud in your normal user profile

Test the 10.04 live CD
Attached USB HD should just mount
I'd consider using ext4 if you can

I have come across posts where users add the device to /etc/fstab
But that is just not needed

---

### Post by PicoDeRyo on 2012-01-19
I am very inexperienced in the Linux world, I am running Ubuntu Server, and I am running it headless, so I am working from a Mac and getting to the server via "Chicken of the VNC" to see the machine (also using the terminal on my mac). I don't know if this makes a difference. I entered some commands to add a new user, but now I don't know of to log on to the server using the "chicken of the VNC" without logging in under my main login. I'm sorry I need some more specific instructions. Please advise

---

### Post by carl4926 on 2012-01-20
> **PicoDeRyo said:**
> I am very inexperienced in the Linux world, I am running Ubuntu Server, and I am running it headless, so I am working from a Mac and getting to the server via "Chicken of the VNC" to see the machine (also using the terminal on my mac). I don't know if this makes a difference. I entered some commands to add a new user, but now I don't know of to log on to the server using the "chicken of the VNC" without logging in under my main login. I'm sorry I need some more specific instructions. Please advise

Wow.
Yes it makes a difference

Do you want to leave it mounted permanently ? And have it mount on reboot?
Then you could try adding it to fstab

Or if you want to mount it to a specific location, for example in /mnt
Create a directory in /mnt/sdb
Open a terminal:
```
cd /mnt
```
```
sudo mkdir sdb
```
```
sudo mount /dev/sdb1 /mnt/sdb
```

---

### Post by PicoDeRyo on 2012-01-21
That seems to have moved the drive into the folder created, but I am still unable to really do anything with it. And in that location I can't see it from finder on my Mac. (I have Avahi installed to see the server in Finder.) 

Leaving it mounted permanently sounds good, as well as mounting on reboot. I just don't understand why it doesn't just work when plugged in. 

For some reason the drive has a folder in it named "Lost+Found" but if I try to open it says 
"The folder contents could not be displayed.
you do not have the permissions necessary to view the contents of "lost+found". "

There is nothing on the drive I can format it if needed to make things work, I just don't know how it needs to be formatted, or if it even makes a difference

---

### Post by carl4926 on 2012-01-21
lost+found is a protected dir related to recovery. Just leave it.

I have a external USB HD (ext4) connected and it never gets pulled. But it just works.
If you add such a device to fstab and you happened to leave it disconnected, the system may throw a wobbly.

I think perhaps you need to explain exactly and as clearly as you can, just what your circumstances are.

---

### Post by PicoDeRyo on 2012-01-21
I will do my best to explain my setup. Fair warning though I am usually following how to's in order to get things up and running. 

So I have an old Dell laptop running Lucid 10.04 server with an external Hard drive connected via USB and the laptop is connected to my router with a network cable. I used two sites primarily to setup the system.
This is the first one where I got the idea to run Ubuntu Server headless
[http://www.havetheknowhow.com/Install-Ubuntu.html]("http://www.havetheknowhow.com/Install-Ubuntu.html")

after installing Lucid Server, I installed OpenSSH, Vim, VNC, and Webmin.

I used Webmin to schedule a Cron job to run VNC on startup so that I can use Chicken of the VNC on my Mac to get on the server. I also access the server from the Terminal on my Mac by logging on using SSH. 

The other website I used for instruction was  here:
[http://www.maclife.com/article/howtos/build_os_x_friendly_linux_media_server_your_old_pc?page=0,1]("http://www.maclife.com/article/howtos/build_os_x_friendly_linux_media_server_your_old_pc?page=0,1")

From here I installed netatalk and avahi so that I could view the server through Finder on my Mac. 

I then formated the external Hard Drive from NTFS to ext3 I have connected via USB using gparted. But still no luck mounting. 

I am more than willing to start over to get this to work, I just don't know what I am doing wrong. I installed server so that the install was light and didn't have unnecessary software, but now I wonder if that is part of the problem.  Let me know what you think. again thanks for your help

---

### Post by carl4926 on 2012-01-21
I guess you could try adding a line to fstab

First though lets make a directory on / for it

Open a terminal and 

```
cd /
```
```
sudo mkdir external
```
```
sudo chown bourne external
```

Now edit /etc/fstab
Add the line

```
/dev/sdb1    /external    ext3    defaults    0 0
```
You need to reboot for this to take effect

Crashing for the night now :D

---

### Post by carl4926 on 2012-01-21
That assumed I was correct with your username** bourne ** ??

Replace as necessary..!

---

### Post by PicoDeRyo on 2012-01-21
ok so I follow the commands  that you posted and it didn't work.  nothing happens in the terminal after I entered 

Code:
sudo chown bourne external

 and yes bourne is my username

and then in order to edit I used the following code

sudo gedit /etc/fstab

and then I entered the code you posted and saved, was that right? I don't know if I had the spacing exactly right does that make a difference?

after reboot I was able to see the drive in "places" but again I got the same error
 "Unable to mount 750 GB Filesystem
not authorized"

---

### Post by carl4926 on 2012-01-22
The drive should be in the root tree
/external

It should not load as a device on the fly under some generic term

Post result of

```
cat /etc/fstab
```

---

### Post by PicoDeRyo on 2012-01-22
bourne@JonesMash:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/JonesMash-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=57cc791d-d1d8-4806-a692-ebd4f6ec7de7 /boot           ext2    defaults        0       2
/dev/mapper/JonesMash-swap_1 none            swap    sw              0       0
bourne@JonesMash:~$ 


It doesn't look like I did it correctly I don't see sdb in there

---

### Post by carl4926 on 2012-01-22
Are you now saying you don't know how to edit the file?

---

### Post by PicoDeRyo on 2012-01-22
I think I know how to edit it, as I said,  to edit I used the following code

sudo gedit /etc/fstab

and then I entered the code you posted estimating the spacing you had posted, saved the file and closed, is that right? Then I rebooted

---

### Post by carl4926 on 2012-01-22
> **PicoDeRyo said:**
> I think I know how to edit it, as I said,  to edit I used the following code

sudo gedit /etc/fstab

and then I entered the code you posted estimating the spacing you had posted, saved the file and closed, is that right? Then I rebooted

Are you sure you were editing fstab on the correct machine?

```
gnomesu gedit /etc/fstab
```

---

### Post by carl4926 on 2012-01-22
Sorry: gnomesu (I don't think works in Ubuntu)

sudo gedit (is correct)

---

### Post by PicoDeRyo on 2012-01-22
Alright, so I finally was able to edit the file, and I did the reboot, and within the VNC I can open a file browser and I see the folder titled "External" but if I do a right click and try to add a folder I am unable to. 

Also viewing through the finder window on my mac using avahi I can login with the user bourne, and I can only see what is the home folder but nothing in the filesystem. 

Did I enter the info in the file correctly? I just put it as the last line


bourne@JonesMash:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/JonesMash-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=57cc791d-d1d8-4806-a692-ebd4f6ec7de7 /boot           ext2    defaults        0       2
/dev/mapper/JonesMash-swap_1 none            swap    sw              0       0
/dev/sdb1         /external      ext3        defaults      0     0
bourne@JonesMash:~$

---

### Post by carl4926 on 2012-01-22
It looks fine

Try this:

```
sudo chown -R bourne /external
```

I'm really not sure about OSX stuff
Same with VNC, it's not something I know.

I only use Linux and ssh

---

### Post by PicoDeRyo on 2012-01-22
Success!! I was able to create a new folder and copy a file over. Looks like I am in business. Thanks for all your help.  So in order to unplug the hard drive I should shut down the server correct? and not start it up without the drive connected? I don't really plan to disconnect it, I just want to know in case I need to. Thanks again

---

### Post by carl4926 on 2012-01-23
> **PicoDeRyo said:**
> Success!! I was able to create a new folder and copy a file over. Looks like I am in business. Thanks for all your help.  So in order to unplug the hard drive I should shut down the server correct? and not start it up without the drive connected? I don't really plan to disconnect it, I just want to know in case I need to. Thanks again

Because the device is listed in fstab the system expects it to be there. It may still boot with it disconnected, I can't really say.

I'm not sure about unmounting it while it's part of the system in fstab. I'd be careful. Servers generally don't employ removable media. They are usually permanent 24/7

Maybe someone else knows about unmounting.?
It may be OK, so long as you are sure it's not busy.

---

### Post by carl4926 on 2012-01-23
I just noticed on my openSUSE box, uses kde
I have a partition mounted at boot in fstab
But the device partition also shows in dolphin as a 145GB Hard Drive. I can right click and have Unmount as an option, but I have not tried it.

I should have said. Yes, if you can afford to shut the server down to remove the HD, unless you learn otherwise with regard to the Unmount option, then shut down would be the safer option.

---

### Post by PicoDeRyo on 2012-01-24
Sounds good, like I said I don't really have any plans to do so, but it is nice to know the best way to handle it if the situation arises. Thanks for all your help.

---

### Post by carl4926 on 2012-01-24
> **PicoDeRyo said:**
> Sounds good, like I said I don't really have any plans to do so, but it is nice to know the best way to handle it if the situation arises. Thanks for all your help.
You are most welcome

---

