---
title: "[SOLVED] How do I partition the hard drive on ubuntu 7.10"
date: 2008-09-24
forum: General Help
---

### Post by tehforum on 2008-09-24
How do I partition the hard drive on ubuntu 7.10, so I can set up a Linux partition, and a Windows XP partition, so i can use XP as well.

I have ubuntu 7.10 installed on my computer right now. But I do not know how to partition the hard drive, so you can install Windows on there.

Would you please advise me on how to partition my hard drive, and what to do after that (I presume you just put in the windows xp installation cd).

Thanks.

---

### Post by indytim on 2008-09-24
Have you searched the forums?  There are literally hundreds of post and threads on the subject.

IndyTim

---

### Post by tehforum on 2008-09-24
Yes, I found this

sudo apt-get install gparted

But just wanted ubuntu 7.10 specific instructions so I don't get anything wrong.

Now I went System > Administration > Partition edtior

And it opened 'GParted', and for a few minutes now it says 'Scanning all devices'.

How long does it take?

---

### Post by tehforum on 2008-09-24
Alright, it has finished scanning.

And it has found

ext3
linux-extended
linux-swap

Now, I found this [http://ubuntuforums.org/showpost.php?p=5796853&postcount=13](http://ubuntuforums.org/showpost.php?p=5796853&postcount=13)

And it is telling me that I need a LiveCd to follow his instructions, are they true?

---

### Post by tehforum on 2008-09-24
Sorry guys and gyals for the triple post, however I am SO close to finishing the install now.

Basically, I need to edit the menu.lst file, and when I go into the terminal from the live cd
```

sudo gedit /boot/grub/menu.lst

```

So I can edit the file, and then it is blank.

[http://ubuntuforums.org/showpost.php?p=5755108&postcount=2](http://ubuntuforums.org/showpost.php?p=5755108&postcount=2)

I found that post saying on how to mount my partition.

So I went to System > Administration > Partition Editor, and I looked at my partition, it was called sda2

So I put into the Terminal

```

sudo mount /dev/sda2 /mnt

```

Like it said in the aforementioned post, and it came up with.

```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt ntfs-3g defaults,force 0 0


```

Any help is much appreciated!

Thanks.

----------------

I tried

sudo fdisk -l 

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a446a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       49396   396773338+  83  Linux
/dev/sda2   *       49397       60092    85915620    7  HPFS/NTFS
/dev/sda3           60093       60801     5695042+   5  Extended
/dev/sda5           60093       60801     5695011   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

If that is any help to you, thanks.

---

### Post by tehforum on 2008-09-25
Sorry to be a pain, and bump the thread.

---

### Post by mikewhatever on 2008-09-25
Why are you trying to mount the NTFS partition? Grub is not there, it's on sda1, however, that's not the way to go. Having reinstalled Windows, you've overwritten the MBR and now need to reinstall grub boot loader.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#Using%20the%20Ubuntu%20Desktop/Live%20CD](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#Using%20the%20Ubuntu%20Desktop/Live%20CD)

---

### Post by tehforum on 2008-09-25
So it is normal for ubuntu to load up automatically without the live cd in?

But what about my steps outlined above?

---

### Post by tehforum on 2008-09-26
A man has got to do, what he's got to do it

Sorry.

---

### Post by oilchangeguy on 2008-09-26
this is not rocket science. simply use gparted to shrink your ubuntu install to the desired size. install windows, then use the live cd to reinstall grub. and learn to use the search bar at the upper right of the screen. and google. AND STOP BUMPING YOUR THREAD!!!!

---

### Post by mikewhatever on 2008-09-26
> **tehforum said:**
> So it is normal for ubuntu to load up automatically without the live cd in?

But what about my steps outlined above?

Yes, it's normal. Perhaps you should re-state your objectives in the next bump, because I don't understand them.

---

### Post by tehforum on 2008-09-26
Hi, it may not be rocket science to you, but it maybe for me, because I don't want to stuck with sitting duck (a.k.a my computer)

I will now follow those provided in that article, and I will report back with my findings.

Thank you.

---

### Post by tehforum on 2008-09-28
Hi,

Thanks, I got it working!

---

