---
title: "Permanently Mount Windows RAID setup"
date: 2009-01-07
forum: Hardware
---

### Post by mfrancis107 on 2009-01-07
Setup:
- 2 hardrives software RAID 0 running Windows (using nvidia RAID software)
- 1 hardrive running Ubuntu 8.10


I followed these directions to mount the drive. ([Original Thread]("http://ubuntuforums.org/showthread.php?t=611583&goto=nextnewest"))

>  Re: Mounting NTFS Raid 0 Array
I think I may have some help for the people posting in this thread, I too have a Nvidia fakeraid with a NTFS partition I wanted to preserve. I scoured the web and found a few simple commands that will make things easy on you.

Insure that dmraid is installed. (Search dmraid in your package manager to check)

run the command "
Quote:
sudo dmraid -ay
"
This will activate you raid drives arrays and partitions.
Output should look like this.

Quote:
RAID set "nvidia_aifccjbb" already active
RAID set "nvidia_aifccjbb1" already active
The text in quotes will differ from system to system, but the important thing here is the second line, the one that ends in one. That signifies the first partition on that drive. So in order to mount this partition all you have to do is.

Quote:
sudo mkdir /media/raid
sudo mount -t ntfs /dev/mapper/nvidia_aifccjbb1 /media/raid
This will mount your raid system (assuming it is already formated with a ntfs partition).

Everything worked wonderfully.  The disk is mounted.  Files can be transfered without any problem.

However, I can't figure out how to mount the drive permanently.  Or will I always have to manual mount the drive every time I boot up.


Thanks for the help.

Michael

---

### Post by Ben Webber on 2009-01-18
Hi Michael. I think the solution might be in your /etc/fstab file.

From the terminal, type:

```
sudo gedit /etc/fstab
```

/etc/fstab is used to keep track of the automatic mounting of all your devices.

At the bottom of the file, add the following. I assume your drive is formatted as NTFS.

```
#Entry for RAID array
/dev/mapper/nvidia_aifccjbb1 /media/raid ntfs users,defaults,umask=000 0 0
```

When you reboot, /media/raid should be mounted and visible on your desktop.

Try this and let me know if it works for you.

---

