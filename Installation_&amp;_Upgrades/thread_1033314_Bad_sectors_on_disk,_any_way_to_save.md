---
title: "Bad sectors on disk, any way to save?"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by airjaw on 2009-01-07
Hey guys, I have a 120gb Disk with bad sectors on it which I am trying to install Ubuntu on. Currently its NTFS but I was hoping to partition it using gparted and get 8.10 running.

Well, I have bad sectors (at least 174 of them) and I was wondering what advice people have regarding my options in saving the disk.
Ubuntu liveCD told me to run chkdsk /f /r a few times (which I have done) and I'm still getting the bad sector problem. 

I tried using terminal and doing 
sudo ntfsresize /dev/sda1 --bad

but it just said that NTFS was fine already.

Is there any hope for my hard disk?  And what is the next step (if any) to go on fixing it?

Thanks.

---

### Post by theinnercityhippy on 2009-01-07
linux has a powerful disk checking utility called fsck. During the install of ubuntu, when you format the drive to the required ext2/3 format (which can be done automatically very well by the installer) it will identify any bad sectors and try to repair them. If this is not possible it will avoid them altogether.

What you didn't state is whether you are planning a proper install, over or alongside windows on its own partition, or are planning to use Wubi to install it within windows on the NTFS drive.

I would always recommend that if you want to dual boot the computer, keeping the windows system alongside Ubuntu, to repartition your drive and install it onto its own dedicated partition. More information can be found here;

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope this helps you. Please feel free to send me a message or reply to this thread if you require further help with the install process

-JimDog*-

---

### Post by airjaw on 2009-01-07
Hello, thanks for the help.
I was hoping for a dualboot setup, so I want to partition my 120 GB into an NTFS drive and an ext3 drive.

My question was more related to the bad sectors on my hard drive -- and then what the best way to actually go through with the partition, with the bad sectors and all.  Right now liveCD gparted won't let me resize the drive due to the bad sectors and i'm not sure how to go forward from here.
Thanks!

---

### Post by theinnercityhippy on 2009-01-07
OK we're going to have to take a brief foray to the command line.

Note: By far te best live CD to use for this operation is something called Knoppix. It is renowned as the "Swiss Army Knife" of linux distributions and contains some very powerful tools for all manner of rescue and recovery operations. A live CD can be downloaded from here:

[www.knoppix.net](www.knoppix.net)

This contains everything you will need by default and so I would recommend going to the site, downloading and burning the live cd and booting from it. Then open a terminal (the black icon on the taskbar) and run the following

root@knoppix:~# blkid

This will give you the name of the windows partition eg /dev/sda1 or /dev/hda1

then type

```
root@knoppix:~# mkdir /mnt/windows
```

```
root@knoppix:~# mount -t ntfs /dev/sda1 /mnt/windows
```

```
root@knoppix:~# fsck.ntfs -p -c -y /dev/sda1
```

The first line makes a directory to mount the drive in, the second mounts it (-t is the type) and the third tells it to check the drive, test for bad blocks and add them to the list of bad blocks and assume yes to all questions.

Hopefully this will solve the problem.

From Ubuntu you first have to install a few extra programs to your live environment.

Open a terminal by going to 

Applications > Accessories > Terminal

This will give you a command prompt. Ensure that the disk is mounted, in your file manager you will see an icon. Double click on it. Then in the terminal type the following
```

user@ubuntu:~$ sudo apt-get install ntfsprogs ntfs-3g
```
```

user@ubuntu:~$ blkid
```

To give you the name of the partition as above

```
user@ubuntu:~$ sudo fsck -y -c -p /dev/sda1
```

change /dev/sda1 to the name given to you by the blkid command. When this is done, try running the installer again and post your results.

If this fails, I would suggest running 

```
C:/ chkdisk
```

from within Windows at the command prompt immediately prior to installing, and make sure that the drive has been defragmented before you try.

