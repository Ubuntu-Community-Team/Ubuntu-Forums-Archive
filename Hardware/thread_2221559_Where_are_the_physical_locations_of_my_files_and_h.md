---
title: "Where are the physical locations of my files and how do I make sure my mount points a"
date: 2014-05-02
forum: Hardware
---

### Post by Baasha on 2014-05-02
I recently upgraded to 14.04 and I may have messed things up, i'm not sure.

My system consists of a 128 GB ssd and two 1 TB hdds configured as Raid I.  I want the OS located on the ssd for fast booting and everything else located on the HDDs.  When doing the upgrade I got to the choice of how I wanted to do the installation and and I chose "Something else" so I could mount my hdds as Home.  But although I could see the drives in Gparted all the options were greyed out and I was unable to change anything.  So I had to back up and I chose to install without out erasing my data.

Now I suspect that Home and all my other files (new ones created during the install) are on the ssd but I don't know how to confirm that.

1. How do I find out the physical locations of of various directories?

2. How do I tell Ubuntu that my Home is on the hdd?

I had a look at the Disks program but don't want to make things worse until I know exactly what to do.

---

### Post by ajgreeny on 2014-05-02
Use command **mount** which will show you where your mounted partitions and filesystems are sited.  There will be one line for root and one for /home if it really has been made separate as well as many more lines for various logical f9lesystems.

PS:  I do not use nor really understand RAID setups, but as far as I know the mount command will still show everything needed.

---

### Post by Baasha on 2014-05-02
Thx ajgreeny, but mount doesn't really give me what I need to know.  As you can see below, only one drive is mentioned and it isn't telling where home is located. 

```

bob@Emma:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=bob)
bob@Emma:~$ 

```

I have attached a screenshot from the Disks program.  As you can see all my drives are shown and I can access them all (they are mounted).
[ATTACH=CONFIG]252765[/ATTACH]
My problem is that I need to tell the system that it should consider the two 1 TB disks as Home.  BTW, Raid 1 merely treats two hdds as one drive.  Each one is a mirror of the other.  if you have two identical drives and set them up as a Raid then you have an automatic backup in case one drive fails.  In the screenshot you will see two 1 TB drives listed at the top and then at the bottom one 1 TB block device.  The system has two drives but it sees them as one device.  Any more sugesstions?

---

### Post by ajgreeny on 2014-05-02
As things stand you do not have a separate /home partition so your home will simply be a folder in the root partition. I know what RAID is and what it does, I just do not know how exactly it does it nor if it makes a difference to things like fstab and how you mount partitions at boot time.

---

### Post by ian-weisser on 2014-05-02
> **Baasha said:**
> if you have two identical drives and set them up as a Raid then you have an automatic backup in case one drive fails.

To be more precise, you have *increased reliability*. It's not a recoverable backup in case, say, your system is compromised or a file is erroneously deleted.

Install the the 'mdadm' package to assemble raid arrays of whatever configuration you like, and to repair damaged arrays.
You are wise to keep your boot separate from your raid array. It prevents many possible problems.
There are quite a few very good tutorials on how to configure mdadm after you have it installed, and [the manpage]("http://manpages.ubuntu.com/manpages/hardy/man5/mdadm.conf.5.html") is quite helpful, too.

Once the array is created, you can mount it anywhere in the filesystem you wish, including as your /home, using the (manual)* mount* command or (automatic) /etc/fstab file.

---

### Post by SeijiSensei on 2014-05-02
Are the 1 TB drives in an external device, or are they in same computer as the SSD?  If they're on an external device, it's likely the device is managing the RAID1 array and simply presenting a single interface to Linux.  If it's a USB or similar device, try unplugging the cable connecting the device to the computer and reconnecting it.  Then use "sudo tail -n100 /var/log/syslog" to see the last hundred lines of syslog.  You should see entries for the device being reconnected.  Does the log report the device as something like /dev/sdb?

If so, try a test mount with
```

sudo mkdir /mnt/raid
sudo mount /dev/sdb1 /mnt/raid
mount

```
If you don't get an error after the first mount command, the second one should display an entry for the mounted device.

If that device has the contents of /home, you can [use /etc/fstab to mount it as /home]("https://help.ubuntu.com/community/Fstab") in your newly-created filesystem on the SSD.  However that will hide the contents of the /home that was created during installation.  If there are files there you need, mount the RAID as above and copy them over to a directory under /mnt/raid.

If you were using Linux software RAID before, then you need to install mdadm as ian-weisser says and activate the array.

---

### Post by Baasha on 2014-05-03
Thx to all how replied.  I think I may have had a bad install file.  I downloaded a fresh iso and started from scratch.  This time Gparted allowed me to set my mount points and I finally have a working system again, configured the way I want it.

---

