---
title: "&quot;grub&gt; find /boot/grub/stage1&quot; not working!"
date: 2008-09-17
forum: General Help
---

### Post by Nanthiel on 2008-09-17
Hello there!

I've the following problem: My GRUB's not there anymore.

After reinstalling Ubuntu, it showed Error 22 (didn't even show a menu) and I was unable to start any OS. I also have Windows XP installed. After using the 'Super Grub Disk', I managed to revive XP, but now it automatically starts XP and ignores Ubuntu. All the auto options (for Linux) in Super Grub Disk don't work due to Error 15: File Not Found.

I have searched these forums, but most (if not all?) of them use a solution where "grub> find /boot/grub/stage1" is involved. The problem is, this command does not work for me, it shows the above mentioned error, Error 15.

Please help! What must I do?


(NOTE: I have tried reinstalling Ubuntu, and with no effect.)

---

### Post by bodhi.zazen on 2008-09-17
Boot a live CD and show us the output of :

```
sudo fdisk -l
```

Which is your Ubuntu partition ?
Which is your boot partition ?

lets mount your /boot partition and take a look-see

---

### Post by Nanthiel on 2008-09-18
> **bodhi.zazen said:**
> Boot a live CD and show us the output of :

```
sudo fdisk -l
```

Which is your Ubuntu partition ?
Which is your boot partition ?

lets mount your /boot partition and take a look-see


So, the output is:

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x367c367b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101       20023   119868997+   5  Extended
/dev/sda5            5101       15192    81063958+   7  HPFS/NTFS
/dev/sda6           15193       19819    37166346   83  Linux
/dev/sda7           19820       20023     1638598+  82  Linux swap / Solaris
```

I knew already, that my Ubuntu partition was sda6. But I don't know which my boot partition is. The last time I installed Ubuntu, GRUB was set to install on "/dev/sda" - I presume that means it's on, in GRUB's lingo, "(hd0)", but that's the actual disk, not a partition.

So is my "/boot" not an actual partition? And if it is, how do I mount it?

**EDIT:** never mind... yes, silly me. There's actually a "*" at the boot... so, "/dev/sda1" it is. (Or GRUB's (hd0,0), right?)

**EDIT2:** As far as I can tell, "mounting" a partition means "opening" it in Places? There's a boot.ini in there, is it of importance? What do I do?

**ADD:** The "boot.ini" file contains:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by bodhi.zazen on 2008-09-18
I see you are getting a little confused re: boot partition.

Your bios must have at least 1 partition marked as bootable, this is the * in your fdisk table.

You do not appear to have a /boot partition for Linux, so /boot is on / which is /dev/sda6

so , on the live CD,

```
sudo mount /dev/sda6 /mnt
```

Now ls /mnt => you should see a boot directory. list that :

```
sudo ls /mnt/boot
```

From the live CD you can install grub :

```
sudo grub
```

you will get a grub prompt:

> grub>

At the grub prompt enter :

```
root (hd0,5)
setup (hd0)
exit #or it may be quit
```

Assuming you have no error messages you can now reboot.

---

### Post by Nanthiel on 2008-09-18
> **bodhi.zazen said:**
> Now ls /mnt => you should see a boot directory. list that :

```
sudo ls /mnt/boot
```


Thanks for the quick reply, but I'm not quite sure what I must do here?

When I enter "sudo mount /dev/sda6 /mnt", nothing "really" happens (I guess it invisibly mounts the partition?).
When I try, plainly, "sudo ls /mnt/boot", it shows a couple of files (the ones under the 'boot' dir on sda6 **=EDIT!=** Seems there's more sets of these; /boot and /mnt/boot. Duh... sorry)
Then, once I tried installing GRUB, right after the stuff above, I got the error:
```
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

Sorry for being annoying, but I just moved from Windows to Linux, like, yesterday... and I guess I'm pretty persistent that I haven't given up yet as a newbie. >.<

---

### Post by bodhi.zazen on 2008-09-18
In Linux if a command is successful you see nothing.

Can you post the output of :

```
sudo ls /mnt/boot
```

And your grub commands are off.

```
root (hd0,5)
setup (hd0)
```

---

### Post by Nanthiel on 2008-09-18
> **bodhi.zazen said:**
> In Linux if a command is successful you see nothing.

Can you post the output of :

```
sudo ls /mnt/boot
```

And your grub commands are off.

```
root (hd0,5)
setup (hd0)
```

I apologise. I did write "root (hd0,5)", I just did not post it, since it seemed to work without problems.

Anyway, the output you requested:
```
sudo ls /mnt/boot
abi-2.6.24-19-generic	      memtest86+.bin
config-2.6.24-19-generic      System.map-2.6.24-19-generic
initrd.img-2.6.24-19-generic  vmlinuz-2.6.24-19-generic

```

---

### Post by bodhi.zazen on 2008-09-18
Well, you do not have any grub files in your boot directory.

At the grup prompt :

```
setup (hd0.5)
root (hd0,5)
setup (hd0)
```

---

### Post by Nanthiel on 2008-09-18
> **bodhi.zazen said:**
> Well, you do not have any grub files in your boot directory.

At the grup prompt :

```
setup (hd0.5)
root (hd0,5)
setup (hd0)
```

What happened (already after "setup (hd0,5)"):
```
grub> setup (hd0,5)
setup (hd0,5)

Error 12: Invalid device requested

```

---

### Post by caljohnsmith on 2008-09-18
Unfortunately, doing the "root" and "setup" commands in the Grub CLI will not create Grub's system files like stage1, stage1_5, stage2, device.map, etc. if those files don't exist (I sure wish they would have designed it that way though :)). I think what you are after is the "grub-install" command, which will create those files, and also install Grub to the MBR at the same time. Nanthiel, do the following while sda6 is still mounted on /mnt:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
That should create all of Grub's system files in /mnt/boot/grub (your Ubuntu partition) except for menu.lst. To create a menu.lst, first you will probably need an internet connection from your Live CD, because most likely you will have to install the "grub" package (I doubt it is all ready installed in your Ubuntu partition, but it might be). Here's the steps:
```

sudo mount -o bind /dev /mnt/dev
sudo mount -t proc none /mnt/proc
sudo chroot /mnt
apt-get install grub
update-grub
exit
```
That should create a menu.lst in your sda6 /boot/grub directory. Reboot, and tell us what happens on start up.
[COLOR="Blue"]
EDIT: Many thanks to forum member meierfra for pointing out that you also need to bind the /dev directory and also mount the proc directory in order to allow update-grub to correctly determine the partitions. I've included the changes above in case anyone stumbles on this thread in the future.[/COLOR]

