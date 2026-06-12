---
title: "How to write on NTFS from Live CD?"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by ineksuyu on 2007-04-30
Hi guys,


I need to be able to write on my NTFS hard drive from Live CD, is this at all possible?


I had first installed ubuntu Feisty under windows, using WUBI (windows ubuntu installer). Then somehow I deleted my hard drive; i.e. I put everything into the Trash of ubuntu. Since ubuntu itself was installed under windows, I could not boot. 

Now, using a Live CD, I can see my <.Trash-alf128> folder in /media/disk drive. All my folders and f&#305;les are &#305;n there, but I want to cut everything from the trash and paste into the drive, so that windows can boot.

How can I get to write into my NTFS drive using LiveCD?


Thanks,


alf

---

### Post by kelvin spratt on 2007-04-30
you can't

---

### Post by Wiebelhaus on 2007-04-30
[Here]("http://jclark.org/weblog/Miscellany/Tech/ubrescue.html")

---

### Post by tuxcantfly on 2007-05-01
that method mentioned above is a tad bit more complicated than it should be... ntfs-3g does the job fine... and a lot faster and easier...

boot using an ubuntu 7.04 live cd

make sure the disks are unmounted

then in a terminal:

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/ntfs
sudo fdisk -l | grep NTFS
```

then something like this will show up:

```
/dev/sda1   *           1       12158    97659103+   7  HPFS/NTFS
```

take that first bit (/dev/sda1 in my case) and substitute it in here:

```
sudo ntfs-3g /dev/sda1 /media/ntfs
```

then navigate to /media/ntfs and all your files will be accessible with read/write support

---

### Post by ineksuyu on 2007-05-01
Thank you very much for your reply, which gave me hope. However, I seems that I cannot install ntfs-3g for some reason. Here is what I got:

```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:2 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty Release   
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/restricted Sources
Fetched 2B in 0s (3B/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g
```

---

### Post by ineksuyu on 2007-05-01
Then I tried to install ntfs-3g manually, with no success. Might it be because I'm using an i386 live cd, whereas my system is 64 bit?

```
ubuntu@ubuntu:~$ cd ntfs-3g-1.417
ubuntu@ubuntu:~/ntfs-3g-1.417$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

---

### Post by Jazzbunny on 2007-05-01
You need to enable Universe repositories as ntfs-3g is located there. After that just follow tuxcantflys guide.__

---

### Post by ineksuyu on 2007-05-01
Thank you very much all, I managed to recover my system. thanks a lot

---

