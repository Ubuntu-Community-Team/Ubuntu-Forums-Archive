---
title: "Retrieving files from crashed windows using Ubuntu question."
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Bobert on 2007-05-11
Hi, I have quite a dilemma, and I have been trying to get at this for days now.  

I have a computer I am working with from work.  It was/is currently running Win XP, and will not boot.  I have a quick blue screen flash, not long enough for me to read the error messages, and then it restarts again and will go through this cycle indefinitely.  After putzing around with it for a little bit, including trying a win boot disk, I decided to try to run the Ubuntu Edgy 6.10 live disc.  With this I can get into the system  and see the hard drive.  Here is problem #2 and #3.  #2, the file system is NFTS and which I believe is not recognizable by linux.  The #3 problem is that the computer is security protected and whatnot.  I do not know how controlled the security is, but seeing as how I cannot even access the files due to the file system contradiction, I can't imagine if they will work or not if pulled from the HDD in linux.  Any help would be greatly appreciated, this is really starting to become a headache for me.  

-Bob

---

### Post by aysiu on 2007-05-11
If by "security protected" you mean it is encrypted, then, yes--this could be tricky.

If it's any other kind of "security protection," it isn't really protected at all.

And Ubuntu can work with NTFS just fine, actually.

Can you boot up the live CD, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
```

---

### Post by Bobert on 2007-05-11
Hope this helps
I also had to use the sudo su command first to get this, otherwise it wasn't coming up.

> Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4863    39062016    7  HPFS/NTFS


---

### Post by aysiu on 2007-05-11
That's weird. *sudo* alone should have done it.

In that case, paste these commands in: ```
sudo -i
mkdir /media/recovery
mount -t ntfs /dev/hda1 /media/recovery
nautilus /media/recovery
``` By the way, that last command will work only if you're using Ubuntu. If you're using Kubuntu, that last command should be ```
konqueror /media/recovery
``` If you're using Xubuntu, it should be ```
thunar /media/recovery
```

---

### Post by Bobert on 2007-05-11
This is the result I got:

> root@ubuntu:/home/ubuntu# sudo -i
root@ubuntu:~# mkdir /media/recovery
root@ubuntu:~# mount -t ntfs /dev/hda1 /media/recovery
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# nautilus media/recovery

(nautilus:13287): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.
root@ubuntu:~# 


just for future reference, I am just using Ubuntu too

---

### Post by aysiu on 2007-05-11
Oh, no. This isn't good: ```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
``` Can you, in fact, post the output of ```
dmesg | tail
```?

**Edit**: Wait. Before you do that, can you also try this? I think I left off an option--not sure if that's going to make a difference or not: ```
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
nautilus /media/recovery
```

---

### Post by Bobert on 2007-05-11
Dont tell me that!  I need to hear "oh thats not so bad"

> [17184189.536000] NTFS-fs error (device hda1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[17184189.536000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load essential metadata.
[17184217.440000]  0:0:0:0: rejecting I/O to dead device
[17184217.444000]  0:0:0:0: rejecting I/O to dead device
[17184217.620000]  0:0:0:0: rejecting I/O to dead device
[17184220.940000]  0:0:0:0: rejecting I/O to dead device
[17184557.028000] NTFS-fs error (device hda1): ntfs_attr_find(): Inode is corrupt.  Run chkdsk.
[17184557.028000] NTFS-fs error (device hda1): ntfs_read_inode_mount(): Failed to lookup attribute list attribute. You should run chkdsk.
[17184557.028000] NTFS-fs error (device hda1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[17184557.028000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load essential metadata.


I do not like seeing that "dead device" though

---

### Post by aysiu on 2007-05-11
There may still be hope.

"This isn't good" just means it's going to be tricky, and we'll have to try several things. Not all hope is lost!

Do you have a removable drive of some kind? Somewhere you can copy the files to? If so, we can maybe use *ddrescue* to help.

Can you try this? ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
``` Remove the # sign from the beginning of any line (it's called *uncommenting*) that looks like a web address. Then save and exit Gedit. ```
sudo apt-get update
sudo apt-get install ddrescue
```  Plug in your rescue USB device (external hard drive, iPod, whatever... it must be as big as the data you have your own corrupted hard drive, though). Find out where it's located by pasting in ```
df -h
``` That will tell you both its "mount point" and how much free space it has. The device name is the one in the left column. The "mount point" is the one in the right column. Let's just assume for the sake of this example that your mount point is /media/usbdisk
```
dd_rescue /dev/hda1 /media/usbdisk/hda1backup.img
sudo mount /media/usbdisk/hda1backup.img /media/recovery
nautilus /media/recovery
``` If you get any errors, just keep posting them back here.

---

### Post by Bobert on 2007-05-11
I got up to step 2 and this happens:

> root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               885M  704M  181M  80% /
varrun                252M   80K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  7.6M  245M   3% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 252M   16K  252M   1% /tmp
/dev/sdb1              23G  129M   23G   1% /media/LOCAL DISK
root@ubuntu:~# sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
root@ubuntu:~# gksudo gedit /etc/apt/sources.list

(gksudo:13885): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


---

### Post by Bobert on 2007-05-11
Is there another way to get at the repositories (thats what they are, right?) but not through the terminal?  I thought there was...  could be wrong though

---

### Post by aysiu on 2007-05-11
When you get this error ```
gksudo:13885): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
``` is it just the error? Or is it the error and Gedit actually shows up? If it's the error and Gedit showing up, just continue on. If it's only the error (and no Gedit), we'll have to use a terminal-based text editor: ```
sudo nano /etc/apt/sources.list
``` To save when you're done press Control-X, Y, then Enter.

FYI: instead of the mount point being /media/usbdisk, it appears to be /media/LOCAL\ DISK

So instead of the commands I gave you earlier, you should use these: ```
sudo apt-get update
sudo apt-get install ddrescue
dd_rescue /dev/hda1 /media/LOCAL\ DISK/hda1backup.img
sudo mount /media/LOCAL\ DISK/hda1backup.img /media/recovery
``` And none of your graphical applications (Nautilus or Gedit) appear to be working for some reason, so once it's mounted, we'll have to check on the files using the terminal. So ditch this last command: ```
nautilus /media/recovery
``` and substitute in ```
cd /media/recovery
ls
``` and then post back the output of *ls* here.

---

### Post by Bobert on 2007-05-11
The actual window of the .list file opened up, but immediately closed out.  I continued on your alternate route.  I get this message now, which I think is where the security is possibly becoming an issue.  

> root@ubuntu:~# dd_rescue /dev/hda1 /media/LOCAL\ DISK/hda1backup.img
dd_rescue: (fatal): open "/media/LOCAL DISK/hda1backup.img" failed: Read-only file system


---

### Post by aysiu on 2007-05-11
Hm. Any chance this might work better? ```
sudo dd_rescue /dev/hda1 /media/LOCAL\ DISK/hda1backup.img
``` It's worth a shot.

---

### Post by Bobert on 2007-05-11
Nope, im getting the same message.  I am slightly confused as to why it is LOCAL\ /DISK.  Isnt it 1 phrase?

---

### Post by aysiu on 2007-05-11
When the terminal sees a space, it assumes that's the end of the file name, so it would read ```
/media/LOCAL DISK
``` as being just ```
/media/LOCAL
``` The backslash tells it the space is in the filename and that the rest of the filename should continue to be read.

---

### Post by Bobert on 2007-05-11
Oh, also, just to do it, I tried to get into the media/recovery directory, and it says it doesnt exist, even thought I did do that mkdir command before.  Any thoughts on that?

EDIT: media/LOCAL does not exist either

---

### Post by aysiu on 2007-05-11
That error is not a good one. I tried searching it on Google and came up with [these results](http://www.google.com/search?num=100&hl=en&safe=off&q=dd_rescue%3A+%28fatal%29%3A+open+failed%3A+%22Read-only+file+system%22&btnG=Search)--nothing with any kind of solution.

How long do you have to wait? I think the problem may have gone beyond what I know, but there are a lot of knowledgeable recovery folk around here who may be able to help you save your files.

If no one answers, then bump the topic after a few hours. If I'm still around I may be able to help you again... not sure, though.

In the meantime, if no one else answers *and* I don't answer, PartImage may be worth a shot: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by aysiu on 2007-05-11
> **Bobert said:**
> Oh, also, just to do it, I tried to get into the media/recovery directory, and it says it doesnt exist, even thought I did do that mkdir command before.  Any thoughts on that?

EDIT: media/LOCAL does not exist either You need a slash in there are the beginning. It should be ```
/media/recovery
``` and not ```
media/recovery
```

---

### Post by Bobert on 2007-05-11
How long?  well sooner the better.  I dont know if it matters much, but have not installed ubuntu, only running the live version, which you may have been under the assumption of.  My question about that is, does that make directory creating impossible? or is it more the situation that is messing everything up?  I appreciate all your help.  I have a few errands to do so I will go take care of them and then look back.  Im hoping for the best!

---

### Post by aysiu on 2007-05-11
I'm hoping for the best, too. Even with some confusion you're having, you're pretty good at following instructions under a stressful situation. 

What I know about is mounting a healthy partition.

I also know about using *ddrescue* to mount dead and/or slightly corrupted partitions.

We've gone past those two. There are a lot of recovery tools available. I just don't know how to use them. That's why I'm hoping a recovery expert will jump in here and help.

---

### Post by Bobert on 2007-05-11
Bump for help

---

### Post by Bobert on 2007-05-14
Hey, I am still looking for some help to my problem listed on the first page.  If anyone has any insight that would be greatly appreciated.

---