---

### Post by Nanthiel on 2008-09-18
> **caljohnsmith said:**
> Unfortunately, doing the "root" and "setup" commands in the Grub CLI will not create Grub's system files like stage1, stage1_5, stage2, device.map, etc. if those files don't exist (I sure wish they would have designed it that way though :)). I think what you are after is the "grub-install" command, which will create those files, and also install Grub to the MBR at the same time. Nanthiel, do the following while sda6 is still mounted on /mnt:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
That should create all of Grub's system files in /mnt/boot/grub (your Ubuntu partition) except for menu.lst. To create a menu.lst, first you will probably need an internet connection from your Live CD, because most likely you will have to install the "grub" package (I doubt it is all ready installed in your Ubuntu partition, but it might be). Here's the steps:
```
sudo chroot /mnt
apt-get install grub
update-grub
exit
```
That should create a menu.lst in your sda6 /boot/grub directory. Reboot, and tell us what happens on start up.

Awesome, these steps apparently did SOMETHING. The Grub files are now where they were supposed to be.

I also did the "grub>root" and "setup" thing now, all successfully! I will restart now, I have a good feeling about this now. =)

---

### Post by Nanthiel on 2008-09-18
So, apparently, this fixed something. The grub menu is there. But!

1. the Grub menu is not showing my Windows installation
and
2. when trying to run the Ubuntu installation, I get "Error 17: Cannot mount selected partition"