Good Luck

-JimDog-

---

### Post by airjaw on 2009-01-07
Thanks for the help.
I'm downloading knoppix CD now. Looks like it will take 10 hours though.
I will report back when it is done.

---

### Post by theinnercityhippy on 2009-01-07
No probs. make sure its the 700mb cd and not the dvd you're downloading. When you get a bit more confident with Linux, it's well worth exploring knoppix a little more. O'Reilly publish a fantastic book called Knoppix Hacks which I would highly recommend.

-JimDog*-

---

### Post by airjaw on 2009-01-07
haha funny, I did download the DVD..

---

### Post by theinnercityhippy on 2009-01-07
> **airjaw said:**
> haha funny, I did download the DVD..

How are you getting on, any joy? sorry for the late reply, been doing some shell scripting and had my head in the clouds :-)

---

### Post by airjaw on 2009-01-09
thanks for checking back in.  i haven't tried anything yet altho the CD is ready. will let you know how it goes.

do you mind giving me a short explanation of what fsck does?
and why do I run it again in ubuntu livecd before installation?
also, 
I'm interested in trying out different distros on that hard drive.. will i have to do fsck custom command everytime I try to install something? Can my hard drive's bad sectors be permanently taken care of or can i only kinda patch it up everytime I install an OS?

Thank you.

---

### Post by Herman on 2009-01-09
Data on a hard disk is stored as combinations of tiny positive and negative magnetic fields or flux. Bad blocks are sectors in the hard disk that are losing their magnetic properties to such an extent that they can no longer be trusted to store data reliably.

New hard disks have some bad blocks and they also have an area of spare sectors that the hard disk's controller will silently swap for the bad ones. Gradually more bad blocks appear from time to time as the hard disk ages, and those are also silently swapped for spare ones by the hard disk controller.

Only after the hard disk's supply of spare sectors runs out, do bad blocks begin to become apparent in the file system and to the operating system's programs like fsck or the badblocks program. 

When that starts to happen it's best to back up all your data and go buy a new hard disk, because your hard disk is on it's last legs.
You can keep it going a little longer by running programs like fsck, but fsck doesn't 'fix' bad blocks, it just maps them out, (tells the file system where they are so it can work around them).

It's anybody's guess how much longer a hard disk like that will last. It's probably okay to keep using it as long as you don't care about storing any important data on it.
You can use it for trying out operating systems, but don't complain if the operating systems you are testing perform poorly and have all kinds of bizarre problems.
Really, you are probably wasting your time and you should really go and buy a better hard disk or find a free one somewhere that's in better condition.
I hate to sound a sour note, but that's what I think.

Regards, Herman :)

---

### Post by airjaw on 2009-01-09
Thank you! very informative..

I don't have any money right now to buy a new one but I'll ask around, maybe I can pick up a used 20gb for free.

---

### Post by Mike.lifeguard on 2009-04-08
I'm having the same issue.

> **theinnercityhippy said:**
> 
```

user@ubuntu:~$ sudo apt-get install ntfsprogs ntfs-3g
```
didn't do anything for me: 0 upgraded, 0 newly installed, 0 to remove, 0 not upgraded.

> **theinnercityhippy said:**
> 
```

user@ubuntu:~$ blkid
```
doesn't return anything at all (though I know it's /dev/sda1)

> **theinnercityhippy said:**
> 
```
user@ubuntu:~$ sudo fsck -y -c -p /dev/sda1
```
fsck fails (fsck.ntfs not found).

> **theinnercityhippy said:**
> 
```
C:/ chkdisk
```
Did that previously (well, ```
chkdsk /f /r
```

---

### Post by Mike.lifeguard on 2009-04-10
See [https://lists.ubuntu.com/archives/ub...il/180136.html](https://lists.ubuntu.com/archives/ub...il/180136.html) (& possibly my previous posts in that thread) for my solution here.

---

