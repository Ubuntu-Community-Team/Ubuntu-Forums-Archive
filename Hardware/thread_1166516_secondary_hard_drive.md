---
title: "secondary hard drive"
date: 2009-05-21
forum: Hardware
---

### Post by kandd10876 on 2009-05-21
I have an acer aspire 4520 and just got rid of Vista ( YAY!!!!!) and am fully running Ubuntu (newest version) and it is not showing my second hard drive where everything is stored at.  Could someone help me with this?

---

### Post by drs305 on 2009-05-21
Is this a second internal drive? If so, for ext2/3/4 you just want to make a mount point, make yourself the owner of the mountpoint, and include the device in fstab. Here is a good reference. 

[How to fstab ]("http://ubuntuforums.org/showthread.php?&t=283131")

We can help if you have questions. We would need the mount point name, format (ntfs, ext3, etc) and the device name and/or UUID (sdb1, sdc2, etc).

---

### Post by kandd10876 on 2009-05-21
Yes, it is a second internal hd. the format is ntfs.

---

### Post by Bucky Ball on 2009-05-21
In Synaptic Package Manager, look for and install:

ntfs-3g

You will then find it in the System->Administration menu as 'NTFS Configuration Editor'. That should find it.

---

### Post by drs305 on 2009-05-21
Install  and open:
```

sudo apt-get install ntfs-config # install
gksudo ntfs-config # open  or via System, Administration, NTFS Configuration Tool

```
Enable internal write support and then enter the mount point. The name you enter will be placed in /media. So if you type in a mount point of "mydata", your device will be mounted in /media/mydata.

Once you have entered everything in ntfs-config and closed it:
```

sudo mount -a

```
If you don't see any messages, the device is now mounted on the mount point you designated.

---

### Post by kandd10876 on 2009-05-21
ok... I just read about mounting. I didn't know I had to mount my second hd. So I need to mount it and assign it an name??  I am new to linux, but I am so happy to be rid of windows.

---

### Post by drs305 on 2009-05-21
> **kandd10876 said:**
> ok... I just read about mounting. I didn't know I had to mount my second hd. So I need to mount it and assign it an name??  I am new to linux, but I am so happy to be rid of windows.

Yes, it has to be mounted. Automatic mounting is done in fstab. The ntfs-configuration tool will make the changes necessary in your system files. Just run the commands as indicated in my previous post to get your ntfs drive mounted and readable. 

Reviewing the link to fstab should give you a background as to what is going on.

---

### Post by kandd10876 on 2009-05-21
ok... the ntfs config is not showing. I input the syntax and get a message saying..

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by drs305 on 2009-05-21
> **kandd10876 said:**
> ok... the ntfs config is not showing. I input the syntax and get a message saying..

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You probably have synaptic open. The system will only let you have one installer running at a time to prevent conflicts. If you prefer, just find "ntfs-config" and "ntfsprogs" in synaptic and install them from within synaptic.

And don't forget the hyphen: ntfs-config  ;-)

---

### Post by kandd10876 on 2009-05-21
I found the ntfs-3g in the synaptic package manager and reinstalled it.

---

### Post by kandd10876 on 2009-05-21
ok... got the ntfs config installed... but not allowing me to enable internal device.

---

### Post by kandd10876 on 2009-05-21
still not showing my other hd....
I got the ntfs config up and running, but not sure how to id my other hd for the os to reconize it

---

### Post by drs305 on 2009-05-21
Here is a link to the manual way to adding the drive to fstab. See post #3:
[http://ubuntuforums.org/showthread.php?t=959315]("http://ubuntuforums.org/showthread.php?t=959315")

Maybe you would find this easier.

---

### Post by logos34 on 2009-05-21
try the steps here:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Bucky Ball on 2009-05-22
NTFS Configuration Editor should do this automatically. It is in your menu if you have reinstalled it, as mentioned.

---

