---
title: "Priblem with dvd mounting.PLEASE HELP"
date: 2008-05-22
forum: Hardware
---

### Post by ultimate_aektzis on 2008-05-22
Hi everybody.I am a new Linux user and I have a liitle problem with my dvd drive.Before changing my desktop's OS I have burned some data to a dvd disk so that I can recover them after format.The problem is that when I insert the disk inside the drive and go to places computer and double-click on the drive's icon i take a message claiming that there is no disk in the drive.Have i done something wrong.I would be very grateful if you could help me solve the problem.
Sorry for bad english...

---

### Post by didac on 2008-05-22
No need to apologize. Nobody knew English when he was born. He had to learn it.

Looks like the drive cannot read the DVD. Maybe the problem is with the DVD disk itself. Can you read it in another computer?

To discard other problems, check the following: 

In a terminal type:

```
dmesg | egrep dvd
```

Mine says:

```
[17.223122] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray

```

Note the sr0 after the square bracket. Yours could be different. Enter now

```
dmesg | egrep sr0
```

changing sr0 to whatever you have. Then enter:

```
cat /etc/fstab
mount
```

And post your results here

---

### Post by ultimate_aektzis on 2008-05-22
I will post my results but i cant understand how can i find "my" sr0???

---

### Post by didac on 2008-05-22
Sorry for not being clear. Once you do dmesg | egrep dvd the output line starts with a number between square brackets (seconds since booting when the event took place) Immediately after and before the colon, you have your device, sr0 or whatever it's in your case.

---

### Post by ultimate_aektzis on 2008-05-22
So we have:
> 
periklis@p:~$ dmesg | egrep dvd
[   22.684938] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray



> 
periklis@p:~$ dmesg | egrep sr1
[   22.684938] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.685032] sr 1:0:1:0: Attached scsi CD-ROM sr1



> periklis@p:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c0acd95f-64d6-4635-8840-e76f355d181b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1f1e261f-9d05-4497-8ac8-cfffed2ffa63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
periklis@p:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/periklis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=periklis)
periklis@p:~$ 


I am looking forward for your help man

---

### Post by didac on 2008-05-22
I'm back online. Sorry about the interruption.

Do:

```
ls -l /dev/sr1
lrwxrwxrwx 1 root root 4 2008-05-22 16:01 /dev/sr1 -> scd1

```

Look at the bit after -> That tells you where your DVD is linked to. Now, you have two lines in your fstab for your dvd. One is /dev/scd0, the other being /dev/scd1. These two control your two cd-dvd's. I don't see anything wrong there, unless ls -l /dev/sr1 gives you a different result, like scd2, which I don't think.

If it gives you anything above scd1, add another line to your fstab by doing 

```
sudo gedit /etc/fstab
```

and copy from the others too.

Be patient. We are arriving -- I think. Insert the dvd, count to 10. In Nautilus, enter in the address bar

```
/media
```

and you should see two folders pertaining to your 2 cd-dvd's. Open them, and you'll be there.

If so far into the game nothing has happened, cry. Your dvd is not recognised, maybe it has scratches and maybe another computer will open it. Sorry

---

### Post by ultimate_aektzis on 2008-05-22
I  've followed your instructions.so I typed ```
periklis@p:~$ ls -l /dev/sr1
lrwxrwxrwx 1 root root 4 2008-05-22 21:28 /dev/sr1 -> scd1

```

As I understood from your post there is no prob here.Right?
So I inserted a dvd drive waited for 10 sec and typed /media and I took the following```
periklis@p:~$ /media
bash: /media: is a directory

```

Any cd icon appeared on my desktop

---

### Post by didac on 2008-05-26
Sorry again for not being around. Have you solved the problem?

I wasn't  clear enough. Type /media in the Nautilus address bar, in your 'Windows explorer', not in a terminal. You'll see a folder called cdrom1. It is inside there where your dvd files should appear. If there is nothing there, type in a terminal (now it's a terminal):

```
sudo mkdir /media/cdrom1
```

Eject and re-insert the cd. Wait for it to settle down and try typing /media or /media/cdrom1 in the Nautilus address bar again.

Sorry, but the problem looks more with the dvd. You'll have to try opening it in another computer or use recovery programs to get part of the data back.

---

### Post by ultimate_aektzis on 2008-06-05
No.All folders in /media are empty.Probabaly my dvd drives are not supported by hardy heron.I wish ubuntu developers will do sth for that.:(
Thank you very much for your help didac.Respect...

---

### Post by ultimate_aektzis on 2008-06-23
I "recover" this topic as I want to ask whether is possible to connect directly with hardy developers explain them the problem and have some desired results like a possible solution or a kernel update.If it helps my drives appear in "my computer" area and my dvd drive(one of 2) is LG.I mention that as I think that LG does not make drivers for linux.
thanks in advance for your help:)

---

