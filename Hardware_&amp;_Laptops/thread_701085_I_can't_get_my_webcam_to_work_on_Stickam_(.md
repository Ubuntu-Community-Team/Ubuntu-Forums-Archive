---
title: "I can't get my webcam to work on Stickam :("
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by 449 on 2008-02-19
Is there anyway to get it to work?

And it's *not* located under /dev/vid0, but does work in cheese. 

:confused:

---

### Post by 449 on 2008-02-21
bump

---

### Post by 449 on 2008-02-21
](*,)

---

### Post by harold4 on 2008-02-22
What webcam are you using? 

What is the result of 
```
ls /dev/vi*
```

---

### Post by 449 on 2008-02-22
Creative Live! Cam Video IM Pro

/dev/video0

---

### Post by harold4 on 2008-02-22
Try [this]("http://ubuntuforums.org/showthread.php?t=607309")

---

### Post by 449 on 2008-02-27
My cam works (with cheese) it's doesn't work with stickam.

---

### Post by harold4 on 2008-02-27
So it works with a local app, but does not work with a flash app.

Have you tried using the link I gave to update your driver?

---

### Post by 449 on 2008-02-27
> **harold4 said:**
> So it works with a local app, but does not work with a flash app.

Have you tried using the link I gave to update your driver?

I'm not sure if I did the right thing, but here's what I did so far:

```
erik@erik-desktop:~$ sudo apt-get update
[sudo] password for erik:
E: Type 'svn' is not known on line 86 in source list /etc/apt/sources.list
erik@erik-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://download.tuxfamily.org gutsy Release.gpg                            
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US               
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US               
Ign http://blognux.free.fr unstable Release.gpg                                
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://download.tuxfamily.org gutsy/multiverse Translation-en_US           
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US               
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
Hit http://us.archive.ubuntu.com edgy Release                                  
Get:5 http://security.ubuntu.com gutsy-security Release [51.2kB]               
Get:6 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:7 http://wine.budgetdedicated.com edgy Release.gpg [191B]                  
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                
Get:8 http://download.tuxfamily.org gutsy Release [1040B]                      
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
Get:9 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
Hit http://us.archive.ubuntu.com edgy/universe Packages                        
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
Hit http://wine.budgetdedicated.com edgy Release                               
Ign http://download.tuxfamily.org gutsy/multiverse Packages                    
Hit http://archive.canonical.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US     
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
Hit http://archive.ubuntu.com gutsy Release                                    
Get:10 http://archive.ubuntu.com gutsy-updates Release [58.5kB]                
Get:11 http://download.tuxfamily.org gutsy/multiverse Packages [4052B]         
Ign http://wine.budgetdedicated.com edgy/main Packages                         
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://blognux.free.fr unstable/main Translation-en_US                     
Hit http://wine.budgetdedicated.com edgy/main Packages                         
Hit http://archive.canonical.com gutsy/partner Sources                         
Get:12 http://archive.ubuntu.com gutsy-backports Release [44.0kB]              
Ign http://blognux.free.fr unstable Release                                    
Get:13 http://security.ubuntu.com gutsy-security/universe Packages [45.1kB]
Hit http://archive.ubuntu.com gutsy/multiverse Packages       
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Get:14 http://archive.ubuntu.com gutsy-updates/universe Packages [68.2kB]     
Get:15 http://archive.ubuntu.com gutsy-updates/main Packages [242kB]
Get:16 http://security.ubuntu.com gutsy-security/main Packages [72.0kB]        
Ign http://blognux.free.fr unstable/main Packages                              
Get:17 http://archive.ubuntu.com gutsy-updates/multiverse Packages [9942B]     
Get:18 http://archive.ubuntu.com gutsy-updates/restricted Packages [4263B]     
Get:19 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]   
Get:20 http://archive.ubuntu.com gutsy-backports/universe Packages [85.9kB]    
Get:21 http://security.ubuntu.com gutsy-security/restricted Packages [14B]     
Get:22 http://archive.ubuntu.com gutsy-backports/main Packages [29.6kB]        
Get:23 http://archive.ubuntu.com gutsy-backports/multiverse Packages [6660B]   
Get:24 http://archive.ubuntu.com gutsy-backports/restricted Packages [14B]     
Hit http://blognux.free.fr unstable/main Packages                              
Fetched 652kB in 3s (176kB/s)                  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
erik@erik-desktop:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
erik@erik-desktop:~$ 
erik@erik-desktop:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libpq5 libsvn1
Suggested packages:
  subversion-tools db4.4-util
The following NEW packages will be installed:
  libapr1 libaprutil1 libpq5 libsvn1 subversion
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1349kB of archives.
After unpacking 6193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main libapr1 1.2.7-8.2ubuntu1 [112kB]
Get:2 http://archive.ubuntu.com gutsy-backports/main libpq5 8.3.0-1~gutsy1 [325kB]
Get:3 http://archive.ubuntu.com gutsy/main libaprutil1 1.2.7+dfsg-2build1 [70.2kB]
Get:4 http://archive.ubuntu.com gutsy/main libsvn1 1.4.4dfsg1-1ubuntu3 [602kB]
Get:5 http://archive.ubuntu.com gutsy/main subversion 1.4.4dfsg1-1ubuntu3 [241kB]
Fetched 1349kB in 2s (487kB/s)
Selecting previously deselected package libapr1.
(Reading database ... 99199 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.7-8.2ubuntu1_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.0-1~gutsy1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.7+dfsg-2build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.4.4dfsg1-1ubuntu3_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.4dfsg1-1ubuntu3_i386.deb) ...
Setting up libapr1 (1.2.7-8.2ubuntu1) ...

Setting up libpq5 (8.3.0-1~gutsy1) ...

Setting up libaprutil1 (1.2.7+dfsg-2build1) ...

Setting up libsvn1 (1.4.4dfsg1-1ubuntu3) ...

Setting up subversion (1.4.4dfsg1-1ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
erik@erik-desktop:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
A    trunk/uvc_status.c
A    trunk/svn-version.sh
A    trunk/uvc_ctrl.c
A    trunk/uvc_queue.c
A    trunk/uvc_video.c
A    trunk/uvc_isight.c
A    trunk/uvc_v4l2.c
A    trunk/uvc_compat.h
A    trunk/uvc_driver.c
A    trunk/uvcvideo.h
A    trunk/Makefile
A    trunk/dynctrl.txt
Checked out revision 189.
erik@erik-desktop:~$ 

```

