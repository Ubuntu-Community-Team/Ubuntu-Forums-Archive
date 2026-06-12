---
title: "Installing Via Unichrome9 (P4M900) drivers"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by ikkefc3 on 2007-04-19
Hello,
I want to install the Via Unichrome9 (P4M900) drivers on Ubuntu 7.04.
The graphics card driver I can only download from source and not from e.g. OpenChrome or a .deb.
If I want to compile, I get this error:
```
root@LottiesPC:/home/ikkefc3/Desktop/CN_CX700-CN800XORG40071-kernel-src_20061107a/src# ./makedriver
Which version driver you want to release ? 
71
mkdir: cannot create directory `/CN_CX700-CN800XORG40071/': File exists
mkdir: cannot create directory `/CN_CX700-CN800XORG40071//': File exists
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P),C7/C7M, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
1
cp: target `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/' is not a directory: No such file or directory
./makedriver: line 359: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
chmod: cannot access `mpatch': No such file or directory
./makedriver: line 391: ./mpatch: No such file or directory
make: *** No rule to make target `clean'.  Stop.
cp: cannot stat `via_drv.o': No such file or directory
 -------- Complete to make & copy driver --------
root@LottiesPC:/home/ikkefc3/Desktop/CN_CX700-CN800XORG40071-kernel-src_20061107a/src# 

```
I have installed al the depencies exept there was a section in the manual:
```
                 Note: There is a convenient GUI package manager called "Synaptic
                 Package Manager" in Ubuntu 6.06.1/6.10. If the Internet connecting to
                 the updated URL has problem, update “/etc/apt/sources.list” file’s
                 URL address. Please click the "Reload Package Information" in the tool
                 then install and update any package needed.
b. Install & compile Xorg source 6.8.2/6.9 or install Xorg 7.0/7.1 DDK (Driver
   Development Kit) or SDK. Run the following commands for Xorg 6.8.2/6.9 in
   Fedora Linux Core 4.0, Mandriva Linux 2006.0, Red Flag Linux 5.0, and SuSE
   Linux 10.0/10.1. Take Fedora Linux Core 4.0 as an example
                 # rpm -ivh xorg-x11-6.8.2-31.src.rpm
                 # cd /usr/src/redhat/SPECS
                 # rpmbuild -bc xorg-x11.spec
                 # cd /usr/src/redhat/BUILD/xorg-x11-6.8.2/
                 # mv xc/ /usr/src/
   Note: Depending on user’s system, it may take 1 or 2 hours to finish.
   Note: Users must install the “xorg-x11-server-sdk” package in Fedora Linux Core
          5/6 (Xorg 7.0/7.1).
   Note: Users must install the “libxorg-x11-devel-7.1.0” package in Mandriva
          Linux 2007.0 (Xorg 7.1).
   Note: Users must install the “xserver-xorg-dev” package in Ubuntu Linux
          6.06.1/6.10 (Xorg 7.0/7.1).

```
Is there any way to get 3D to work?

---

### Post by hakk3rnator on 2007-04-21
I have the same exact problem. ](*,)

---

### Post by nasos on 2007-04-22
I installed logged in as a super user. If you haven't setup the super user account look here:
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html]("http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html")

Also make sure your driver choice is correct, poenchrome are a bit tricky and some drivers work for other models while not quite explictely stated.

---

### Post by ikkefc3 on 2007-04-24
> **nasos said:**
> I installed logged in as a super user. If you haven't setup the super user account look here:
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html]("http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html")

Also make sure your driver choice is correct, poenchrome are a bit tricky and some drivers work for other models while not quite explictely stated.
It cannot find the xorg sourcers...

---

### Post by nasos on 2007-04-24
> **ikkefc3 said:**
> It cannot find the xorg sourcers...

Try this, before reconfgiuring the xserver:

```
sudo apt-get update
sudo apt-get -install --reinstall xserver-xorg
sudo apt-get install xserver-xorg-driver-via
```

Then reconfigure by:

```
sudo dpkg-reconfigure xserver-xorg
```

you may also want to take a look in here:

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

---

### Post by ikkefc3 on 2007-04-28
> **nasos said:**
> Try this, before reconfgiuring the xserver:

```
sudo apt-get update
sudo apt-get -install --reinstall xserver-xorg
sudo apt-get install xserver-xorg-driver-via
```

Then reconfigure by:

```
sudo dpkg-reconfigure xserver-xorg
```

you may also want to take a look in here:

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

That doesn't work (no devices found if i set the driver to VIA)

---

