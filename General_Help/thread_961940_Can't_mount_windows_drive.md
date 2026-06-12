---
title: "Can't mount windows drive"
date: 2008-10-28
forum: General Help
---

### Post by m4778 on 2008-10-28
Hi i am new to linux.  I have been researching and playing around with it for about a week though so i am fairly farmiliar with the basic layout and very simple terminal commands.  I am currently running linux off a 2gb flsh drive so that i can use my programs on other computer at school and such.  but i am wondering how to mount the windows drive on my home computer. i have tried many different commands suggested on other forums like "sudo mount -t ntfs /dev/sda1 /media/windows" and many variations of that command with no success.  all suggestions are much appreciated. thanks in advance.

---

### Post by drelyn86 on 2008-10-28
Is there any output when you try to mount it? Perhaps you have the wrong device name(?) We need more info.

---

### Post by alienprdkt on 2008-10-28
could try the ntfs"-3g"

sudo mount -t ntfs-3g /dev/sda1 /media/windows

---

### Post by m4778 on 2008-10-28
the response to the above command is "mount: according to mtab, /dev/sda1 is already mounted on /media/windows"

---

### Post by josephellengar on 2008-10-28
If you have the partition in the fstab, it might automount on startup, in which case you wouldn't have to manually mount it.  Also, to simplify your commands normally with a terminal command you don't have to specify the filesystem type, as in most cases most linux distros can figure out the fs type on their own, so you can get rid of the -t option and the ntfs part of the command.

---

### Post by m4778 on 2008-10-28
no it isn't mounted. because i can't access it when i go to media/windows. also i tried to unmount it and remount it but when i went to unmount it it said that there was nothing mounted to /media/windows...so its contradicting itself. any advice

---

### Post by drelyn86 on 2008-10-28
> **m4778 said:**
> no it isn't mounted. because i can't access it when i go to media/windows. also i tried to unmount it and remount it but when i went to unmount it it said that there was nothing mounted to /media/windows...so its contradicting itself. any advice

k, try the following and reply with output:

```
ls /media/windows/
```

---

### Post by m4778 on 2008-10-28
Nothing happens

---

### Post by drelyn86 on 2008-10-28
> **m4778 said:**
> Nothing happens

k, that verifies that there is nothing mounted to that folder and that the folder does exist.

I'm wondering if sda1 is your windows drive.
If you know how much space is in your windows drive, the "df" command could help you better guess which one it is

```
df
```

---

### Post by m4778 on 2008-10-28
It then says "df: cannot read table of mounted file systems: Stale NFS file handle"  im pretty sure that /dev/sda1 is the windows drive though becuase when i was just messing around earlier i went to the "partition editor" under the administration tab, it showed a drive (137 gb free, which is my windows drive) and the drive was labeled /dev/sda1. although my windows drive has two partitions (sda1, sda2) is it a problem that im trying to only mount a partition of the drive, like is it possible that i should be trying to mount just sda as opposed to sda1?

---

### Post by drelyn86 on 2008-10-28
> **m4778 said:**
> It then says "df: cannot read table of mounted file systems: Stale NFS file handle"  im pretty sure that /dev/sda1 is the windows drive though becuase when i was just messing around earlier i went to the "partition editor" under the administration tab, it showed a drive (137 gb free, which is my windows drive) and the drive was labeled /dev/sda1. although my windows drive has two partitions (sda1, sda2) is it a problem that im trying to only mount a partition of the drive, like is it possible that i should be trying to mount just sda as opposed to sda1?

Mounting the partition is the correct way to do it. 

The problem is that sda1 and sdb1 could switch on boot without you knowing it... it's somewhat dynamic, for some reason. 
I had a problem with my hard drives doing this, and I had to start mounting by UUID. The UUID is a unique number for every partition and will never change.

```
ls /dev/disk/by-uuid/
```
that code should give you an output of all your disks' UUID

You might want to compare these UUIDs with those that are mounted via your fstab file

```
cat /etc/fstab
```

I'd imagine that your windows drive UUID is the one that's not listed in fstab.

If any of this checks out (if you have a UUID not in fstab), let me know the UUID and we'll see what we can do from there.

---

### Post by m4778 on 2008-10-28
I tried all that and this is what i came up with, im not really sure what it means.

ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/
0005-81BB         454A21B375633993  aeef4a65-2616-49a2-b456-bacb833257e9
2C88743C8874071C  4902-7E9A
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$

---

### Post by drelyn86 on 2008-10-28
> **m4778 said:**
> I tried all that and this is what i came up with, im not really sure what it means.

ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/
0005-81BB         454A21B375633993  aeef4a65-2616-49a2-b456-bacb833257e9
2C88743C8874071C  4902-7E9A
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$

k... what method did you use to put Ubuntu on the flash drive? It looks like what you're running is the equivalent to the liveCD.

---

### Post by m4778 on 2008-10-28
i booted using a livecd, then i ran the command "wget pendrivelinux.com/downloads/u810/u810.sh" and then the command "chmod +x u810.sh && sh u810.sh"

basically i followed the directions on this page, [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

but it is saving back to the flash drive and it retains all settings and programs that i install so it doesn't seem to be running like the live cd.
I'm not sure maybe i have completely overlooked something.

---

### Post by m4778 on 2008-10-28
and if the way i loaded it won't work, what is the correct way to do it.

---

### Post by alienprdkt on 2008-10-28
could try force:

in fstab:
/dev/sda? /media/windows ntfs-3g defaults,force 0 0

if does not work could try:

#sudo ntfs-3g /dev/sda? /media/windows -o force

in both cases where "?" is your actual drive you want to mount

---

### Post by drelyn86 on 2008-10-28
hmm... not really sure how I can help you with that.
I guess a good starting point would be getting ntfs read/write support (assuming you don't have it)... the only thing I can do is direct you to another thread

[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