Any ideas?


EDIT: The entries in the current menu.lst are:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


I guess the roots are wrong?

---

### Post by caljohnsmith on 2008-09-18
> **Nanthiel said:**
> So, apparently, this fixed something. The grub menu is there. But!

1. the Grub menu is not showing my Windows installation
and
2. when trying to run the Ubuntu installation, I get "Error 17: Cannot mount selected partition"

Any ideas?
No problem, it just means the "update-grub" command probably guessed the wrong entries for Ubuntu, and left out any entries for Windows. Please mount your sda6 partition again from the Live CD and print the menu.lst:
```
sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst

```

---

### Post by Nanthiel on 2008-09-18
The code you gave throws out the same info in my EDIT above.

Here it is again, if there are any minor details I missed.
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


---

### Post by caljohnsmith on 2008-09-18
Looks like update-grub did a terrible job figuring out which partition your Ubuntu is on. :roll: First, change all the "root (hd0,0)" to "root (hd0,5)". Then run:
```
sudo blkid | grep sda6
```
And use whatever sda6's UUID is as follows:
```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root [COLOR="Blue"](hd0,5)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic [COLOR="Blue"]root=UUID=51c6525c-a30b-49c5-b67d-7a83626c5049[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```
But of course use your sda6 UUID, not the one above. Also, to boot Windows:
```
title Windows
root (hd0,0)
makeactive
chainloader +1
```
Add that to the end of your menu.lst, reboot, and let me know what happens.

---

### Post by Nanthiel on 2008-09-18
Quick problem:
I don't have permissions to save the menu.lst

Also, should I add the root=UUID=.... thing to the "(recovery mode)" Ubuntu, too? (I guess I should?)

---

### Post by caljohnsmith on 2008-09-18
> **Nanthiel said:**
> Quick problem:
I don't have permissions to save the menu.lst

Also, should I add the root=UUID=.... thing to the "(recovery mode)" Ubuntu, too? (I guess I should?)
From the Live CD while sda6 is mounted on /mnt, just do:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And yes, change the (hd0,0) and UUIDs for all your Ubuntu entries in menu.lst. :)

---

### Post by Nanthiel on 2008-09-18
Thaaanks! It works now. =)

My joy in Linux is back. ^_^

---

### Post by caljohnsmith on 2008-09-18
> **Nanthiel said:**
> Thaaanks! It works now. =)

My joy in Linux is back. ^_^
Great you're up and running again. Cheers and have fun. :)

---

### Post by Chirola on 2010-03-01
Hello
My problem is very similar with the one discussed here.

I'm trying to restore the grub using a ubuntu 9.10 live cd.
I have two partitions in my computer, and i used the partition that contained Vista to install windows 7. 
Now, i'm trying to restore the grub so that i can also boot ubuntu.

When i do "sudo fdisk -l", the output is:

[B]Disk /dev/sda: 120.0 GB, 120034123776 bytes
138 heads, 12 sectors/track, 141571 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes
Disk identifier: 0x0fb3cfe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6185       91128    70332416    7  HPFS/NTFS
/dev/sda2           91133      141568    41760967+   f  W95 Ext'd (LBA)
/dev/sda5          132411      141568     7582648+  82  Linux swap / Solaris

[/B]I'm pretty sure that the filesystem created when i've installed ubuntu was extended 3.
I don't recognize "W95 Ext'd (LBA)". Is this a other type of filesystem?

I already tried to use super grub disk, but when i'm in "grub>" and i do: "find /boot/grub/stage1" the output is the same as Nanthiel: "Error 15:File not found"

Right now, i'm using the live cd, and when i do "sudo grub", 
i get "sudo: grub: command not found"

If you can help me to restore grub, i would be grateful;)

PS: Sorry for the possible, bad english.

