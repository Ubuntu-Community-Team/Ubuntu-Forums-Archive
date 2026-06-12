---
title: "Help with installing a slave drive please"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by chester112 on 2009-08-14
I installed an extra 160Gb drive, configured it through bios as a slave. I Noticed that the
drive was greyed out, so after downloading Partition editor- I tried to follow this tutorial
as best I could :  [https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=(drive)|(hard)|(new)#Partition%20The%20Disk]("https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28hard%29%7C%28new%29#Partition%20The%20Disk")

I assumed the drive was pre formatted, advertised as such but probably with windows. I'm a very confused noob but I think I managed to create an entire partition on the hard drive,  (souley to be used for ubuntu). It asked for a password before completing the operation, I typed my usual and rebooted.

The drive now appears under computer in PLACES. I can open it but I don't have permissions to use it  (won't let me drag any files to it etc).

[B]Error opening file '/media/disk 
Permission denied[/B]

Totally lost. Can someone please help? Not sure what I've done wrong :confused:

Thanks

---

### Post by AmerNewbieInDE on 2009-08-14
looks like the file ur trying to copy has the restriction on it... try some files from your home directory, if that is the problem, then use 

sudo cp **/media/disk** /path

there is a space as /media/disk(space)/path

---

### Post by chester112 on 2009-08-14
Thanks but no success. Under permissions it states The Permissions of "disk" could
not be determined.

---

### Post by AmerNewbieInDE on 2009-08-14
quick question.. which of the eide cable did you put the slave disk, why not on the disk jumpers state which is master and slave.. if i remember correct, master is on the end and slave is in the middle.

are you running dual boot with windows?  i had similiar problems with a windows formated disk. try running 

sudo gparted

enter the admin password

then remove the partition and remake it, careful not to remove your current install.

---

### Post by presence1960 on 2009-08-14
I will give you a graphical solution to this. You need to take ownership of that device. Open a file browser and click on that device (drive) to mount it. Now open a terminal and run this command ```
gksu nautilus
``` Type in your password and when nautilus opens go here: File System > media > <your device name>. Right click on the device and choose properties. Set owner & group to your user name. See attached screen shot. 

Remember you are in nautilus as root. Do this only close nautilus and reboot. You should be able to access the device with read/write permissions.

---

### Post by chester112 on 2009-08-15
Thanks presence. Okay I tried that but when I execute that nautilus command, I get the following:

[B]MYUSERNAME@MYUSERNAME-desktop:~$ gksu nautilus

** (nautilus:3635): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.[/B]

AmberNewbie- This is my first full PC build from scratch, the setup is as you described (master at the end, slave in the middle, jumpers all set correctly). This systems entirely dedicated to Ubuntu, no dual boot.
___________________________________________________________________________________________________

right, I think I got it half way there. I typed the following into the terminal:
[B]
sudo mkdir /media/'main storage'/$USER
> sudo chown -R $USER:$USER /media/'main storage'/$USER[/B]

'Main Storage' was (I think) where I mounted the new drive. So I have managed to create a writeable folder on the new drive, but the rest of the hard drive is still un-writeable. Is there a way to make the whole 'Main Storage' drive writeable, not just the folder I created? If there is no easy way, then can I put the new writeable folder as a shortcut on my desktop?

feels like I need a flippin degree in computer science for this lol

---

### Post by presence1960 on 2009-08-15
that is what mine says also but the nautilus window should open after the message. See my screenshot. The nautilus window is on the right. This is file browser logged in as root!

---

### Post by chester112 on 2009-08-15
Oh that's embarrassing, I'm sure No file browser popped up last time. :oops:

Anyway, I mounted, executed & changed the properties as advised. Works brilliantly. 
Thanks very much for your help there presence, sorted, really appreciated \\:D/

---

### Post by presence1960 on 2009-08-15
glad you got it working! Enjoy Ubuntu.

---

