---
title: "[SOLVED] fsck died with exit status 8 ....fail!"
date: 2008-10-24
forum: Hardware
---

### Post by lrs52200 on 2008-10-24
uh......that doesn't sound good.  

I just re-partitioned my disks with gparted live cd, and reinstalled the O.S. this morning & ran all of the updates (Ubuntu 8.04 LTS). The updates required restarting on a few occasions and everything was fine.  I shut down my machine this evening, then remembered something I wanted to view online so I started my machine back up and here's what it said:

  fsck 1.40.8 (13-Mar 2008)
  /dev/sda1: clean, 25373/3630144 files, 632105/7259364 blocks...
  ....done
  starting early  crypto disks...
  ....done
  starting remaining crypto disks...
  ...done
  checking file systems...
  1178
  fsck 1.40.8 (13-Mar-2008)
  fsck. ext2: unable to resolve 'UUID=0b529fb0-9ff4-4bf0-8c0c-424a17a06c33
  fsck. ext2: unable to resolve 'UUID-c167d129-83d9-423a-8b89-fb099fob8abf
  fsck died with exit status 8
  ...fail!
  file system check failed
  A log is being saved in /var/log/fsck/checkf if that location is 
      writable
  Please repair the file system manually
  A maintenance shell will now be started.
  Control-D will terminate this shell and resume system boot
  BASH: no job control in this shell
  BASH: groups: command not found
  BASH: dircolors: command not found
  root:pamela-desktop:`#

The machine never rebooted - it's just stuck there like that.  I haven't tried to shut it down yet......I figured I'd better call in the Zen Master Ubuntu Fixer-Upper first!   :)

It sounds like I'm in trouble.........can it be fixed?  Does anyone know what I should do?  BTW - I'm brand new at this linux thing.  As I said in an earlier post, I'm barely past the conception stage of noob...

---

### Post by prshah on 2008-10-24
> **lrs52200 said:**
> 
  fsck 1.40.8 (13-Mar-2008)
  fsck. ext2: unable to resolve 'UUID=0b529fb0-9ff4-4bf0-8c0c-424a17a06c33
  fsck. ext2: unable to resolve 'UUID-c167d129-83d9-423a-8b89-fb099fob8abf
  fsck died with exit status 8
  ...fail!


Looks like your UUIDs are wrong; from the maintenance shell prompt, give the below commands for more information:```

