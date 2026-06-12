---
title: "Rescue/Recover files from external hdd ?"
date: 2017-05-10
forum: Hardware
---

### Post by funked up on 2017-05-10
Hello everybody,

I have an external 3TB HDD drive which I used to back up all my big files like movies, videos, pictures, etc
One day I tried to back up all my files from my desktop to update to a newer ubuntu version. 

I copied and pasted many files at once and after a while there was nothing responding. After rebooting my system the HDD could no longer be mounted.
I've tried almost everything I could think of but with no luck yet. Even tried windows & mac (yep, so desperate!)

Disk utilities and gparted can "see" the drive but both programs say that it's an unknown format. I could just format it again but then I would loose all my data on that disk. I'm 99% sure it's not a hardware failure.

Last week I tried using the TestDisk utility from the software center. After a deep scan that lasted almost 24 hours it gave me these results (attached pics).
[ATTACH=CONFIG]275042[/ATTACH][ATTACH=CONFIG]275043[/ATTACH]
Problem is, I'm an average everyday user so I don't know what this means and how to proceed from here.

Can anybody tell me if I can recover my files? And if so, how exactly do I do that?
Remember I'm not a computer geek so a walk through would be very much appreciated.

Thank you in advance for your time!
George.

---

### Post by oldfred on 2017-05-10
Forcing shutdown almost always causes corruption if system is doing something.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key) 
    
What format was partition? If NTFS, often better to use Windows tools.

Did you really have one 3TB partition for all your data? 
Testdisk seems to be finding the possibility of a small partition near beginning of drive and at end.
It finds all or most all old partitions so if you resized something it finds before & after partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 
    
       An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by funked up on 2017-05-11
Thank you oldfred for your reply!

- Yes I know, you are right about forced shutdown.

- I'm afraid that the partition format is ext4.

- Yes, I really had one 3TB partition.

It's a glimpse of hope that Testdisk did find my partitions but as I mentioned before I do not know how to proceed. I've already gone several times through that link you've provided about data recovery but all the instructions about how to use testdisk are: "Run testdisk and it will scan your computer for media and offer you a menu-driven way to recover your partition."
The "menu-driven way" is in the screenshots I've attached in my initial post. I really don't know what to do!

---

### Post by oldfred on 2017-05-11
Sometimes Testdisk's deeper search will find files.

You may just need to run fsck if ext4 and partition is shown. If not then you have to use testdisk to make sure you have a partition. 
Sometimes parted rescue works, but best to know approx. start & end of partition.
       Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 
    

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by funked up on 2017-05-21
This is what I've got after running gpart
```
george@george-ThinkPad-R61e:~$ sudo gpart /dev/sdb
[sudo] password for george: 

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

---

### Post by oldfred on 2017-05-21
That did not show any partitions in partition table.

---