**EDIT : **I tried to do: "sudo apt-get install grub" 
but i get this
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I write in the console: "sudo dpkg --configure -a" then " sudo apt-get install grub"
and the output is:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `wireless-crda': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

---

### Post by oldfred on 2010-03-01
Chirola welcome to the forums, but this thread is almost 2 years old and really just available for reference. It would have been much better for you to start a new thread with your problem.  

Your problem is not like this thread as you have(?) Karmic with grub2. The ways to fix grub2 all not at all like grub legacy and in fact mixing them makes the fixes even more difficult.

The larger issue is your fdisk listing shows no linux partition. The 
sda1 is your windows
sda2 is the extended partition which is just a container for logical partitions
sda5 is a logical partition (in sda2) that is swap.
It does look like sda2 was bigger than just swap so it may have had another partition.

I think you need to delete swap and sda2 and reinstall unless you are sure you have another partition somewhere?? 

If you still have problems please post to a new thread with the title clearing stating your problem.

---

### Post by dioxip on 2010-03-29
> **caljohnsmith said:**
> Unfortunately, doing the "root" and "setup" commands in the Grub CLI will not create Grub's system files like stage1, stage1_5, stage2, device.map, etc. if those files don't exist (I sure wish they would have designed it that way though :)). I think what you are after is the "grub-install" command, which will create those files, and also install Grub to the MBR at the same time. Nanthiel, do the following while sda6 is still mounted on /mnt:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
That should create all of Grub's system files in /mnt/boot/grub (your Ubuntu partition) except for menu.lst. To create a menu.lst, first you will probably need an internet connection from your Live CD, because most likely you will have to install the "grub" package (I doubt it is all ready installed in your Ubuntu partition, but it might be). Here's the steps:
```

sudo mount -o bind /dev /mnt/dev
sudo mount -t proc none /mnt/proc
sudo chroot /mnt
apt-get install grub
update-grub
exit
```
That should create a menu.lst in your sda6 /boot/grub directory. Reboot, and tell us what happens on start up.
[COLOR="Blue"]
EDIT: Many thanks to forum member meierfra for pointing out that you also need to bind the /dev directory and also mount the proc directory in order to allow update-grub to correctly determine the partitions. I've included the changes above in case anyone stumbles on this thread in the future.[/COLOR]


You are the greatest!!!!

I´ve been fighting with grub loader the past 4 hours and finaly I found a guide that worked, after I resized my root partion!!! :D:D

---

### Post by levis lover on 2010-07-11
My problem is very similar to these..
```

1. sudo grub-install --root-directory=/mnt /dev/sda
2. sudo mount -o bind /dev /mnt/dev
3. sudo mount -t proc none /mnt/proc
4. sudo chroot /mnt
5. apt-get install grub
6. update-grub
7. exit

```
First four commands run smoothly but the fifth one i.e. ```
apt-get install grub
``` yields this output
```

Err http://in.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
What am i missing here ?

---

### Post by bodhi.zazen on 2010-07-11
> **levis lover said:**
> My problem is very similar to these..
```

1. sudo grub-install --root-directory=/mnt /dev/sda
2. sudo mount -o bind /dev /mnt/dev
3. sudo mount -t proc none /mnt/proc
4. sudo chroot /mnt
5. apt-get install grub
6. update-grub
7. exit

```First four commands run smoothly but the fifth one i.e. ```
apt-get install grub
``` yields this output
```

Err http://in.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```What am i missing here ?

I think your problem is you are following the advice of a very old thread.

Ubuntu now uses grub 2 , see :

[Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")

---

### Post by Carrera993 on 2011-05-16
_***[COLOR=Lime]PROBLEM SOLVED !!!![/COLOR]***_

I want to thank [COLOR=Blue]_***Caljohnsmith***_[/COLOR] so much for the explanation of this problem.

Without your help i would be stuck BIGGGGtime and would be booting only xp .

I am so glad this fixed everything and i can use xp and ubuntu.


Superthanks !

Great FORUM


grts Carrera993

---

