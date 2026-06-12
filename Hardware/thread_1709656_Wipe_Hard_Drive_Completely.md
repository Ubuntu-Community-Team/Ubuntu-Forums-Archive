---
title: "Wipe Hard Drive Completely"
date: 2011-03-18
forum: Hardware
---

### Post by rbodnar on 2011-03-18
Hello,

My sisters computer has recently been experincing some technical problems (mainly hard disk failure).  She has a 320 GB ATA TOSHIBA MK3265GSX, firmare GJ003M.  Windows has recently stopped working, and will not even start up (shows some weird paragraph looking symbol in the boot, but that doesn't matter).  I've downloaded ubuntu and installed it to my flash drive so I can can whatever necesary.  When I start the computer I receive a warning message saying that the hard disk may be broken or may have failed.  If I try to format it in the Disk Utility program it says that it is either busy, or cannot be written to.  I've browsed around the forums and tried numerous answers people have given in the terminal, but nothing has occurred as it should.  Here are some terminal entries that I have:
```

ubuntu@ubuntu:~$ sudo shred -n2 -v /dev/sdb
shred: /dev/sdb: failed to open for writing: No medium found
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00108121 s, 0.0 kB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: opening `/dev/sdb': No medium found
ubuntu@ubuntu:~$ fsisk /dev/sdd
No command 'fsisk' found, did you mean:
 Command 'fdisk' from package 'gnu-fdisk' (universe)
 Command 'fdisk' from package 'util-linux' (main)
fsisk: command not found
ubuntu@ubuntu:~$ fdisk /dev/sdd

Unable to open /dev/sdd
ubuntu@ubuntu:~$ sudo dd if=/dev/random of=/dev/sda
dd: writing to `/dev/sda': Input/output error
0+16 records in
0+0 records out
0 bytes (0 B) copied, 25.7806 s, 0.0 kB/s
```I was just wondering if there was anything I could do to sort of refresh the hard drive, or completely sweep all data from it and format it somehow.  I don't want to buy a new one unless I absolutely have to.

---

### Post by grabbindrivers on 2011-03-18
> **rbodnar said:**
> Hello,

My sisters computer has recently been experincing some technical problems (mainly hard disk failure).  She has a 320 GB ATA TOSHIBA MK3265GSX, firmare GJ003M.  Windows has recently stopped working, and will not even start up (shows some weird paragraph looking symbol in the boot, but that doesn't matter).  I've downloaded ubuntu and installed it to my flash drive so I can can whatever necesary.  When I start the computer I receive a warning message saying that the hard disk may be broken or may have failed.  If I try to format it in the Disk Utility program it says that it is either busy, or cannot be written to.  I've browsed around the forums and tried numerous answers people have given in the terminal, but nothing has occurred as it should.  Here are some terminal entries that I have:
```

ubuntu@ubuntu:~$ sudo shred -n2 -v /dev/sdb
shred: /dev/sdb: failed to open for writing: No medium found
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00108121 s, 0.0 kB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: opening `/dev/sdb': No medium found
ubuntu@ubuntu:~$ fsisk /dev/sdd
No command 'fsisk' found, did you mean:
 Command 'fdisk' from package 'gnu-fdisk' (universe)
 Command 'fdisk' from package 'util-linux' (main)
fsisk: command not found
ubuntu@ubuntu:~$ fdisk /dev/sdd

Unable to open /dev/sdd
ubuntu@ubuntu:~$ sudo dd if=/dev/random of=/dev/sda
dd: writing to `/dev/sda': Input/output error
0+16 records in
0+0 records out
0 bytes (0 B) copied, 25.7806 s, 0.0 kB/s
```I was just wondering if there was anything I could do to sort of refresh the hard drive, or completely sweep all data from it and format it somehow.  I don't want to buy a new one unless I absolutely have to.

Pull the cable out as far as you can and listen to the drive when it boots. If it makes any sort of noise you've got a dead drive.

If that's the case, the only thing you can do is thermite/blow torch/degauss the drive and start again. If the sectors can't be read you can't expect them to be able to be wiped.

---

### Post by wormyblackburny on 2011-03-18
Toss it. Even if you could possibly get it wiped and an OS installed, it will inevitably cause problems. Lets say it takes you 3-4 hours of research on how to wipe it, then another x amount of hours to actually DO the wipe, plus an hour installing/configuring the OS (even more if you have to find drivers). How much is your time worth? A decent HD from Bestbuy, Frys, Newegg is ~$30-40. Just buy a new one...

---

