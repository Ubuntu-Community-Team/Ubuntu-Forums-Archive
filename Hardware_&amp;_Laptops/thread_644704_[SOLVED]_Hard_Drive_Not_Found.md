---
title: "[SOLVED] Hard Drive Not Found"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by MidianLies on 2007-12-19
Hello All,

Two SATA/150 HDD's installed in an  HP dv9000 notebook

I just used Acronis True Image Home to clone my operating system hard drive. I removed the old hard drive and installed the new one. When I was finished, the program mentioned something about resetting jumpers to establish a primary drive, but I don't remember what exactly it told me to do.

So I decided to resize a partition on my new OS drive using Acronis Partition Expert, but when it reboots and attempts to resize the drive, I get an error saying drive not found. (Keep in mind, that I am able to boot to my OS drive and Data drive and access all files.)

When I attempt to access disk management, I get an error saying, "The Disk Management console failed to connect to the remote computer because the Disk Management remoting service is not in the Windows Firewall exception list. Add the Disk Management remoting service (dmremote.exe) to the Windows Firewall exception list and try again." At the bottom of the Disk Management window, it says, "Unable to connect to Logical Disk Manager service." << --- This problem has somehow resolved itself on its own.

When I observe the status of my new OS hard drive and my secondary Data Drive, they are both listed as primary master drives. Is this a problematic configuration? If so, how can I change it?

Please bear with the long-winded plea for help, and
Thanks To All

BTW - I am attempting to resize my HDD partition in order to install Ubuntu to the freed space.

---

### Post by MidianLies on 2007-12-19
This damned thing is already pushed back to the third page in just 5 hours? Is anyone helpful going to even see this?

---

### Post by MidianLies on 2007-12-19
Bump.

---

### Post by nick_h on 2007-12-19
> When I observe the status of my new OS hard drive and my secondary Data Drive, they are both listed as primary master drives. Is this a problematic configuration? If so, how can I change it?

When you have 2 devices on the same IDE channel one should be set to master and the other to slave.  This is done by setting jumpers on the drive.

Please wait a little longer before bumping your thread, people do read them.

---

### Post by MidianLies on 2007-12-19
Its an SATA HDD, thus master/slave conditions don't apply.

---

### Post by MidianLies on 2007-12-19
I didn't realize that at the time.

---

### Post by nick_h on 2007-12-20
> Its an SATA HDD, thus master/slave conditions don't apply.
True.  I don't know why your software refers to the drives as "master".  It probably isn't a problem.  I would just create some free space and attempt to install Ubuntu.

---

### Post by tommcd on 2007-12-20
In the future use parted magic to partition in linux. It is probably more reliable for partitioning linux systems:
[http://partedmagic.com/](http://partedmagic.com/)

---

