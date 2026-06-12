---
title: "Data Recover Help Needed"
date: 2008-11-24
forum: General Help
---

### Post by russ5811 on 2008-11-24
I recently followed a tutorial to put my Home on a different partition. (Here's the link to the tutorial: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) )

After I did this, I got numerous errors involving .dmrc and .ICEauthority.  I tried to use recovery mode and the live CD to fix this and it did not work. 

So, I now just want to reinstall Ubuntu 8.10, but I have a MAJOR problem. All the files in my Documents, Music, and Video folders are not accessible.  I can see them, but when I try to copy them to an external hard drive, I get write errors because the files can't be read because I'm not the owner.

Please, can someone tell me what to do to recover these files either from the live CD environment or from the recovery mode command line. I have some irreplaceable files in there.

I can't believe I was this stupid!! PLEASE HELP Guys!

---

### Post by ju2wheels on 2008-11-24
First, whatever you do, do not modify your partitions any further so you dont end up losing the data.

The easiest solution to try first is a live cd. If you are lucky, you should just be able to boot into the live cd, click on Places and one of the drives listed there should be the partition with your home data on it.

Open that partition by clicking on it. If you see your data then just plug in a usb drive or your external and copy things over. If you get any errors post back here.

Here is a guide similar to what you want to do: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

If you have to resort to mounting manually as described, post the output of "fdisk -l" here first.

---

### Post by russ5811 on 2008-11-24
thanks for the reply, unfortunately this didn't work..unless i did something wrong. which is entirely possible. 

i booted a live cd, found the folders and attempted to copy them to my external hdd. however, it says that i don't have the right permissions to access the files. i tried mounting the drives but then it says that the files cannot be accessed. i can try to get verbatim messages later if you need them. thanks again.

---

### Post by ju2wheels on 2008-11-24
We will need more info to be of further assistance. At the moment we wont be able to tell whether the permission problems are on the home partition or your external.

When you try again, plug in your external and mount the home partition to where you can at least browse and see your files on it if you can.

Then give us the output of the following commands:

```

fdisk -l
mount

```

---

### Post by russ5811 on 2008-11-24
Here's what happened. Did I do anything wrong?

ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdf
ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by ju2wheels on 2008-11-24
Ok at least now I know what partition types we are working with.

The first command failed though, so could you run this:
```

sudo fdisk -l

```

So we have one formatted as FAT32 (External?) and one as EXT3 (the hard drive of the pc). If that does not sound correct then post the above command so we can see the other partitions on your drives, otherwise continue below.

Run this:
```

ls -al /media/disk-1

```

If that gives you a listing of files/folders that you know were on your home drive (you would most likely just see lost+found and a folder of your user name) then try to this to recover your files:

Create a folder on the external and call it "backup".

```

sudo cp -R /media/disk-1 /media/disk/backup

```

Note: If you had files larger than 4gb in your home folder (dvds for example), you will not be able to copy them to the external as the FAT32 file system has a 4gb file size limit.

---

