---
title: "How to increase swap file size?"
date: 2008-11-13
forum: General Help
---

### Post by maxbini on 2008-11-13
Hi
I've succesfully installed Ubuntu via Wubi in 10 minutes on my office laptop. The purpose is: test every applications to replace Windows' ones before repartition the disk, and Wubi is the best way to do this.

I have a problem when trying to installing Oracle: it needs a swap partition of 1Gb at least, and Wubi creates a 512Mb one.
So I've tried as suggested by copying (in Windows) a big file on the original swap.disk, and reboot ubuntu.
The first attempt was partially a success: swap size has increased to 986Mb, but it was not enough.

So I've repeated the operation using a bigger video file: copied onto swap.disk to replace it, and reboot Ubuntu

This time my Ubuntu(wubi) doesn't load swap file anymore, talking of a "swap signature missing" at the boot. So I have 0 Mb of swap file, and I didn't solved the problem.

Does anyone knows how to get rid of this problem?

Max

---

### Post by Orlsend on 2008-11-13
Why not try this?

[I]"Another dirty trick (but working) is to copy any other file of the desired size to c:\wubi\disks and rename it "root.disk", "home.disk", "swap.disk" or "extra.disk". That's the wubi equivalent of buying (and installing) a new hard disk ;)

If you are running Windows XP (may work in Windows 2000 and Vista as well) you can create a file by using the fsutil that is included with Windows. The command format is fsutil file createnew filename filesize where filename is the file you wish to create and filesize is the size of the file to be created in bytes."[/I]

For all your Wubi needs:
[URL="https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?"]
https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?[/URL]

Enjoy your Swap!

---

### Post by maxbini on 2008-11-13
> **Orlsend said:**
> Why not try this?

[I]"Another dirty trick (but working) is to copy any other file of the desired size to c:\wubi\disks and rename it "root.disk", "home.disk", "swap.disk" or "extra.disk". That's the wubi equivalent of buying (and installing) a new hard disk ;)

If you are running Windows XP (may work in Windows 2000 and Vista as well) you can create a file by using the fsutil that is included with Windows. The command format is fsutil file createnew filename filesize where filename is the file you wish to create and filesize is the size of the file to be created in bytes."[/I]



As i said:

> So I've repeated the operation using a bigger video file: copied onto swap.disk to replace it, and reboot Ubuntu

I already tried to create a swap.disk from a big file, and from scratch via fsutil too.
Also restoring the original 500mb swap.disk doesn't help, the system is always starting without mounting a swap.

I'm beginning to think the problem resides in a fragmented NTSF. I'm going to start defragment now.

---

### Post by Orlsend on 2008-11-14
Woops din't read, Yes defragmenting it vital when booting.

Please tell us if it does not work.

---

### Post by uncaspi on 2008-11-14
You can create a new swap file in Linux doing this. I don't know if it works in wubi, but in other distros it works. I did this also in Ubuntu-8.04, but here I installed Ubuntu in a partition and not wubi. I forgot to create a swap partition when I installed. Try this.

dd if=/dev/zero of=swapfile bs=1024 count=262144
/sbin/mkswap
/sbin/swapon -a

Check man dd for the size(count) According to man dd count is blocks of bs bytes. so in the example this should be a swapfile of a little more than 262 Mb.:)

---

### Post by maxbini on 2008-11-17
> **Orlsend said:**
> Woops din't read, Yes defragmenting it vital when booting.

Please tell us if it does not work.

Hi

It doesn't work: I've tried from a fresh (re)installation recreating a 1Gb swap file in different ways  (dd included) and everytime Ubuntu miss mounting the swap file. And this time restoring the original 512Mb one didn't restore swap.
Disk is defragmented enough this time.

Now I would like to try another direction, so the question is:

is there a way to specify swap size when installing Ubuntu via Wubi? Wubi just asks for the total size: if I put 6gb, it will reserve 5,5Gb for the OS and 0,5 for swap, without querying for a different choice.

---

### Post by EV500B on 2008-11-17
Desactivate your current swap using the swapoff command. Try to open cfdisk, delete your current swap partition and create a new one of x size and note its hda/hdb number. Then write the changes and exit.
For example, it in hdb2 : Type mkswap /dev/hdb2
                   Then        : Type swapon /dev/hdb2
It should work.        (I guess)

---

### Post by maxbini on 2008-11-17
> **EV500B said:**
> Desactivate your current swap using the swapoff command. Try to open cfdisk, delete your current swap partition and create a new one of x size and note its hda/hdb number. Then write the changes and exit.
For example, it in hdb2 : Type mkswap /dev/hdb2
                   Then        : Type swapon /dev/hdb2
It should work.        (I guess)


Hi

In the meantime you was wroting I realized which was the problem by looking in /var/log/syslog:

"Unable to find swap-space signature"

So I tried this way:

$ sudo su
$ cd /host/ubuntu/disks
$ cp swap.disk bigswap.disk
$ cat swap.disk>>bigswap.disk
$ cat swap.disk>>bigswap.disk
$ mkswap bigswap.disk
$ swapoff -a
$ vi /etc/fstab --> and modify swap.disk to bigswap.disk
$ swapon bigswap.disk
$ free -m
             total       used       free     shared    buffers     cached
Mem:           991        969         22          0        157        196
-/+ buffers/cache:        614        377
Swap:         1430          0       1430

And now it's working

It seems that it's not enough to recreate a big file to make it become the new swap file, you also need to format it by the mkswap command.

Thank you for your suggestions :)

---

### Post by dhuljev on 2008-11-20
Hello everyone, I am having a similar issue.

By any chance would it be possible to simply run Partition Magic in a Windows installation and simply edit the partition size for the swap file directly?

---

### Post by EV500B on 2008-11-20
Oh, sorry that's not swap file, It's swap partition.

---

### Post by dhuljev on 2008-11-20
> **EV500B said:**
> Oh, sorry that's not swap file, It's swap partition.

Heh yeah I meant swap partition.

Is there a way to do with partition magic or hopefully some kind of similar freeware?

---

### Post by EV500B on 2008-11-21
> **dhuljev said:**
> Heh yeah I meant swap partition.

Is there a way to do with partition magic or hopefully some kind of similar freeware?
Huh, similar freeware. You mean in windoze or any other could do the thing?
So if you meant swap partition, you can use Gparted(if you have any spare cd) or you can use my favourite BootitNG(The partition manager is free but the boot manager isn't).
BootitNG: just install it in a floppy disk and boot from newly made media.
The link is [www.terabyteunlimited.com/bootit-next-generation.htm]("http://ubuntuforums.org/www.terabyteunlimited.com/bootit-next-generation.htm")

---

