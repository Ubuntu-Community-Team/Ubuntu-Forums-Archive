---
title: "Acer Aspire Windows Input/Output Error when try to copy"
date: 2015-12-02
forum: Hardware
---

### Post by Chris_Law on 2015-12-02
Hi, I have a near dead hard drive. I realised recently that I should try and access the disk with ubuntu live cd to recover many things including photos that, if i lost, would end me up in a lawsuit. So i ***_Need_*** to get these.

When I try and access the internal disk (/dev/sda), most of the files are there. Except for where the pictures are located. Some other files do some errors as well when I try to open them, but they arent as important.


I tried cloning the drive using this tutorial: [http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

I tried doing the command: sudo dd if=/dev/sda of=/dev/sdc, which [[/B]should][B] go from the internal drive to a 1tb external drive. But it gives me this error:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdc
dd: error reading &#8216;/dev/sda&#8217;: Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00159157 s, 0.0 kB/s
```


[U]PLEASE HELP!!!!

[/U]

Kind Regards,

Chris,



update:

Tried accessing the drive via terminal, brought up this:
```
ubuntu@ubuntu:/media/ubuntu/Acer$ ls
1.tms.dat                         FFOutput
2-click run                       hiberfil.sys
2faf696be5f612163bc9656a592bbdf2  log.txt
2.tms.dat                         msdia80.dll
3911dc178b7f05d36459              MSOCache
3.tms.dat                         OEM
5.tms.dat                         pagefile.sys
6.tms.dat                         PerfLogs
7.tms.dat                         ProgramData
aa.txt                            Program Files
AMD                               Program Files (x86)
Autodesk                          Recovery
$AVG                              $Recycle.Bin
book                              System Volume Information
BOOTSECT.BAK                      twonky-locations-70.db
Config.Msi                        user.js
db.info                           Users
Documents and Settings            Windows
Downloads                         ZEdit32
ebef6cb3514c491626cc514d
ubuntu@ubuntu:/media/ubuntu/Acer$ cd Users
ubuntu@ubuntu:/media/ubuntu/Acer/Users$ ls
Administrator  Andrew   Default User  Public
All Users      Default  desktop.ini   Therese
ubuntu@ubuntu:/media/ubuntu/Acer/Users$ cd Administrator
ubuntu@ubuntu:/media/ubuntu/Acer/Users/Administrator$ ls
ls: reading directory .: Input/output error
ubuntu@ubuntu:/media/ubuntu/Acer/Users/Administrator$ cd
ubuntu@ubuntu:~$ cd /media/ubuntu/Acer/Users/Therese
ubuntu@ubuntu:/media/ubuntu/Acer/Users/Therese$ ls
ls: reading directory .: Input/output error
ubuntu@ubuntu:/media/ubuntu/Acer/Users/Therese$ ^C -- Tried to ctrl+c
ubuntu@ubuntu:/media/ubuntu/Acer/Users/Therese$ 

```

---

### Post by Bucky Ball on 2015-12-02
Welcome. Why clone? The clone will be exactly the same as the source, which is corrupted by the sound of it. 

When you say a 'near dead drive', what do you mean? Please describe what symptoms it is showing of this. If it is a Windows NTFS drive, is it nearly full? Have you tried defragmenting it with Windows tools? 

Anyhow, sounds like you may need data recovery tools rather than a clone. Report back what the drive's doing and we'll keep digging. But again: if you clone a dodgy source partition/drive the target partition/drive will be an exact replica. Dodgy.

PS: Do you have a whole partition that is problematic? [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") should be able to recover the partition. If you are going for recovering just files, [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") it is (and sounds like it might be what you are looking for).

---

### Post by Chris_Law on 2015-12-02
It cannot boot into windows, there are signs of windows. But it doesn't boot into windows.

If left alone for a long period of time, it will come to one of the window 7 fancy artwork screens that are commonly seen when your on the login page. But I believe that is the Startup Repair. Nothing shows, though.

If I try and access the disk via Ubuntu, it will first show with an I/O error. But if I leave it for a while, it eventually loads**some **files in. But when I try to access the location of the photos, as stated above. Nothing is there. Or it gives me an I/O error.
If I try and attempt to enter a file in the drive without the use of Terminal, it flashes up with an I/O error.

I tried using HBCD, fired up Mini XP. I couldn't access the drive. It wouldn't show up.


I will give photorec a try. It looks promising. Does this only recover pictures?

Thanks.

---

### Post by Bucky Ball on 2015-12-02
> **Chris_Law said:**
> 
I will give photorec a try. It looks promising. Does this only recover pictures?

No.

---

### Post by Chris_Law on 2015-12-02
Aww, rats. I thought it was bootable.

Well that brings me to my next problem.

Ubuntu doesn't wanna boot anymore. It gets stuck on a grey whitish screen with a - flashing in the corner once I hit enter on the launch live cd ubuntu thing.

---

### Post by weatherman2 on 2015-12-02
Ubuntu might be stuck trying to examine your failing hard drive.  It sounds like it is nearly dead (failing hard drives routinely get worse the more you use them).  You can confirm this by powering off the computer, unplugging the hard drive inside, and trying to boot again.  If you are now able to boot Ubuntu immediately, it's probably the hard drive causing the boot freeze.  Or maybe you're not choosing the right boot device; I'm not quite clear what you mean about booting the Ubuntu CD.  Is CD/DVD drive set first in the boot order on your computer (so it tries to boot a CD before it tries to boot the hard drive?).  Or are you choosing CD/DVD from a boot menu on the computer to override trying to boot the hard drive?

You may have to pay $$$ to a data recovery service that can extract the data from the drive platters, if it is worth that much to you.

You could try ddrescue, but you'd of course need to get past booting Ubuntu.  ddrescue will copy only data that can be read and can re-try bad blocks again and again, sometimes taking days to try to copy something.  Even then, you may spend many hours trying to recover data and not even get that much of it back.

---

### Post by Bucky Ball on 2015-12-03
> **Chris_Law said:**
> Aww, rats. I thought it was bootable.

Well that brings me to my next problem.

Ubuntu doesn't wanna boot anymore. It gets stuck on a grey whitish screen with a - flashing in the corner once I hit enter on the launch live cd ubuntu thing.

You could try [SystemRescueCD]("http://www.sysresccd.org/System-tools") if you want a bootable version of Photorec. That may be able to retrieve the files if the disk is not too far gone. It includes Photorec, Testdisk and a bunch of other stuff. The live media boots to an xfce4 session (like Xubuntu). I am never without a bootable USB of SystemRescueCD in my kit-bag. 

As alluded to in the previous post: avoid using your hard disk unless it is to retrieve data. Sorry, should have said that earlier. :)

---