---

### Post by harold4 on 2008-02-27
in the "trunk" directory

```

make

sudo install -v -m644 uvcvideo.ko /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo/uvcvideo.ko\

sudo depmod -ae


```

EDIT: Assuming your the output of "uname -r" is 2.6.22-14-generic

---

### Post by 449 on 2008-02-27
I was fine until the last command...

```
erik@erik-desktop:~/trunk$ make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/erik/trunk/uvc_driver.o
  CC [M]  /home/erik/trunk/uvc_queue.o
  CC [M]  /home/erik/trunk/uvc_v4l2.o
  CC [M]  /home/erik/trunk/uvc_video.o
  CC [M]  /home/erik/trunk/uvc_ctrl.o
  CC [M]  /home/erik/trunk/uvc_status.o
  CC [M]  /home/erik/trunk/uvc_isight.o
  LD [M]  /home/erik/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/erik/trunk/uvcvideo.mod.o
  LD [M]  /home/erik/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
erik@erik-desktop:~/trunk$ sudo install -v -m644 uvcvideo.ko /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo/uvcvideo.ko\
> sudo depmod -ae
[sudo] password for erik:
install: invalid option -- a
Try `install --help' for more information.

```

---

### Post by harold4 on 2008-02-28
```

sudo install -v -m644 uvcvideo.ko /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo/uvcvideo.ko && sudo depmod -ae
sudo modprobe uvcvideo

```

---

### Post by 449 on 2008-02-29
I did that, restarted, and it's still not working.

---

### Post by harold4 on 2008-02-29
Is there any useful info in dmesg or /var/log/syslog?

---