cat /etc/fstab
blkid
```

You can also try just pressing Ctrl+D to see if it proceeds normally.

---

### Post by lrs52200 on 2008-10-25
First, thank you very much for trying to help me.  This is what it said:

cat etc/fstab

# /etc/fstab: static file system information
#
#<file system>  <mount point>  <type>  <options>        <dump>      <pass>
proc             /proc          proc   defaults           0           0

#/dev/hda1  --converted during upgrade to edgy
UUID=7be2862d-3274-4dde-8c8d-b5397f78b73d  /ext3  defaults, errors=remount ro 0  1

#/dev/hda4  --converted during upgrade to edgy
UUID=0b529fb0-0ff4-4bf0-8c9c-424a17a06c33  /home  ext2  defaults

#/dev/hda5 --converted during upgrade to edgy
UUID-c167d120-83d9-423a-8b89-fb099f0b8abf  /usr  ext2  defaults  0  2

#/dev/hda3 - converted during upgrade to edgy
UUID-88b2fe5d-cfba-4628-8f7d-3fafb70-ead2e none  swap  0  0

/dev/hdc  /media/cdrom0  udf, iso9660  user, noauto  00

root@pamela-desktop: ~ # blkid

[66.169338]  buffer  I/O  error on device sda4, logical block 88180672
[66.169434] buffer  I/O  error on device sda4, logical block 88180673
[66.169515] buffer  I/O  error on device sda4, logical block 88180674
[66.169597] buffer  I/O  error on device sda4, logical block 88180675
[66.169679] buffer  I/O  error on device sda4, logical block 88180672

/dev/sda1: UUID="7be2862d-3274-4dde-8c8d-b5397f78b73d"  type= "ext3"

/dev/sda3: TYPE= "swap" UUID= "88b2fe5d-cfba-4628-8f7d-3fafb70ead2e

---

### Post by lrs52200 on 2008-10-25
Good morning all-

  I am on my machine right now.  I put in the Ubuntu Live CD and had to choose the last option (something like, start from 1st hard disk?).  Okay, so I'm here on my machine.......waiting for some kind, sweet soul to tell me if I can fix this error or not. 
  What does it mean:  "converted during upgrade to edgy?"  Was "edgy" part of the upgrade to Ubuntu 8.04 LTS? And for that matter, what ***is[I][B] edgy?***[/I][/B] I noticed that on startup, my computer now says:  Kubuntu instead of Ubuntu.

edit:  I've got to run out for a while, so if anyone responds, thank you in advance and I'll catch up with you when I get home.

---

### Post by lrs52200 on 2008-10-26
Can anyone tell me how to use UUIDgen and tune2fs?  I found the man pages, but I don't understand them.  I've never done this before.

---

### Post by lrs52200 on 2008-10-26
I just tried those commands (cat /etc/fstab  &
blkid) that you gave me yesterday.  The first one works, but blkid produces nothing.  I just get this again:  pamela@pamela-desktop:~$ 

Is that bad?

---

### Post by lrs52200 on 2008-10-26
I copied and pasted all of those numbers together so I could see if they were all alike, and they are.  So are you saying that the problem is that both hda4/sda4 and hda5/sda5 each say "ext 2?"
If so, how would I change that?


# /dev/hda	-  UUID=7be2862d-3274-4dde-8c8d-b5397f78b73d - ext3
/dev/sda1	-  UUID=7be2862d-3274-4dde-8c8d-b5397f78b73d - ext3

# /dev/hda4	-  UUID=0b529fb0-9ff4-4bf0-8c9c-424a17a06c33 - ext2
/dev/sda4 	-  UUID=0b529fb0-9ff4-4bf0-8c9c-424a17a06c33 - ext2

# /dev/hda5	-  UUID=c167d129-83d9-423a-8b89-fb099f0b8abf - ext2
/dev/sda5	-  UUID=c167d129-83d9-423a-8b89-fb099f0b8abf - ext2

# /dev/hda3	-  UUID=88b2fe5d-cfba-4628-8f7d-3fafb70ead2e - swap 
/dev/sda3	-  UUID=88b2fe5d-cfba-4628-8f7d-3fafb70ead2e - swap

What about gparted - can I use that to fix this?  Here's what gparted says:

Partition  Filesystem  mountpoint  size   used   unused   flags
/dev/sda1   ext3          /         27.69  2.55   25.14
/dev/sda3   linux/swap               5.56  ---      ---
/dev/sda4   ext2         home       84.10  1.45   82.65
/dev/sda2   extended               116.41  ---      ---
/dev/sda5   ext2         /usr      116.41  5.14  111.27

---

### Post by lrs52200 on 2008-10-27
Is there anyone who can help me with this?  Yesterday I re-installed version 8.04 LTS all over again.  Just as soon as I shut down I tried to reboot again - sure enough, the same error was there.  This time however, it wouldn't let me startup with the Live CD using 'boot from 1st hard disk.'  It doesn't appear that I'm able to start the OS at all since yesterday no other option on the Live CD would work (except install).  Control D didn't let me startup either, it just returned more errors

---

### Post by prshah on 2008-10-27
> **lrs52200 said:**
> 
 but blkid produces nothing.  

Did you do it from the maintenance prompt? (Recovery mode).

If not, you need to use "sudo" Eg;```
sudo blkid
```

Considering your other posts, maybe you should also post the output of ```
sudo fdisk -l
```

---

### Post by lrs52200 on 2008-10-27
Yes, the blkid thing worked......... I think the information changed after the reinstalled the operating system:

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=4eacb353-8e87-4b8e-a105-4aeb9480a82c / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1d424f71-e13f-48e3-a6da-0b264bae5ff9 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=237d8a01-f03f-40c4-8435-fd4417aa5bf2 /usr ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=f5276bc9-c039-42a4-b8ee-15b65ce9d1ab none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
pamela@pamela-desktop:~$ 

blkid:

pamela@pamela-desktop:~$ sudo blkid
[sudo] password for pamela: 
/dev/sda1: UUID="4eacb353-8e87-4b8e-a105-4aeb9480a82c" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="f5276bc9-c039-42a4-b8ee-15b65ce9d1ab" 
/dev/sdb1: UUID="237d8a01-f03f-40c4-8435-fd4417aa5bf2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1d424f71-e13f-48e3-a6da-0b264bae5ff9" SEC_TYPE="ext2" TYPE="ext3" 

I don't know what happened but I am right now on the computer that keeps tormenting me like this.  One moment it won't boot, giving me the finger of death, and the next minute I shut it down and it lets me on.  This happened yesterday too and I foolishly thought my problem was solved, but during the next shut down & restart, it gave the same error messages and wouldn't let me on and control-D didn't work either.  Go figure.  It seems though, that I still have the same problem because it still shows an error.  Can you tell me - in layman's terms - how to fix this?

pamela@pamela-desktop:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3a84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3442    27647833+  83  Linux
/dev/sda2            3443        4207     6144862+  82  Linux swap / Solaris
/dev/sda3            4208       30515   211319010    5  Extended
/dev/sda5            4208       30515   211318978+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
pamela@pamela-desktop:~$

---

### Post by lrs52200 on 2008-10-27
pamela@pamela-desktop:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3a84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3442    27647833+  83  Linux
/dev/sda2            3443        4207     6144862+  82  Linux swap / Solaris
/dev/sda3            4208       30515   211319010    5  Extended
/dev/sda5            4208       30515   211318978+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
pamela@pamela-desktop:~$

---

### Post by lrs52200 on 2008-10-27
pamela@pamela-desktop:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3a84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3442    27647833+  83  Linux
/dev/sda2            3443        4207     6144862+  82  Linux swap / Solaris
/dev/sda3            4208       30515   211319010    5  Extended
/dev/sda5            4208       30515   211318978+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00067445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
pamela@pamela-desktop:~$

Konsole:

pamela@pamela-desktop:~$ sudo /sbin/vol_id -u /dev/sda3
[sudo] password for pamela:
/dev/sda3: unknown volume type
pamela@pamela-desktop:~$ sudo /sbin/vol_id -u /dev/sda1
4eacb353-8e87-4b8e-a105-4aeb9480a82c
pamela@pamela-desktop:~$ sudo /sbin/vol_id -u /dev/sda2
f5276bc9-c039-42a4-b8ee-15b65ce9d1ab
pamela@pamela-desktop:~$ sudo /sbin/vol_id -u /dev/sda3
/dev/sda3: unknown volume type
pamela@pamela-desktop:~$ sudo /sbin/vol_id -u /dev/sda5
1d424f71-e13f-48e3-a6da-0b264bae5ff9
pamela@pamela-desktop:~$

---

### Post by lrs52200 on 2008-10-27
Just a quick update....  When I was trying to resolve my networking problems (configuring the printer through something in KDE?) my computer seemed to freeze up, I couldn't exit out of the application; when I tried to restart the computer, there was no longer an option to either "restart" or "shut down."  I was unable to do anything.  I got so frustrated that I did an illegal shut down.  Now I can't get back into my computer - same errors as before.  Again, Control-D does nothing but gives me a "login" and "password" prompt again.  I tried the Live CD.  It lets me use all of the prompts except "boot from first disk."  This may be a stupid question, in fact I'm sure it is, but I've got to ask it - how come when I select any of the options on the Live CD, it doesn't load my desktop?  I mean, I thought maybe I could go into the terminal and fix my UUID problem - but it comes back as:  ubuntu@ubuntu - instead of pamela@pamela - I told you I was new at this :( 

I found a page that said I should do the following and I want to know if you think I should try it. 

1)  navigate to a file called: /var/log/fsck
2)  open terminal and unmount the file system/partition and run a fsck on it (I don't know how to "unmount" the partition - or for that matter, run fsck on it)
3)  open /etc/fstab  (does he mean to open a file folder or to run this through the terminal?)
4)  open terminal & run blkid
5)  copy & paste the UUID alphanumerica value to the appropriate location for that partition in the fstab file, then save the file

I found this in one of the forums but I don't remember who wrote it.  I had bookmarked the page but since I'm not able to load my system, it isn't in my favorites.  I used Live CD and chose option 1.

I remember reading answers from you all that involve the "shell," and somehow using it to resolve this exact problem.  I don't know what the shell is.  Is it that black screen I default to when the OS doesn't load?  The black one that prompts me to "login?"

Also, if by your guidance I am able to resolve this problem, should I expect this to happen again when I upgrade to 8.10?  Is this going to happen every time?  

Lastly, if you think this is my best shot at resolving this problem AND if I'm able to accomplish this at that black screen of death that I enter when the error (fsck died with exit status 8) shows up, is my problem disk #3 or #1 or both?  (sda1 said there was an error-see fsck, and sda3 said it was an unknown volume-see Konsole)

---

### Post by lrs52200 on 2008-10-28
Let me ask this question from another angle.......

My problem stems from the upgrade to version 8.04, right?  I mean, that was what caused the change in the UUIDs (if I understand everyone correctly).  So if I just reinstall the operating system, it will go away, right?  I mean, I can use "killdisk" to erase everything, repartition the drives, and viola!  Bob's my uncle, right?

I have no information of any kind on this computer except the optional programs I've loaded since the upgrade.

But before I do this, can you at least tell me this - is there a Live CD out there with version 8.04 (so I can avoid the upgrade/UUID problem) or better yet, when version 8.10 comes out Thursday, will THAT be an ISO image that I can burn and use to install without any problems forever and ever amen?  

Further, the next time I upgrade, how can I avoid this UUID issue after an upgrade, but before a shutdown......(you see, I did learn something - don't shut down the computer until I've checked to see that the UUID numbers are the same in fsck, recovery, and fstab)..:)

---

### Post by lrs52200 on 2008-10-28
Maybe you can go one step further and tell me exactly how to divide my disks.  

My master drive is a 250GB, and my slave is a 300GB.  I use a lot of space for pics, documents, and games.  

What type of file system should I use, how big should I make the partitions, and where should I make the mount points?

BTW - thank you very much for being so patient with me.

---

### Post by hortstu on 2013-01-11
Where the solution?

---

### Post by overdrank on 2013-01-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

