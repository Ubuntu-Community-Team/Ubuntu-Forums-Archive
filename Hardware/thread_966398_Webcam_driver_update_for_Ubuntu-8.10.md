---
title: "Webcam driver update for Ubuntu-8.10"
date: 2008-11-01
forum: Hardware
---

### Post by linux23dragon on 2008-11-01
[SIZE=6]Webcam driver update for Ubuntu-8.10[/SIZE]


***[I]UPDATE 25-02-09*** :- Sorry, I have been busy making money for free.  Well actually, without having to work for money.  Please see my [[COLOR="Blue"]web page[/COLOR]]("http://adam.com.au/linux23d") for more info.

In regards to known working web cams?  please see this link.
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)[/I]


***[I]UPDATE 10-12-08*** :- Removed out of date code.  Thread should be clossed.[/I]

***[I]UPDATE 29-11-08*** :- The kernel today (29-11-08 ) has been updated to 2.6.27-9.  These installation instructions have not been tested with this new Ubuntu kernel.[/I]
                   Please post a bug at [***_[COLOR="Blue"]Luanchpad[/COLOR]_***]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506") if you come across any webcam issues and help test the patch fixes that has been submitted.  The next kernel update may include the fixes.  Currently there is updates for libV4l and kernel fixes that has not yet been implemented.   

*Updated 26/11/08 :- Added the [I]**make clean*** command so the user can safely reuse the same installation code for updates[/I]
*Updated 16/11/08 :- Fixed the back port modules command.*
*Updated 13/11/08 :- The UVC only driver section is now deprecated, as the UVC driver is now officially merged into the GSPCA installation.*
*Updated 12/11/08 :- Added driver warning note*
*Updated 12/11/08 :- Clarified the and labeled GSPCA driver installation section.  UVC driver  also Clarified*
*Updated 10/11/08 :- Added a list of supported webcam and associated drivers.*
*Updated 06/11/08 :- Added more information about V4L/V4L2 driver conflicts between the two different drivers.*
*Updated 03/11/08 :- Added more webcam drivers*
*Updated 03/11/08 :- included the make install command.*

---

### Post by Yezinki on 2008-11-02
Hi there,

I hhave a integrated web cam on my Sony vaio VGC-LS1.

what driver should I use?


$ lsusb
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 054c:024b Sony Corp.
Bus 003 Device 001: ID 0000:0000

Hoping to hear,

Regards,

Yezinki.

---

### Post by caglar.dursun on 2008-11-02
Still something going wrong and I dont get it.

  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/caglar/trunk/trunk/uvcvideo.mod.o
  LD [M]  /home/caglar/trunk/trunk/uvcvideo.ko
make[1]: `/usr/src/linux-headers-2.6.24-16-generic' extract folder
cp: "/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/uvc/uvcvideo.ko" relocated: No such file or directory

Did i missed something ?

---

### Post by linux23dragon on 2008-11-02
> **Yezinki said:**
> Hi there,

I hhave a integrated web cam on my Sony vaio VGC-LS1.

what driver should I use?


$ lsusb
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 054c:024b Sony Corp.
Bus 003 Device 001: ID 0000:0000

Hoping to hear,

Regards,

Yezinki.


Hi Yezinki

According to this [***[COLOR="Blue"]descriptor[/COLOR]***]("http://www.qbik.ch/usb/devices/showdescr.php?id=3959") the [[COLOR="Blue"]***gspa***[/COLOR]]("http://mxhaard.free.fr/download.html") driver supports this webcam.

---

### Post by linux23dragon on 2008-11-02
> **caglar.dursun said:**
> Still something going wrong and I dont get it.

  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/caglar/trunk/trunk/uvcvideo.mod.o
  LD [M]  /home/caglar/trunk/trunk/uvcvideo.ko
make[1]: `/usr/src/linux-headers-2.6.24-16-generic' extract folder
cp: "/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/uvc/uvcvideo.ko" relocated: No such file or directory

Did i missed something ?

That was just the command to copy your old uvc driver to /lib/modules.

Can you please omit this cp command  :-

***sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&***

**Update**.  I have just added the *make install* command.  I did not include that command as it installs header files as well.

---

### Post by Sealbhach on 2008-11-02
I don't think my webcam is supported, I get this build error message:

```
Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/r5u870/0.11.1/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: error processing r5u870-dkms (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 r5u870-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by linux23dragon on 2008-11-02
> **Sealbhach said:**
> I don't think my webcam is supported, I get this build error message:

```
Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/r5u870/0.11.1/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: error processing r5u870-dkms (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 r5u870-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please have a look at your make.log.  It will let you know a bit more on whats happening.

Kernel device drivers will build and install on any PC, even if the actual device does not exist on that same PC.

---

### Post by linux23dragon on 2008-11-02
UPDATE:

I've corrected the installation commands. And made a note that the installation only installs the Linux UVC driver.


Please test.

---

### Post by Yezinki on 2008-11-02
You are a GENIUS linux23dragon!

What command should I use for my Sony Vaio VGC-LS1 machine's web cam.

[http://www.pcmag.com/article2/0,2817,2006322,00.asp](http://www.pcmag.com/article2/0,2817,2006322,00.asp)

Will the driver only work for 8.10 OR for all Linux distros?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-02
What command should I type to get the cam running??

Btw I am running Gutsy at the moment.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-02
> **Yezinki said:**
> 

Will the driver only work for 8.10 OR for all Linux distros?

Regards,

Yezinki.


It should work on a standard Linux kernel and it should be able to work on any Linux distribution.  But it depends on the distribution developers themselves if they keep the driver up to date or not.   

Some times its best to use the Package management tools of the distribution to install software, but it depends.

---

### Post by Yezinki on 2008-11-02
What do I type in the Terminal/Konsole?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-02
> **Yezinki said:**
> What command should I type to get the cam running??

Regards,

Yezinki.

You mean to run, or install the webcam?

Normally to install the driver, you only need to use the commands *make* and *make install*.  There is a Readme file on how to install the driver in the parent driver directory.

To use the webcam, you only need to run a webcam based application.

---

### Post by Yezinki on 2008-11-02
I have Kopete so in Yahoo messenger it does not run, displays plugin missing?

So Both Run & Install.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-02
> **linux23dragon said:**
> You mean to run, or install the webcam?

Normally to install the driver, you only need to use the commands *make* and *make install*.  There is a Readme file on how to install the driver in the parent driver directory.

To use the webcam, you only need to run a webcam based application.

**linux dragon am a newbie Kindly guide me how to install & run.**

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-02
> **Yezinki said:**
> **linux dragon am a newbie Kindly guide me how to install & run.**

Regards,

Yezinki.

OK later on today I'll look into it.  I'm currently at work and have no time to work on it.

I'll post later today (around 6 hours time)

---

### Post by Yezinki on 2008-11-02
Thanks a ton linuxdragon,

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-03
> **caglar.dursun said:**
> Still something going wrong and I dont get it.

  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/caglar/trunk/trunk/uvcvideo.mod.o
  LD [M]  /home/caglar/trunk/trunk/uvcvideo.ko
make[1]: `/usr/src/linux-headers-2.6.24-16-generic' extract folder
cp: "/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/uvc/uvcvideo.ko" relocated: No such file or directory

Did i missed something ?

Please remove the trunk directory if you are too repeat the installation please.

---

### Post by Yezinki on 2008-11-03
is this for me likuxdragon,

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-03
Running 3 distros Ubuntu gutsy , hardy & intrepid.

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Running 3 distros Ubuntu gutsy , hardy & intrepid.

Well it is time for some fun.

Your webcam is meant to be able to use the [[COLOR="Blue"]*_hvc032x_*[/COLOR]]("http://moinejf.free.fr/webcam.html") kernel module built from the gspca driver.

The driver is currently maintained at [[COLOR="Blue"]*_LinuxTV.org_*[/COLOR]]("http://linuxtv.org/hg/~jfrancois/gspca/"). 
 
Here is the build method.  But I have no idea if it will work as is.  You will need to test that for your self I'm afraid.  So don't blame me if it Borks up your system.

 

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
``` 

you might need to reboot the system to see the changes.

Hope this helps

---

### Post by Yezinki on 2008-11-03
Thanks lets have some fun.........I have installed Ubuntu 8.10.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-03
linuxdragon could you please till me step wise what to do?

Regards!

---

### Post by Yezinki on 2008-11-03
linux/drivers/media/video/v4l2-compat-ioctl32.c

1. how do I download install this?

2. [B]sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
weget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
make install &&
depmod -ae $(uname -r)[/B]

3. Whats uname.......what should I replace with?

---

### Post by Yezinki on 2008-11-03
ubuntu@ubuntu-laptop:~$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
> weget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
> tar xf tip.tar.bz2 &&
> cd gspca-* &&
> make &&
> make install &&
> depmod -ae $(uname -r)
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
linux-headers-2.6.27-7-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc subversion-tools db4.6-util
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
  subversion
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 9757kB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libstdc++6-4.3-dev 4.3.2-1ubuntu11 [1354kB]
Get:2 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main g++-4.3 4.3.2-1ubuntu11 [4128kB]
Get:3 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B]                                                                                                                                 
Get:4 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main patch 2.5.9-5 [100kB]                                                                                                                                        
Get:5 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main dpkg-dev 1.14.20ubuntu6 [612kB]                                                                                                                              
Get:6 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main build-essential 11.4 [7172B]                                                                                                                                 
Get:7 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libapr1 1.2.12-4 [109kB]                                                                                                                                     
Get:8 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main mysql-common 5.0.67-0ubuntu6 [60.7kB]                                                                                                                        
Get:9 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libmysqlclient15off 5.0.67-0ubuntu6 [1841kB]                                                                                                                 
Get:10 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libpq5 8.3.4-2.2 [281kB]                                                                                                                                    
Get:11 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libaprutil1 1.2.12+dfsg-7 [75.7kB]                                                                                                                          
Get:12 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libneon27-gnutls 0.28.2-2build1 [114kB]                                                                                                                     
Get:13 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libsvn1 1.5.1dfsg1-1ubuntu2 [734kB]                                                                                                                         
Get:14 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main subversion 1.5.1dfsg1-1ubuntu2 [340kB]                                                                                                                      
Fetched 9757kB in 2min53s (56.3kB/s)                                                                                                                                                                          
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 99828 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.2.12-4_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.4-2.2_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-7_i386.deb) ...
Selecting previously deselected package libneon27-gnutls.
Unpacking libneon27-gnutls (from .../libneon27-gnutls_0.28.2-2build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libapr1 (1.2.12-4) ...

Setting up mysql-common (5.0.67-0ubuntu6) ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libpq5 (8.3.4-2.2) ...

Setting up libaprutil1 (1.2.12+dfsg-7) ...

Setting up libneon27-gnutls (0.28.2-2build1) ...

Setting up libsvn1 (1.5.1dfsg1-1ubuntu2) ...

Setting up subversion (1.5.1dfsg1-1ubuntu2) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
bash: weget: command not found
ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> linux/drivers/media/video/v4l2-compat-ioctl32.c

1. how do I download install this?

2. [B]sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
weget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
make install &&
depmod -ae $(uname -r)[/B]

3. Whats uname.......what should I replace with?

Just copy the whole code section and then past it into the terminal.
You don't need to replace $(uname -r)

And I just edit the installation commands as I forgot to add the  *sudo* command.

---

### Post by Yezinki on 2008-11-03
[B]sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
weget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
make install &&
depmod -ae $(uname -r)[/B]

Output of this command.

---

### Post by Yezinki on 2008-11-03
What do I do now?

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> 
bash: weget: command not found
ubuntu@ubuntu-laptop:~$

Opps all fixed now. Please see the same post you copied the code from.  Thanks for the report

---

### Post by Yezinki on 2008-11-03
[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
> weget [http://linuxtv.org/hg/~jfrancois/gsp...ve/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gsp...ve/tip.tar.bz2) &&
> tar xf tip.tar.bz2 &&
> cd gspca-* &&
> make &&
> make install &&
> depmod -ae $(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bash: weget: command not found
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ [/B]


Same command in terminal but the out put is this now.

Regards!

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
> weget [http://linuxtv.org/hg/~jfrancois/gsp...ve/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gsp...ve/tip.tar.bz2) &&
> tar xf tip.tar.bz2 &&
> cd gspca-* &&
> make &&
> make install &&
> depmod -ae $(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bash: weget: command not found
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ [/B]


Same command in terminal but the out put is this now.

Regards!

Please refresh the page. Then copy the code.

---

### Post by linux23dragon on 2008-11-03
The code should look like this:-

```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

---

### Post by Yezinki on 2008-11-03
Output is this now:

[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
> wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
> tar xf tip.tar.bz2 &&
> cd gspca-* &&
> make &&
> sudo make install &&
> sudo depmod -ae $(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2008-11-03 14:13:27--  [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2)
Resolving linuxtv.org... 212.227.166.180
Connecting to linuxtv.org|212.227.166.180|:80... connected.
HTTP request sent, awaiting response... 200 Script output follows
Length: unspecified [application/x-tar]
Saving to: `tip.tar.bz2.1'

    [           <=>                         ] 2,953,370   83.9K/s   in 50s     

2008-11-03 14:14:17 (58.2 KB/s) - `tip.tar.bz2.1' saved [2953370]

make -C /home/ubuntu/gspca-e0b06b01146c/v4l 
make[1]: Entering directory `/home/ubuntu/gspca-e0b06b01146c/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.27-7-generic/build
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/ubuntu/gspca-e0b06b01146c/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  Building modules, stage 2.
  MODPOST 290 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
./scripts/rmmod.pl check
found 290 modules
make[1]: Leaving directory `/home/ubuntu/gspca-e0b06b01146c/v4l'
make -C /home/ubuntu/gspca-e0b06b01146c/v4l install
make[1]: Entering directory `/home/ubuntu/gspca-e0b06b01146c/v4l'
Stripping debug info from files
-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.27-7-generic/kernel/drivers/media/:
	video/gspca/m5602/: gspca_m5602.ko 
	dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko 
		dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko 
		dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-a800.ko 
		dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko dvb-usb-au6610.ko 
		dvb-usb-digitv.ko dvb-usb.ko dvb-usb-dibusb-mc.ko 
		dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-dtt200u.ko 
		dvb-usb-cinergyT2.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko 
		dvb-usb-anysee.ko dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko 
		dvb-usb-gl861.ko dvb-usb-m920x.ko 
	video/zoran/: videocodec.ko zr36050.ko zr36016.ko 
		zr36060.ko zr36067.ko 
	video/cx18/: cx18.ko 
	video/cpia2/: cpia2.ko 
	dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko 
	video/ivtv/: ivtvfb.ko ivtv.ko 
	common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko 
		mt2131.ko qt1010.ko mt20xx.ko 
		tda827x.ko tda18271.ko xc5000.ko 
		mxl5007t.ko tea5761.ko tuner-types.ko 
		tda8290.ko tuner-simple.ko mt2266.ko 
		tea5767.ko mxl5005s.ko 
	video/sn9c102/: sn9c102.ko 
	dvb/dvb-core/: dvb-core.ko 
	video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko 
		pms.ko bt856.ko upd64083.ko 
		v4l2-compat-ioctl32.ko stradis.ko videobuf-core.ko 
		tda9840.ko saa7191.ko cx2341x.ko 
		wm8775.ko meye.ko w9968cf.ko 
		saa7185.ko tuner.ko zr364xx.ko 
		ks0127.ko stv680.ko videobuf-dvb.ko 
		tvaudio.ko bt866.ko tea6420.ko 
		cafe_ccic.ko saa5246a.ko msp3400.ko 
		tcm825x.ko soc_camera.ko wm8739.ko 
		stkwebcam.ko saa5249.ko cpia_pp.ko 
		tda7432.ko w9966.ko mt9m001.ko 
		upd64031a.ko ir-kbd-i2c.ko ov511.ko 
		tea6415c.ko dabusb.ko bt819.ko 
		cpia_usb.ko videodev.ko tda9875.ko 
		adv7175.ko mxb.ko vivi.ko 
		soc_camera_platform.ko cs53l32a.ko s2255drv.ko 
		btcx-risc.ko se401.ko saa7110.ko 
		saa7115.ko saa6588.ko saa7111.ko 
		tvmixer.ko v4l2-common.ko saa7114.ko 
		hexium_orion.ko hexium_gemini.ko tvp5150.ko 
		mt9m111.ko vp27smpx.ko adv7170.ko 
		ov772x.ko ov7670.ko saa7127.ko 
		m52790.ko mt9v022.ko v4l1-compat.ko 
		videobuf-vmalloc.ko v4l2-int-device.ko sh_mobile_ceu_camera.ko 
		c-qcam.ko tveeprom.ko cs5345.ko 
		saa717x.ko cpia.ko tlv320aic23b.ko 
		bw-qcam.ko 
	video/cx23885/: cx23885.ko 
	dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko 
		dst.ko 
	dvb/siano/: sms1xxx.ko 
	video/cx25840/: cx25840.ko 
	dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko 
	dvb/dm1105/: dm1105.ko 
	video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko 
		saa7134-dvb.ko saa7134.ko 
	dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko 
		budget-av.ko budget.ko budget-core.ko 
		budget-ci.ko 
	video/et61x251/: et61x251.ko 
	dvb/frontends/: nxt6000.ko dib7000m.ko drx397xD.ko 
		s5h1411.ko si21xx.ko au8522.ko 
		s5h1420.ko stv0288.ko nxt200x.ko 
		mt352.ko s921.ko isl6405.ko 
		s5h1409.ko sp887x.ko dibx000_common.ko 
		isl6421.ko mt312.ko or51132.ko 
		tda1004x.ko dib3000mb.ko lgs8gl5.ko 
		dib3000mc.ko itd1000.ko sp8870.ko 
		l64781.ko dib7000p.ko ves1x93.ko 
		tda8083.ko stb6100.ko dib0070.ko 
		ves1820.ko stv0297.ko tda10086.ko 
		cx22700.ko zl10353.ko cx24110.ko 
		stv0299.ko dvb_dummy_fe.ko cx24123.ko 
		lgdt330x.ko dvb-pll.ko lnbp21.ko 
		cx22702.ko stb6000.ko lgdt3304.ko 
		cx24116.ko tda8261.ko tda10023.ko 
		tua6100.ko bcm3510.ko tda10021.ko 
		tda10048.ko stb0899.ko or51211.ko 
		tda826x.ko af9013.ko 
	video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
		cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
		cx88-dvb.ko 
	video/bt8xx/: bttv.ko 
	video/gspca/: gspca_pac207.ko gspca_stk014.ko gspca_spca501.ko 
		gspca_spca500.ko gspca_mars.ko gspca_spca508.ko 
		gspca_t613.ko gspca_sunplus.ko gspca_vc032x.ko 
		gspca_spca561.ko gspca_tv8532.ko gspca_spca505.ko 
		gspca_spca506.ko gspca_sonixj.ko gspca_zc3xx.ko 
		gspca_main.ko gspca_conex.ko gspca_pac7311.ko 
		gspca_sonixb.ko gspca_ov519.ko gspca_finepix.ko 
		gspca_etoms.ko 
	dvb/pluto2/: pluto2.ko 
	video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko 
		ultracam.ko konicawc.ko quickcam_messenger.ko 
	video/usbvision/: usbvision.ko 
	common/: saa7146_vv.ko ir-common.ko saa7146.ko 
	video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko 
	video/pvrusb2/: pvrusb2.ko 
	radio/: dsbr100.ko radio-maestro.ko radio-zoltrix.ko 
		radio-terratec.ko radio-aimslab.ko radio-maxiradio.ko 
		radio-gemtek.ko radio-trust.ko radio-sf16fmr2.ko 
		radio-typhoon.ko radio-cadet.ko radio-aztech.ko 
		radio-si470x.ko radio-sf16fmi.ko radio-rtrack2.ko 
		radio-gemtek-pci.ko radio-mr800.ko 
	video/uvc/: uvcvideo.ko 
	dvb/ttusb-budget/: dvb-ttusb-budget.ko 
	video/pwc/: pwc.ko 
	video/zc0301/: zc0301.ko 
	video/ovcamchip/: ovcamchip.ko 
	video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.27-7-generic 
make[1]: Leaving directory `/home/ubuntu/gspca-e0b06b01146c/v4l'
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
[/B]

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> 
make[1]: Leaving directory `/home/ubuntu/gspca-e0b06b01146c/v4l'
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
ubuntu@ubuntu-laptop:~/gspca-e0b06b01146c$ 
[/B]

nice.  looks good.  now reboot and try out your new webcam driver.

**EDIT.**  looks like it installs the linux uvc drivers as well.   nice.

---

### Post by Yezinki on 2008-11-03
> **linux23dragon said:**
> nice.  looks good.  now reboot and try out your new webcam driver.

Ok what application should I use for the cam??

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Ok what application should I use for the cam??

Ekiga, cheese, motion, amsn and camE

---

### Post by Yezinki on 2008-11-03
Rebooted..........just installed Ubuntu 8.10.........I only have Ekiga?

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Rebooted..........just installed Ubuntu 8.10.........I only have Ekiga?

Ekiga will do fine

---

### Post by Yezinki on 2008-11-03
Error internet NAT.........

---

### Post by Yezinki on 2008-11-03
For your view.......should I install Kopete?

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> For your view.......should I install Kopete?

No that is not an error, just the standard set up procedures.  Ekiga should do fine.

You can bypass the setup by clicking the cancel button.  The web cam will still operate (if the driver works ok)

---

### Post by Yezinki on 2008-11-03
Hey GENIUS it works on Ekiga........

**linuxdragon you are the best...........No: 1**

Thanks a ton,

Regards,

Yezinki.

What other soft wares can I use it in......yahoo, msn , koepte??

---

### Post by Yezinki on 2008-11-03
For your comments GENIUS!!

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Hey GENIUS it works on Ekiga........

**linuxdragon you are the best...........No: 1**

Thanks a ton,

Regards,

Yezinki.

What other soft wares can I use it in......yahoo, msn , koepte??

lol,  your funny.

Try them all out and have fun.  Also remember that you will need to repeat this webcam installation process every time the kernel gets updated, or if you happen to change the system kernel.

If the webcam just works with a new or updated kernel.  Then you won't need to worry about it again. 

Are you from china?

---

### Post by Yezinki on 2008-11-03
> **linux23dragon said:**
> lol,  your funny.

Try them all out and have fun.  Also remember that you will need to repeat this webcam installation process every time the kernel gets updated, or if you happen to change the system kernel.

If the webcam just works with a new or updated kernel.  Then you won't need to worry about it again. 

Are you from china?


No I aint from China though I was born there.

I'm a med doc MD in the US.

You are a** GENIUS LINUX KING**.......I hope that you wont mind my bugging you later since I am new to linux.....Can I add you as a friend??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-03
one last question KING!

How would I know that the kernel is changed or updated?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> No I aint from China though I was born there.

I'm a med doc MD in the US.

You are a** GENIUS LINUX KING**.......I hope that you wont mind my bugging you later since I am new to linux.....Can I add you as a friend??

Regards,

Yezinki.

lol, Yea that's cool.  Welcome to fun computing :)

---

### Post by Yezinki on 2008-11-03
Thanks KING.

For the welcome.

Ubuntu 8.10 is great but a little bloated vs Hardy.

Can I use it in Kopete, Messengers??

Take care,

Yezinki.

PS: I am adding ya OK.

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Thanks KING.

For the welcome.

Ubuntu 8.10 is great but a little bloated vs Hardy.

Can I use it in Kopete, Messengers??

Take care,

Yezinki.

PS: I am adding ya OK.

That's cool.
The webcam should be ok.  You might need to give it a go and see.

---

### Post by Yezinki on 2008-11-03
**Thanks GENIUS KING OF LINUX!!!**

Take good care of yourself!

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> one last question KING!

How would I know that the kernel is changed or updated?

Regards,

Yezinki.

Sorry I missed this one.

The update manger will show you a list of packages before you install them.  You only need to look out for the Linux kernel names (kernel modules and/or image) , and then you will know.

---

### Post by Yezinki on 2008-11-03
Which is the present kernel KING?

---

### Post by linux23dragon on 2008-11-03
> **Yezinki said:**
> Which is the present kernel KING?

linux23dragon@linux23dragon-desktop:~$ uname -r
2.6.27-7-generic
linux23dragon@linux23dragon-desktop:~$

---

### Post by Yezinki on 2008-11-03
Thanks KING!

Have a great day!

Cya later!

Regards,

Yezinki.

---

### Post by sidslasttheorem on 2008-11-03
hey, 

 I installed the uvc drivers, but it seems to have thrown something in visual effects.. the option has reverted to none, and i cant make a selection or either none, normal or extra
- i was working on extra to begin with
- im on the 8.10 ubuntu with a HP Pavilion dv5

is there something i can do to rectify?

---

### Post by linux23dragon on 2008-11-03
> **sidslasttheorem said:**
> hey, 

 I installed the uvc drivers, but it seems to have thrown something in visual effects.. the option has reverted to none, and i cant make a selection or either none, normal or extra
- i was working on extra to begin with
- im on the 8.10 ubuntu with a HP Pavilion dv5

is there something i can do to rectify?

Which application are you refering too?

---

### Post by sidslasttheorem on 2008-11-03
the visual effects tab under 
system->preferences->appearance

- i was working under 'extra' (with the squiggly windows, etc..)
  but it has now reverted back to 'none' and is not allowing me to select
  any option from the 3 specified ('none', 'normal' and 'extra')
   - but not allowing, i mean that the entire tab is greyed out so that I
     cant make a selection.
   - i tried reinstalling the video drivers (nVidia 177 - from system->administration->hardware drivers) but to no avail

---

### Post by linux23dragon on 2008-11-03
> **sidslasttheorem said:**
> the visual effects tab under 
system->preferences->appearance

- i was working under 'extra' (with the squiggly windows, etc..)
  but it has now reverted back to 'none' and is not allowing me to select
  any option from the 3 specified ('none', 'normal' and 'extra')
   - but not allowing, i mean that the entire tab is greyed out so that I
     cant make a selection.
   - i tried reinstalling the video drivers (nVidia 177 - from system->administration->hardware drivers) but to no avail

I have installed both webcam drivers on my system.  Compiz works ok (using your method) for me. 

Can you post a kernel and or Xorg.0.log or System log when you try to activate Compiz please?


Can you try to reinstall the kernel modules?  You won't need to reinstall the webcam drivers.

Hope that helps.

---

### Post by sidslasttheorem on 2008-11-03
> **linux23dragon said:**
> I have installed both webcam drivers on my system.  Compiz works ok (using your method) for me. 

Can you post a kernel and or Xorg.0.log or System log when you try to activate Compiz please?
>>am a relative newbie to linux, so couatiold you tell be how to do this?
>>btw, isnt compiz supposed to be the thing that lets you roatate the cube thing? I dont have that set up (just in case you were referring to that)

Can you try to reinstall the kernel modules?  You won't need to reinstall the webcam drivers.

>> again, could you tell me how to go about doing this?
>> i wouldnt mind not having support for my webcam if necessary, so i dont mind uninstalling the webcam drivers either.

Hope that helps.

>> thanks a bunch :)

---

### Post by linux23dragon on 2008-11-03
> **sidslasttheorem said:**
> >> thanks a bunch :)

Use the Synaptic package Manager to serch for ***linux modules***, and *mark for re-installation*(right click with mouse to get a list of options) the following:-

linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-modules-2.6.27-generic and also search for linux-image-2.6.27-7-generic

Reboot once this is done.  And test.

You will still have the new webcam driver you just installed after you have done this

Compiz is part of the *extra effects* option and is in relation only to the X server, video drivers and window manager (that works behind the Gnome or KDE desktops).

You can install Compiz Config Settings Manager to set up the cube and other excellent effects using Synaptic Package Manager.  It is a Very nice tool to have.

---

### Post by sidslasttheorem on 2008-11-03
> **linux23dragon said:**
> Use the Synaptic package Manager to serch for ***linux modules***, and *mark for re-installation*(right click with mouse to get a list of options) the following:-

linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-modules-2.6.27-generic

Reboot once this is done.  And test.

>>> doesnt help :( 
>>> I still cannot specify an option in the visual effects tab

You will still have the new webcam driver you just installed after you have done this

Compiz is part of the *extra effects* option and is in relation only to the X server, video drivers and window manager (that works behind the Gnome or KDE desktops).

You can install Compiz Config Settings Manager to set up the cube and other excellent effects using Synaptic Package Manager.  It is a Very nice tool to have.

Am installing Compiz Config Settings Manager now.
Is this supposed to be a replacement of sorts for the inbuilt visual effects?

---

### Post by linux23dragon on 2008-11-03
> **sidslasttheorem said:**
> Am installing Compiz Config Settings Manager now.
Is this supposed to be a replacement of sorts for the inbuilt visual effects?

Yes, it will override the default set up, but it will reset to some of the defaults (no desktop cube) once you deactivate the visual effects.  But the Compiz Config Settings Manager won't enable or disable Compiz.

---

### Post by sidslasttheorem on 2008-11-03
> **linux23dragon said:**
> Yes, it will override the default set up, but it will reset to some of the defaults (no desktop cube) once you deactivate the visual effects.

yeah, it works now.. :)
Thanks a lot :)

---

### Post by Silverspell on 2008-11-06
Dear linuxdragon,

I used the codes you specified, but after running the second one (for the supported linux UVC drivers) and rebooting, my network connection now doesn't work. Any ideas why, or possible solutions?

---

### Post by Yezinki on 2008-11-06
Unplug your adsl modem all leads.....turn of power for 5 mins at least.....re plug all cables/wires & turn on power.

---

### Post by Silverspell on 2008-11-06
I am sorry but this is not the case. It has nothing to do with my internet connection. First, i am on a university network every other computer is working fine. Second, if i  boot with the old kernel (2.6.24-21) instead of the new one (2.6.27-7), my network connection works like a charm.

---

### Post by linux23dragon on 2008-11-06
> **Silverspell said:**
> Dear linuxdragon,

I used the codes you specified, but after running the second one (for the supported linux UVC drivers) and rebooting, my network connection now doesn't work. Any ideas why, or possible solutions?

Nope, The installation should only effect the webcam drivers only (V4L and/or V4L2 modlues).  You can confirm that from the installation output from the terminal.


I recommend looking at your system logs using System Log (System -> Administration -> System Log) and look for network related errors there.

Of course you can also use a nice tool called wireshark, that will also help debug networking issues.


Are you using a NIC or WiFi?
Did you need to blacklist any kernel drivers to get your networking running?

Hope that helps

PS:  You can reverse all of the steps to see what caused the issues in the first place as well.  I can help with that too, if needed.  Also, did you install the Linux back ports modules?

---

### Post by Silverspell on 2008-11-06
Hey,

Thanks for the reply. I was actually using WiFi to connect. I had installed the backport modules also, and i didn't need to black list any kernel drivers to have it working.

Thing is, in my attempt to fix this, i tried to reinstall the kernel, which eventually led to me messing the OS up more, so now i have formatted and reinstalled Ubuntu 8.10.

So now, i will attempt to do everything again.

For knowledge's sake though i would really like to know how i could have reversed all the steps, as you say in your PS (and consequently amybe avoid the reinstallation).. although reinstalling was probably a good idea since it was my first Linux installation ever, and probably i had already messed stuff up, while learning.

---

### Post by linux23dragon on 2008-11-06
> **Silverspell said:**
> Hey,

Thanks for the reply. I was actually using WiFi to connect. I had installed the backport modules also, and i didn't need to black list any kernel drivers to have it working.

Thing is, in my attempt to fix this, i tried to reinstall the kernel, which eventually led to me messing the OS up more, so now i have formatted and reinstalled Ubuntu 8.10.

So now, i will attempt to do everything again.

For knowledge's sake though i would really like to know how i could have reversed all the steps, as you say in your PS (and consequently amybe avoid the reinstallation).. although reinstalling was probably a good idea since it was my first Linux installation ever, and probably i had already messed stuff up, while learning.

It might of been as easy as removing the kernel back ports.  

Reinstalling the kernel won't mess up the installation.  But it is good practise for you to start over.  Installing Ubuntu (or any distribution) for the first time can be a trail and error for anyone.

---

### Post by linux949 on 2008-11-07
I have an old Intel Webcam SC330 model, should I be able to use the codes that were posted earlier to fix driver problem in Ubuntu 8.10? I know this model worked fine in Ubuntu 8.04 (at least in Camorama) but it does not work now after I upgrade to 8.10 version.  

I am new to Linux so I am very appreciated to any help.  Thanks.

---

### Post by linux23dragon on 2008-11-07
> **linux949 said:**
> I have an old Intel Webcam SC330 model, should I be able to use the codes that were posted earlier to fix driver problem in Ubuntu 8.10? I know this model worked fine in Ubuntu 8.04 (at least in Camorama) but it does not work now after I upgrade to 8.10 version.  

I am new to Linux so I am very appreciated to any help.  Thanks.

You can only know by trying it out.  I don't have any feedback otherwise about the SC330.  But start with the kernel backports first and perhaps keep an eye on the kernel log as well.

---

### Post by saladbar2000 on 2008-11-09
> **linux23dragon said:**
> [SIZE=6]Webcam driver update for Ubuntu-8.10[/SIZE]


***Note2:- If you already installed the gspca drivers (witch does have an older version of the UVC driver), then you need to reinstall the kernel modules using synaptic manager before continuing.***


I already installed the gspca drivers and my webcam is still not recognized or functioning.  I was wondering how I go about reinstalling the kernel like you described.

I have a logitech quickcam chat and it was working before the 8.1 upgrade but was way too dark but now it isn't recognized at all.  I am a total ubuntu linux newbie so please forgive my complete and total ignorance.  Any response will be greatly appreciated.

r/
Dan

---

### Post by linux23dragon on 2008-11-09
> **saladbar2000 said:**
> I already installed the gspca drivers and my webcam is still not recognized or functioning.  I was wondering how I go about reinstalling the kernel like you described.

I have a logitech quickcam chat and it was working before the 8.1 upgrade but was way too dark but now it isn't recognized at all.  I am a total ubuntu linux newbie so please forgive my complete and total ignorance.  Any response will be greatly appreciated.

r/
Dan

Hi Dan

Use the synaptic package manager to reinstall the following kernel modules :-

linux-image-2.6.27-7-generic
linux-generic
linux-restricted-modules-common
linux-restricted-modules-generic


Then reboot.

Regards
Dave

---

### Post by zoomy942 on 2008-11-09
so, im at ubuntu 8.10, and my cam isnt working the cheese application and i have a few questions.

first, there is a bug report i have been watching and they dont mention a driver update there...  so is this not related?

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506")

also, this will simply fix my issue with my cam?

Lastly, it mentions changing kernel and using backports.  does this mean i will be dropping to an older version of the kernel i have?  does this change anything else about my system?

---

### Post by linux23dragon on 2008-11-09
> **zoomy942 said:**
> so, im at ubuntu 8.10, and my cam isnt working the cheese application and i have a few questions.

first, there is a bug report i have been watching and they dont mention a driver update there...  so is this not related?


Yes it is possibly related to that bug, as my webcam would not work without updating the UVC driver.  I have a logitech QC fusion.

You also might like to test the webcam with Ekiga as well.  



[QUOTE=zoomy]
also, this will simply fix my issue with my cam?
[/quote]

Yes it possibly will.  You can only try and see. 

[QUOTE=zoomy]
Lastly, it mentions changing kernel and using backports.  does this mean i will be dropping to an older version of the kernel i have?  does this change anything else about my system?[/QUOTE]

No it is later (and bug fixed) drivers that are backported to work with the current kernel used.  So it is more of a system upgrade.

---

### Post by zoomy942 on 2008-11-09
So, in all honesty, it wont hurt a thing to do this?  (i ask because, in all honesty, i'm not even sure what kernel headers are for)

---

### Post by saladbar2000 on 2008-11-09
Thanks

I re-installed the kernal modules and than copied and pasted the lines for installed the uvc driver but had one more question.

what do you mean by removing the trunk directory?

---

### Post by linux23dragon on 2008-11-10
> **zoomy942 said:**
> So, in all honesty, it wont hurt a thing to do this?  (i ask because, in all honesty, i'm not even sure what kernel headers are for)

It is safe.  The Kernel headers are only used when you compile user space software or the kernel drivers and even the kernel itself.

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> Thanks

I re-installed the kernal modules and than copied and pasted the lines for installed the uvc driver but had one more question.

what do you mean by removing the trunk directory?

Trunk is the name of the directory that has been downloaded onto your system.

They use the trunk directory (in svn) to track changes in development software.

---

### Post by saladbar2000 on 2008-11-10
I checked it out in the file browser and saw lots of stuff in there.  Did you mean to delete the whole trunk file folder?  Is it pretty much just temporary files from the installation?

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> I checked it out in the file browser and saw lots of stuff in there.  Did you mean to delete the whole trunk file folder?  Is it pretty much just temporary files from the installation?

Correct.

---

### Post by zoomy942 on 2008-11-10
forgive me for asking easy questions...

i finally got my ubuntu how i like it, and this wont hurt anything?

and i run the first step hoping it will work, if now continute on right?

---

### Post by saladbar2000 on 2008-11-10
Thanks again.  So in linux or ubuntu, the trunk is pretty much like the temperary files folder, correct?

---

### Post by saladbar2000 on 2008-11-10
I installed the uvc files, deleted the trunk and restarted but nothing is seeing my camera.  I've tried ekiga, skype, cheese and camerama but none of them work.  Any suggestions?

---

### Post by linux23dragon on 2008-11-10
> **zoomy942 said:**
> forgive me for asking easy questions...

i finally got my ubuntu how i like it, and this wont hurt anything?

and i run the first step hoping it will work, if now continute on right?

It should be ok.   You can always un-install the backports module it if things don't work out.

The system won't behave like windows.

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> I installed the uvc files, deleted the trunk and restarted but nothing is seeing my camera.  I've tried ekiga, skype, cheese and camerama but none of them work.  Any suggestions?

I'll get you to check if the driver does support your webcam after I come home from work later on today.

---

### Post by saladbar2000 on 2008-11-10
sounds good.

I'll probably get some beauty sleep soon and check back on tomorrow sometime.  Thanks for all the help.

r/

Dan

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> Thanks again.  So in linux or ubuntu, the trunk is pretty much like the temperary files folder, correct?

Not quite.  The trunk directory can be updated (keept in sync) without having the need to download all files from the developers svn trunk.

So you can keep it around, if you plan on updating the files every day.

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> I installed the uvc files, deleted the trunk and restarted but nothing is seeing my camera.  I've tried ekiga, skype, cheese and camerama but none of them work.  Any suggestions?

Hi saladbar2000


I found out that your webcam (***logitech quickcam chat***) is not UVC compliant.

You need to use the gspca/spca5xx driver.

---

### Post by Die_Aap on 2008-11-10
i have a philips spc 1000 nc webcam, which is uvc complaint.
i did what you requested but i am having no luck.
the video works on skype and ekiga, but i am unable to get any audio, not even thru playback nor testing.

please help.

---

### Post by linux23dragon on 2008-11-10
> **Die_Aap said:**
> i have a philips spc 1000 nc webcam, which is uvc complaint.
i did what you requested but i am having no luck.
the video works on skype and ekiga, but i am unable to get any audio, not even thru playback nor testing.

please help.

Can you please attach a copy of your kernel log please?

EDIT: Actually, you need to make sure that the volume for the microphone is ok.

You need to open your volume control and select the USB device.

Please see attached file.

Are you using a 64bit or 32bit OS?

---

### Post by saladbar2000 on 2008-11-10
Should I re-install the same kernal files before installing the gspa driver?

---

### Post by zoomy942 on 2008-11-10
i read through the thread again, and you know what?  aMSN, kopete, and all those work fine with my cam.  only cheese is acting funny.

---

### Post by linux23dragon on 2008-11-10
> **saladbar2000 said:**
> Should I re-install the same kernal files before installing the gspa driver?

Yes, if you can please.

---

### Post by saladbar2000 on 2008-11-11
well, I reinstalled the kernal files you listed and entered the code for installing the non-uvc cameras.  I unplugged and replugged in the camera and it worked in cheese (it was almost too dark to see but it was working) but it didn't work in ekiga, skype, or camorama.  I restarted the computer and it didn't work in any of them including cheese but I unplugged and replugged the camera and it worked in cheese (really dark) but none of the others.  It isn't making any sense to me but I was hoping this would mean something to you.

---

### Post by linux23dragon on 2008-11-11
> **saladbar2000 said:**
> well, I reinstalled the kernal files you listed and entered the code for installing the non-uvc cameras.  I unplugged and replugged in the camera and it worked in cheese (it was almost too dark to see but it was working) but it didn't work in ekiga, skype, or camorama.  I restarted the computer and it didn't work in any of them including cheese but I unplugged and replugged the camera and it worked in cheese (really dark) but none of the others.  It isn't making any sense to me but I was hoping this would mean something to you.

The divers are direct from the developers and reading the mailing list it appears that some of the code has had a complete re-write.

It was something to do with driver duplication, but I'm not sure what drivers were duplicated. 

I'll read more into this later tonight.

---

### Post by saladbar2000 on 2008-11-11
thanks again for all the help.  As of now, all of this is greek to me but hopefully if I stick with it I can eventually learn the ways of the linux and ubuntu.

---

### Post by zoomy942 on 2008-11-11
> **saladbar2000 said:**
> thanks again for all the help.  As of now, all of this is greek to me but hopefully if I stick with it I can eventually learn the ways of the linux and ubuntu.


so i ran this

  sudo apt-get install linux-backports-modules-2.6.27-7-generic

     sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
     wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
     tar xf tip.tar.bz2 && cd gspca-* &&
     make &&
     sudo make install &&
     sudo depmod -ae $(uname -r)


and still not working.  

what do you think?

---

### Post by linux23dragon on 2008-11-11
> **zoomy942 said:**
> i read through the thread again, and you know what?  aMSN, kopete, and all those work fine with my cam.  only cheese is acting funny.

Well your web cam works fine.


This is what I have read in the cheese FAQ (Frequently Asked Questions) section 5.4:-

[I]5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in
      gstreamer-properties. If it works
      there, but not in Cheese, please file a bug report in our [**_[COLOR="Blue"]bug tracker[/COLOR]_**]("http://bugzilla.gnome.org/browse.cgi?product=cheese").[/I]

---

### Post by socngill on 2008-11-11
Hi.  I am also having problems with my webcam.  I had orignally followed the instructions on here to install a different webcam which I finally got working, but it was very basic and slow so decided to buy a new one.  To get the old one working I basically did everything mentioned in the first post.

sudo apt-get install linux-backports-modules-2.6.27-7-generic

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko &&
sudo make install &&
sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&
sudo depmod -ae $(uname -r)

I did all of these, but I got the thing working. However, plugged in my new Creative Live! Cam Video IM (VF0350) and nothing worked.  Nothing recognised it.  lsusb showed that it was connected, but cheesecam came up with no camera found as did Skype.  So i found this site [http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx) which said the webcam was supported, so I went to Adept and installed the ov51 drivers, but still nothing.  So I donwloaded the source code and installed it that way, still nothing so I found the .deb file for it, downloaded it and re-installed but still nothing.  Since then I have run:

apt-get remove linux-backports-modules-2.6.27-7-generic

to try and backtrack and remove some of what I have installed.  I also follwed a hint on here and reinstalled the followinf:

linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-modules-2.6.27-generic and also search for linux-image-2.6.27-7-generic

but again it has made no difference follwoing a re-boot.

I am at a loss as to what to try.  The cam is supposed to be supported, but I just can't get it to work.  Any help would be greatly appreciated.

PS>  I have started a seperate thread as this one says "solved" and wasn't sure if it was still being checked.  [http://ubuntuforums.org/showthread.php?p=6152930#post6152930](http://ubuntuforums.org/showthread.php?p=6152930#post6152930)

---

### Post by linux23dragon on 2008-11-11
> **socngill said:**
> 

However, plugged in my new Creative Live! Cam Video IM (VF0350) and nothing worked.  Nothing recognised it.  lsusb showed that it was connected, but cheesecam came up with no camera found as did Skype.  So i found this site [http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx) which said the webcam was supported, so I went to Adept and installed the ov51 drivers, but still nothing.  So I donwloaded the source code and installed it that way, still nothing so I found the .deb file for it, downloaded it and re-installed but still nothing.  


Thanks for the report socngill.  

Is your webcam device reporting to be 041e:4060 ?.

I have had a look at the [[COLOR="Blue"]***_GSPA ov519 sub driver support list_***[/COLOR]]("http://moinejf.free.fr/webcam.html"), and found that the driver is not tested.  And Its not clear on what sensor is been used.  So I suspect that its possible that the driver is not production ready for that device.


You might be better off looking to get another webcam if you need one to work right now (since you can return the new cam).   

Have a look at the [[COLOR="Blue"]_***UVC based***_[/COLOR]]("http://linux-uvc.berlios.de/#devices") web cams as well.


EDIT:  I take it that you did read the [[COLOR="Blue"]***_FAQ_***[/COLOR]]("http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ") in regards to the ov51x-jpeg driver?

---

### Post by saladbar2000 on 2008-11-11
> **linux23dragon said:**
> Well your web cam works fine.


This is what I have read in the cheese FAQ (Frequently Asked Questions) section 5.4:-

[I]5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in
      gstreamer-properties. If it works
      there, but not in Cheese, please file a bug report in our [**_[COLOR="Blue"]bug tracker[/COLOR]_**]("http://bugzilla.gnome.org/browse.cgi?product=cheese").[/I]

My problem was actually the opposite.  It worked in cheese (only if I disconnect and reconnect the camera and even then it is super dark) but it doesn't work in the other programs.  what is gstreamer and how do I test my camera with it.  

Thanks

Dan

---

### Post by linux23dragon on 2008-11-11
> **saladbar2000 said:**
> My problem was actually the opposite.  It worked in cheese (only if I disconnect and reconnect the camera and even then it is super dark) but it doesn't work in the other programs.  what is gstreamer and how do I test my camera with it.  

Thanks

Dan

gstreamer is a streaming media framework.  Most of the gnome media applications use gstreamer for encoding/decoding video and audio using the gstreamer plug ins available. 


Enter this command in the terminal to test your webcam with gstreamer.
```
gstreamer-properties
```

---

### Post by saladbar2000 on 2008-11-12
It works when I select v4l2 under "plugin" on video input settings but it is very dark.  I was able to change the settings in ekiga and get it to work (very dark) but I'm not seeing settings in skype.  Is there any way to save this as the default for all the other applications?  And how do I adjust the brightness?

Thanks 

Dan

---

### Post by linux23dragon on 2008-11-13
The UVC only driver section is now deprecated, as the UVC driver is now officially merged into GSPCA

---

### Post by saladbar2000 on 2008-11-14
So does that mean that the other programs are trying to use UVC while cheese is the only program that is using the correct driver?

---

### Post by linux23dragon on 2008-11-14
> **saladbar2000 said:**
> So does that mean that the other programs are trying to use UVC while cheese is the only program that is using the correct driver?

Are you talking about the effect of the driver?

UVC is just a driver that will only run with UVC compliant webcams. It should not effect any programs directly.  You also have V4L2 and gstreamer to look at as well.  And the driver can effect only those (V4L2 and gstreamer) areas (or vis-versa), in regards to operation.  But the driver won't directly effect the front end

---

### Post by saladbar2000 on 2008-11-15
well, I guess the drivers are working because I am getting something when I test on the console, with cheese, and ekiga.  Would the darkness have to do with the drivers or would that be something else?  Ekiga won't let me control the lighting anymore and I'm not seeing how to control it in any other program.  Also, does anybody know how to make skype see the camera?  Skype video still isn't working.

---

### Post by wordmagic on 2008-11-15
This is what I got:
(Ubuntu 8.10)


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-2.6.27-7-generic-generic
spiros@spiros-desktop:~$

---

### Post by linux23dragon on 2008-11-15
> **wordmagic said:**
> This is what I got:
(Ubuntu 8.10)


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-2.6.27-7-generic-generic
spiros@spiros-desktop:~$

Fixed, thanks

---

### Post by 081105jk on 2008-11-16
[**BELIMO&#38400;&#38376;**](http://WWW.yhht-valve.com/belimofm.htm)  Belimo&#26159;&#20840;&#29699;&#26368;&#22823;[**BELIMO&#38400;&#38376;**](http://WWW.yhht-valve.com/belimofm.htm)&#21644;&#25216;&#26415;&#20379;&#26262;&#12289;&#36890;&#39118;&#12289;&#31354;&#35843;(&#26262;&#27668;&#36890;&#39118;&#31354;&#35843;):&#40784;&#20840;&#21333;&#19968;&#26469;&#28304;. &#19981;&#35770;&#26159;&#31354;&#27668;&#25110;&#27700;&#30005;&#36335;&#12289;&#26356;&#23433;&#20840;&#30340;&#38450;&#28779;&#21450;&#25490;&#28895;&#12289;&#31354;&#20013;&#31649;&#21046;&#23460;&#25110;&#20010;&#20154;:&#25552;&#20379;&#26368;&#20339;&#30340;&#35299;&#20915;&#26041;&#26696; [**BELIMO&#38400;&#38376;**](http://WWW.yhht-valve.com/belimofm.htm)R2&#20108;&#36890;&#25511;&#21046;&#29699;&#38400;[**BELIMO&#38400;&#38376;**](http://WWW.yhht-valve.com/belimofm.htm)&#12289;[**BELIMO&#38400;&#38376;**](http://WWW.yhht-valve.com/belimofm.htm)R3&#19977;&#36890;&#25511;&#21046;&#29699;&#38400;&#25511;&#21046;&#29305;&#24615; &#20026;&#20102;&#25511;&#21046;&#30340;&#31283;&#23450;&#24615;&#65292;&#38400;&#38376;&#38656;&#35201;&#26377;&#22312;&#30424;&#31649;&#21644;&#20854;&#20182;&#20256;&#28909;&#35013;&#32622;&#38750;&#32447;&#24418;&#29305;&#24449;&#30456;&#21453;&#30340;&#27969;&#37327;&#29305;&#24449;&#12290;&#31561;&#30334;&#20998;&#27604;&#29305;&#24615;&#21487;&#20197;&#20351;&#28909;&#36755;&#20986;&#21644;&#38400;&#38376;&#24320;&#24230;&#30456;&#27604;&#21576;&#32447;&#24615;.&#24403;&#38400;&#38376;&#24320;&#22987;&#25171;&#24320;&#26102;,&#27969;&#37327;&#22686;&#21152;&#38750;&#24120;&#32531;&#24930; &#20856;&#22411;&#30340;&#29699;&#38400;&#23646;&#24615; &#22312;&#25511;&#21046;&#23454;&#39564;&#26465;&#20214;&#19979;&#65292;&#20840;&#36890;&#29699;&#38400;&#34920;&#29616;&#20026;&#31561;&#30334;&#20998;&#27604;&#29305;&#24449;&#12290;&#36951;&#25022;&#30340;&#26159;&#24403;&#20856;&#22411;&#30340;&#29699;&#38400;&#23433;&#35013;&#22312;&#29616;&#22330;&#26102;&#36215;&#29305;&#24615;&#20250;&#20135;&#29983;&#20005;&#37325;&#30072;&#21464;&#12290;&#21407;&#22240;&#26159;&#20840;&#36890;&#29699;&#38400;&#30456;&#23545;&#19982;&#23427;&#26412;&#36523;&#23610;&#23544;&#26377;&#26497;&#22823;&#30340;C&#20540;&#12290;&#22312;&#36825;&#31181;&#24212;&#29992;&#22330;&#21512;&#38400;&#38376;&#23610;&#23544;&#36807;&#22823;&#65292;&#32780;&#8220;&#38400;&#26435;&#8221;&#24456;&#24046;&#12290;&#32467;&#26524;&#26159;&#65292;&#24403;&#38400;&#38376;&#20840;&#24320;&#21551;&#26102;&#65292;&#38400;&#38376;&#20004;&#31471;&#30340;&#21387;&#21147;&#24046;&#38750;&#24120;&#23567;&#12290; &#38543;&#30528;&#38400;&#38376;&#20851;&#38381;&#65292;&#21387;&#24046;&#22686;&#21152;&#12290;&#21482;&#21040;&#38400;&#38376;&#23436;&#20840;&#20851;&#38381;&#65292;&#20840;&#31995;&#32479;&#21387;&#21147;&#20316;&#29992;&#20110;&#38400;&#38376; [IMG]http://www.yhht-valve.com/img/biao/2.jpg[/IMG]

---

### Post by wordmagic on 2008-11-16
I tried both commands:

```
sudo apt-get install linux-backports-modules-$(uname -r)
```

(Did not uninstall though, how do i do it?)

and

```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

(This produced very long output...)

But my cam still does not work. It is a Protax DC30C and I have a Windows driver for it (works fine in Windows).

---

### Post by saladbar2000 on 2008-11-16
I'm looking through old threads on adjusting brightness but it looks like everything is different now.  How do I adjust brightness for the gspa drivers?

Thanks

Dan

---

### Post by linux23dragon on 2008-11-17
> **wordmagic said:**
> I tried both commands:

```
sudo apt-get install linux-backports-modules-$(uname -r)
```

(Did not uninstall though, how do i do it?)


uninstal via Synaptic package manager or

```
sudo apt-get purge linux-backports-modules-$(uname -r)
```





> **wordmagic said:**
> 
and

```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

(This produced very long output...)

That's normal

The GSPCA has Webcam, V4L and TV tuner drivers in the same package.


> **wordmagic said:**
> 
But my cam still does not work. It is a Protax DC30C and I have a Windows driver for it (works fine in Windows).

Is that a digital camera?

---

### Post by linux23dragon on 2008-11-17
> **saladbar2000 said:**
> I'm looking through old threads on adjusting brightness but it looks like everything is different now.  How do I adjust brightness for the gspa drivers?

Thanks

Dan

You should be able to use the brightness and gamma controls from the application your using.

If you can't, then its possibly a V4L or gstreamer issue your having, but that needs to be researched via kernel and system logs..

---

### Post by wordmagic on 2008-11-17
> **linux23dragon said:**
> 
Is that a digital camera?

It is described as "Digital Compact camera"

[IMG]http://www.mymemory.co.uk/images/memory-selector/products/1179314320.jpg[/IMG]

---

### Post by campbuds on 2008-11-17
how about for my sony vaio... vgn-cr220e?

---

### Post by Yezinki on 2008-11-17
> **wordmagic said:**
> It is described as "Digital Compact camera"

[IMG]http://www.mymemory.co.uk/images/memory-selector/products/1179314320.jpg[/IMG]

Yes looks like a Digital Camera with dual function of webcam ....similar to Logitech's click smart 510.

Regards,

Yezinki.

---

### Post by saladbar2000 on 2008-11-17
it is too dark in every application that it works in and none of them are letting me change anything.  How would I go about researching the kernel and system logs?

---

### Post by em4g.3ht on 2008-11-18
Hi there linux23dragon I was referred to you by another forum

I have been trying for a while to get my webcam to work consistently.

I have tried both

```
sudo apt-get install linux-backports-modules-$(uname -r)
```

and

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

*I removed backports before trying the second

I am using a lenovo y510 laptop with ubuntu 8.10. 

When use lsusb, my webcam does not show up 

when I dmesg i get:

```
[   18.951959] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[   18.953875] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   18.955711] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input12
[   18.980237] usbcore: registered new interface driver uvcvideo
[   18.980241] USB Video Class driver (v0.1.0)
```

in most forums users say this camera works out of the box , but mine doesn't. Any Help would be much appreciated

also every once in a while the camera will work with cheese (and cheese only) but after quiting, or cheese freezing it wont display anything, or give me a TV screen test with static in the right bottom corner.

and if there is nothing to be done, how do I undo the linuxtv drivers?

---

### Post by Yezinki on 2008-11-18
em4g.3ht

You made a smart move at last!

Good luck e LINUX KING.......he's a busy guy so be patient.

---

### Post by em4g.3ht on 2008-11-18
oh, i just check through the the dmesg code again and found this

[  212.715732] usb 7-6: configuration #1 chosen from 1 choice
[  212.717388] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[  212.719356] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  212.722799] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input14
[  391.106025] usb 7-6: USB disconnect, address 5
[  402.608188] usb 7-6: new high speed USB device using ehci_hcd and address 6
[  402.780090] usb 7-6: configuration #1 chosen from 1 choice
[  402.780839] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[  402.782949] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  402.784918] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input15


I'm somewhat certain that wasn't there before so it may have been from gspca drivers

---

### Post by em4g.3ht on 2008-11-18
well, Yezinki, i guess next time my girl friend askes me if i ever do anything right I can say yes, at least one thing :lolflag:

---

### Post by linux23dragon on 2008-11-18
> **em4g.3ht said:**
> oh, i just check through the the dmesg code again and found this

[  212.715732] usb 7-6: configuration #1 chosen from 1 choice
[  212.717388] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[  212.719356] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  212.722799] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input14
[  391.106025] usb 7-6: USB disconnect, address 5
[  402.608188] usb 7-6: new high speed USB device using ehci_hcd and address 6
[  402.780090] usb 7-6: configuration #1 chosen from 1 choice
[  402.780839] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[  402.782949] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  402.784918] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input15


I'm somewhat certain that wasn't there before so it may have been from gspca drivers

The driver seems to be working ok.  In this kernel log the driver has been loaded twice becuse you connected the webcam twice into your PC.

Have you tried out Ekiga?

---

### Post by linux23dragon on 2008-11-18
> **campbuds said:**
> how about for my sony vaio... vgn-cr220e?

Have you tried it out yet?

I need to know the device ID number.  Please post the output from this command.  Using the terminal.

```
***lsusb***
```

---

### Post by linux23dragon on 2008-11-18
> **wordmagic said:**
> It is described as "Digital Compact camera"

[IMG]http://www.mymemory.co.uk/images/memory-selector/products/1179314320.jpg[/IMG]

Please post the output after entering this command in a terminal.
[B][I]```

lsusb
```[/I][/B]

---

### Post by em4g.3ht on 2008-11-18
ekiga worked great! :)

which is good news i suppose because that means the driver is working, and I suppose always was.

Man, i hate wasting so much time just to find out that it was the programs fault :mad:

cheese and camorama do not work, does anyone know of a good "photo booth" software i can use?

or should I try updating cheese manually, if not really sure of my next step.

and linux dragon is there a simple way to un-do the gspca drivers? or would it be better to leave them?

---

### Post by Yezinki on 2008-11-18
> **em4g.3ht said:**
> well, Yezinki, i guess next time my girl friend askes me if i ever do anything right I can say yes, at least one thing :lolflag:


So True........

---

### Post by Hyperion_1984 on 2008-11-18
Hello,

I have a Logitech Quickcam for notebooks 
```
$ lsusb
Bus 004 Device 005: ID 046d:08ae Logitech, Inc. Quickcam for Notebooks
```
 which used to work under Hardy with the GSPCA driver. I had to replace the ZC0301 module with the GSPCA one to have it running smoothly.

In Intrepid, it works in Cheese and in Ekiga wit the ZC0301 driver but wont show any picture in application such as skype or aMSN. I've tried to install the GSPCA, compilling it from the original package or using your technique, however everytime I try to load the GSPCA driver I get a message  : 

```
$ sudo modprobe gspca
FATAL: Module gspca not found
```

Any clues?

---

### Post by Yezinki on 2008-11-18
Logitech quick cam vision & quick cam pro 9000, shall function in 8.10 with out any issues.

---

### Post by Nevon on 2008-11-19
My intergrated webcam used to work perfectly in 8.04, now it doesn't work at all. Here's the output of lsusb:

```
nevon@loltop:~$ lsusb
Bus 008 Device 004: ID 5986:0200 Acer, Inc 
Bus 008 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 09da:000e A4 Tech Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Yezinki on 2008-11-19
Hi, linux23dragon will take care of it.....he's a genius but an extremely busy guy....so be patient!

Regards,

Yezinki.

---

### Post by Hyperion_1984 on 2008-11-19
> **Yezinki said:**
> Logitech quick cam vision & quick cam pro 9000, shall function in 8.10 with out any issues.

Well, it does work. Although I'm now limited to V4L2 application (e.g. cheese, Ekiga). I can't use my webcam with applications using V4L (e.g. skype, aMSN, etc).

I had a similar issue with Hardy which I solved by removing the ZC0301 driver and by replacing it with the gspca one (following this thread: [http://ubuntuforums.org/showthread.php?t=583132&page=2]("http://ubuntuforums.org/showthread.php?t=583132&page=2")). However, I'm not able to do so in Intrepid. After compiling the gspca module, I get the error:

```
$ sudo modprobe gspca
FATAL: Module gspca not found.
```

---

### Post by Yezinki on 2008-11-19
My Sony's machine's built in, Z star micro corp webcam, works with Ekiga but NOT with aMSN too....

---

### Post by saladbar2000 on 2008-11-20
I've pretty much given up on my quickcam chat and I'm considering getting another webcam.  It looks like almost everybody has had issues with theirs also so I was wondering what would I be able to plug in and have work the way it was intended on all the programs it was intended to.  I am open to suggestions.

---

### Post by Yezinki on 2008-11-20
Logitech quick cam Vision pro 9000.

---

### Post by Yezinki on 2008-11-20
Its worth the headache of posts & replies..........just plug in & enjoy!

---

### Post by saladbar2000 on 2008-11-20
It looks a little pricey but it seems to have good reviews.  I'm a little wary of the charts and lists of what is and isn't compatible since apparently my camera is compatible but doesn't work.  Are there any cheaper ones that haven't had any problems?

---

### Post by Yezinki on 2008-11-20
Quick cam pro 9000.........cheaper than vision works great too.......uses V4L.........works on all applications..........you can see my posted pics using that & Sony's built in Z star which wont work with aMSN........BOTH quick cams function flawlessly.

---

### Post by saladbar2000 on 2008-11-20
thanks.
I'm going to have to go out and check for those tomorrow.  I've followed every thread I could find on the quickcam chat and I think I've run into a deadend.  It would be nice to be able to just plug it in and use it.

---

### Post by Yezinki on 2008-11-20
let me plug in quick cam pro 9000 & post a pic for you.

---

### Post by Yezinki on 2008-11-20
Sorry I just installed Ubuntu haven't installed amsn yet.........but you can have a look .

---

### Post by saladbar2000 on 2008-11-20
No worries.  Does it work on skype?

---

### Post by Yezinki on 2008-11-20
**[http://ubuntuforums.org/showthread.php?t=965754&page=29](http://ubuntuforums.org/showthread.php?t=965754&page=29)**


View & see the difference for yourself.

Z star with Ekiga & quick cam pro 9000 with aMSN simultaneously.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-20
> **em4g.3ht said:**
> ekiga worked great! :)

should I try updating cheese manually, if not really sure of my next step.

Updating aMSN or Cheese will not fix this issue.  The drivers are now using V4L2 as the default standard.  And there may be issues with Gstreamer plug ins.  So hold of on manually updating aMSN and Cheese software for now.

> **em4g.3ht said:**
> 
and linux dragon is there a simple way to un-do the gspca drivers? or would it be better to leave them?

Its best to keep them for now.  There will be a new kernel later on that should have a fix.  I have no idea when that updated kernel will be available.

---

### Post by Yezinki on 2008-11-20
Yes does work with Skype too.

---

### Post by saladbar2000 on 2008-11-20
sounds great.  
I might have to do some shopping tomorrow then.  

Thanks for the help.  
I'll let you know how it goes

---

### Post by Yezinki on 2008-11-20
Hey KING where have you been..........hibernation  mode??

Missed your presence!

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-20
> **Hyperion_1984 said:**
> Hello,

I have a Logitech Quickcam for notebooks 
```
$ lsusb
Bus 004 Device 005: ID 046d:08ae Logitech, Inc. Quickcam for Notebooks
```
 which used to work under Hardy with the GSPCA driver. I had to replace the ZC0301 module with the GSPCA one to have it running smoothly.



In Intrepid, it works in Cheese and in Ekiga wit the ZC0301 driver but wont show any picture in application such as skype or aMSN. I've tried to install the GSPCA, compilling it from the original package or using your technique, however everytime I try to load the GSPCA driver I get a message  : 

```
$ sudo modprobe gspca
FATAL: Module gspca not found
```

Any clues?

The aMSN and maybe Skype might be in relation with V4L2  and the driver support for V4L and V4L2.

I'm not the developer so You might need to ask upstream about it or post a bug.

But the module your trying to load.  Are you sure ***gspca*** is the actual driver for you webcam?  Try to find the actual driver, because I think it is the UVC driver you need to load I think.

---

### Post by Yezinki on 2008-11-20
> **saladbar2000 said:**
> sounds great.  
I might have to do some shopping tomorrow then.  

Thanks for the help.  
I'll let you know how it goes

Not a problem.

Good luck!

Yezinki.

---

### Post by Yezinki on 2008-11-20
> **linux23dragon said:**
> The aMSN and maybe Skype might be in relation with V4L2  and the driver support for V4L and V4L2.

I'm not the developer so You might need to ask upstream about it or post a bug.


The driver he has is for V4L2 & he needs V4L to work in aMSN & Skype.......

My thoughts,

Yezinki.

---

### Post by Yezinki on 2008-11-20
KING after a fresh install while configuring Ekiga my Sony's cam works only with V4L2 & not V4L.

---

### Post by linux23dragon on 2008-11-20
> **Nevon said:**
> My intergrated webcam used to work perfectly in 8.04, now it doesn't work at all. Here's the output of lsusb:

```
nevon@loltop:~$ lsusb
Bus 008 Device 004: ID 5986:0200 Acer, Inc 
Bus 008 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 09da:000e A4 Tech Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

That cam seems to be connected and should work OK with the new uvc driver (provided with the gspca drivers).

Test it with Ekiga.

---

### Post by linux23dragon on 2008-11-20
> **Yezinki said:**
> My Sony's machine's built in, Z star micro corp webcam, works with Ekiga but NOT with aMSN too....

This is starting to look like V4L2 vs Driver vs application support with V4L.

---

### Post by linux23dragon on 2008-11-20
> **saladbar2000 said:**
> I've pretty much given up on my quickcam chat and I'm considering getting another webcam.  It looks like almost everybody has had issues with theirs also so I was wondering what would I be able to plug in and have work the way it was intended on all the programs it was intended to.  I am open to suggestions.


Don't upgrade.  Wait for the kernel update with the fix.  And find or report a bug about aMSN

---

### Post by linux23dragon on 2008-11-20
> **Yezinki said:**
> Hey KING where have you been..........hibernation  mode??

Missed your presence!

Regards,

Yezinki.

Working and investing at the same time.

---

### Post by em4g.3ht on 2008-11-20
thanks linuxdragon, I guess I will hold tight and wait for a kernel update :\

---

### Post by saladbar2000 on 2008-11-20
I don't use aMSN but I use skype.  Are you saying that either way, my camera won't work?  Is there anyway to go back to a previous ubuntu version or would it work on a previous version?

---

### Post by linux23dragon on 2008-11-20
> **saladbar2000 said:**
> I don't use aMSN but I use skype.  Are you saying that either way, my camera won't work?  Is there anyway to go back to a previous ubuntu version or would it work on a previous version?

I've corrected the post.  But if it had worked before with Ubuntu-8.04 then you should not need to upgrade.

Wait for a kernel update that will have a webcam fix.

I have no idea if the applications will be ok, but the webcam driver should be fixed.

---

### Post by saladbar2000 on 2008-11-20
how long does that usually take and how do I post an error report?

---

### Post by Yezinki on 2008-11-20
ubuntu@ubuntu-laptop:~$ lsusb
Bus 005 Device 010: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 005 Device 006: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 005 Device 003: ID 054c:031d Sony Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 054c:024b Sony Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-20
ubuntu@ubuntu-laptop:~$ lsusb
Bus 005 Device 010: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 005 Device 006: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 005 Device 003: ID 054c:031d Sony Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 054c:024b Sony Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu-laptop:~$

---

### Post by saladbar2000 on 2008-11-20
I'm kind of weighing my options here.  Would a new webcam not work correctly or are you just saying hold on to save my hard-earned duckets.  If that is the case, how long does a fix usually take after reports have been posted?

btw, it worked but was too dark in the previous version also.  I could adjust ekiga to get decent lighting but I couldn't adjust anything else.  Now ekiga won't let me adjust the brightness and neither will anything else.

---

### Post by Yezinki on 2008-11-20
saladbar2000 its worth a 90 bucks investment....... awesome piece of hard ware.......with its Carl Zeis lens & upto 8 mega pixel zoom.

Just my thoughts,

Regards,

Yezinki.

---

### Post by saladbar2000 on 2008-11-20
so the other camera will work with the current version of ubuntu and it will work with skype and other programs, correct?  I think I might go check it out tomorrow.

---

### Post by Yezinki on 2008-11-20
Let me install aMSN & show you .......hold on.

---

### Post by Yezinki on 2008-11-20
With default settings of Brightness, Hue, Saturation etc..........

Hope that helps,

Good Luck.

Yezinki.

---

### Post by Nevon on 2008-11-20
> **linux23dragon said:**
> That cam seems to be connected and should work OK with the new uvc driver (provided with the gspca drivers).

Test it with Ekiga.

Doesn't work. It just says it couldn't connect to the device. I can't get my built-in microphone to work either, but that's a subject for another thread.

How do I install the gspca drivers? (After 1½ years with Linux I still feel like a noob)

---

### Post by Yezinki on 2008-11-20
Join the party ...........Im a noob too.

---

### Post by saladbar2000 on 2008-11-20
that pic looks great.  Does the default picture look as good in all your other programs (including skype)?

---

### Post by Yezinki on 2008-11-20
Looks even better.........I hurriedly installed aMSN to show the results......didn't configure/cutomize the settings.

---

### Post by Yezinki on 2008-11-20
Plus no hassle of configuring drivers...........need a bottle of Tylenol to relieve the head aches I get lol..........

---

### Post by Yezinki on 2008-11-20
what do you do to install Skype in 8.10??

---

### Post by Yezinki on 2008-11-20
Skype cam for you saladbar.........

Regards,

Good Luck.

Yezinki.

---

### Post by Yezinki on 2008-11-20
> **saladbar2000 said:**
> that pic looks great.  Does the default picture look as good in all your other programs (including skype)?

Hope it helped........im hitting the bed have a busy day ahead.

Regards!

---

### Post by saladbar2000 on 2008-11-20
that looks fantastic!

That was with the quickcam pro 9000 right?  It looks like it got cnet editor's choice and it is running about $90.  I think I'll try to pick one up tomorrow.

---

### Post by Yezinki on 2008-11-20
Yes this was just a display of Quick cam pro 9000........not Vision 9000..........that's even better lol.

My personal recommendation would be to go for quick cam pro 9000........Vision one is too advanced.......this shall meet ALL your needs.

Good Nite!

---

### Post by saladbar2000 on 2008-11-20
thanks again

good night

---

### Post by Yezinki on 2008-11-20
Not a problem.......have fun.

Good luck & Good Nite!

---

### Post by Hyperion_1984 on 2008-11-20
> **linux23dragon said:**
> The aMSN and maybe Skype might be in relation with V4L2  and the driver support for V4L and V4L2.

I'm not the developer so You might need to ask upstream about it or post a bug.

But the module your trying to load.  Are you sure ***gspca*** is the actual driver for you webcam?  Try to find the actual driver, because I think it is the UVC driver you need to load I think.

I didn't try the UVC driver yet. I'll check and get back to you about it.

---

### Post by scottpayne on 2008-11-20
Thanks for the information. Installing gspca was the best solution for using my UVC webcam.

It appears to have resolved problems using the webcam in Cheese and Skype.

So, UVC webcams worked in the last Ubuntu release and there is a fix for this bug in the current release. How to get this into intrepid-updates or intrepid-proposed repositories?

Note, installing the suggested back ports didn't help. In fact, it broke the wireless connection.

---

### Post by saladbar2000 on 2008-11-21
I picked up the quickcam pro 9000 today and just plugged it in.  It actually worked just by plugging it in and the picture and sound are great.  I give this webcam three thumbs up!

---

### Post by Yezinki on 2008-11-21
I am so glad for you saladbar2000.........

What ever advice/ suggestions I usually give are TRIED & TESTED!!

Good Luck again & have fun with this great piece of hardware.

Regards,

Yezinki.

---

### Post by saladbar2000 on 2008-11-21
thanks again

the difference between the quickcam chat and the pro 9000 is night and day.  I also had to mess around with my headset for the mic on the quickcam chat.  Not quite sure what will become of the headset now.

---

### Post by Yezinki on 2008-11-21
The mic in quick cam pro 9000 is very sensitive with great quality audio, ideally made for video conferencing.

No hassles of making commands to detect video/audio drivers.......just simply plug & PLAY lol.

Enjoy the fun of real quality camming in Ubuntu.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
> **saladbar2000 said:**
> I picked up the quickcam pro 9000 today and just plugged it in.  It actually worked just by plugging it in and the picture and sound are great.  I give this webcam three thumbs up!

Smart, intelligent choice!

---

### Post by Yezinki on 2008-11-21
[IMG]http://i4.photobucket.com/albums/y129/eDOC/99-1.jpg[/IMG]

Quick cam Pro 9000 in windows using yahoo messanger!

Regards,

Yezinki.

---

### Post by saladbar2000 on 2008-11-21
yeah, I was surprised how bright and detailed the picture looked when I tested it out.  Also, like you said, your voice is very clear from anywhere in the room.  Great choice.

---

### Post by cyrulution on 2008-11-21
I got a Logitec webcam

> Bus 002 Device 007: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX

installed everything as proposed above. 
Most time I start the video test in Skype all Skype crashes away.
Help!

---

### Post by Yezinki on 2008-11-21
> **saladbar2000 said:**
> yeah, I was surprised how bright and detailed the picture looked when I tested it out.  Also, like you said, your voice is very clear from anywhere in the room.  Great choice.

Exactly saladbar2000 its FULL HD!

Have fun.

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
> **cyrulution said:**
> I got a Logitec webcam



installed everything as proposed above. 
Most time I start the video test in Skype all Skype crashes away.
Help!


Just like saladbar2000 get a 90 bucks Quick cam Pro 9000....it shall relieve you of all headaches/ hassles of compiling drivers etc....works great on Skype plus other messengers....Full HD....awesome audio & video....upto 8 megapixel.

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

---

### Post by cyrulution on 2008-11-22
> **Yezinki said:**
> I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....
Yezinki.

My deepest sympathies for moving to Windows. Rest well!:lolflag:

I don't have the money to waste for expensive nonsense.

My Logitec webcam used to work very well under Hardy. Now the built in Microphone is working excellently, but the video part of the camera just brings scrambled colors.

---

### Post by sondosia on 2008-11-22
HELP! I did this and now, first of all, my webcam still doesn't work, and second, I have NO WIRELESS. How do you reverse this process or fix that or anything? It took me months to get wireless working last time. I can't believe this. Please please help.

---

### Post by em4g.3ht on 2008-11-22
SOLVED!!! all I had to do was turn down the resolution in cheese and make sure to turn my webcam off before exiting.

I know it's still not 100% working, but hey I works about 80% which is more than 0%

---

### Post by linux23dragon on 2008-11-22
> **sondosia said:**
> HELP! I did this and now, first of all, my webcam still doesn't work, and second, I have NO WIRELESS. How do you reverse this process or fix that or anything? It took me months to get wireless working last time. I can't believe this. Please please help.

Did you install linux back port modules?

If you did uninstall linux back port modules.

```
apt-get remove linux-backports-modules-2.6.27-7-generic
```

Then use the Synapyic Pakage Manager to reinstall :-

[I][B]linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-modules-2.6.27-generic 
linux-image-2.6.27-7-generic[/B][/I]

Then reboot.

If you needed a to configure the wireless before, then you will need to reconfigure it using the same steps you had done before.

---

### Post by linux23dragon on 2008-11-22
> **Yezinki said:**
> Exactly saladbar2000 its FULL HD!

Have fun.

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

We will see you back soon.  Don't spend up on Microsoft and stay away from the so called *gold membership* as well.  It will cost you more than you really think.

---

### Post by Yezinki on 2008-11-23
> **cyrulution said:**
> My deepest sympathies for moving to Windows. Rest well!:lolflag:

I don't have the money to waste for expensive nonsense.

My Logitec webcam used to work very well under Hardy. Now the built in Microphone is working excellently, but the video part of the camera just brings scrambled colors.



This is how my Sony's cam worked in aMSN.....colors scrambled.

---

### Post by rhenium3 on 2008-11-23
I did the above but my webcam does not work with skype or Ekiga :(  Any ideas?  This is for my built in camera in my notebook --------


LMAO, nevermind, I didn't turn my camera on! P2, thank you, works now :D :D :D

---

### Post by Yezinki on 2008-11-23
> **linux23dragon said:**
> We will see you back soon.  Don't spend up on Microsoft and stay away from the so called *gold membership* as well.  It will cost you more than you really think.

Hi KING!

Hoping to be back one day?

What's *gold membership* lol?

Regards,

Yezinki.

---

### Post by sondosia on 2008-11-23
THANK YOU, linux23dragon! That did the trick.

Do you know if there's any chance I could still get the webcam working now, too? I'm almost scared to mess with it anymore...but all the steps I took seemed to have worked, and yet when I plug it in, still no video0 in /dev/. :confused:

---

### Post by Yezinki on 2008-11-23
> **Yezinki said:**
> Hi KING!

Hoping to be back one day?

What's *gold membership* lol?

Regards,

Yezinki.


No wonder I call you the **[FONT="Arial"][SIZE="5"][COLOR="Red"]KING of LINUX![/COLOR][/SIZE][/FONT]** ;)

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-24
> **Yezinki said:**
> No wonder I call you the **[FONT="Arial"][SIZE="5"][COLOR="Red"]KING of LINUX![/COLOR][/SIZE][/FONT]** ;)

Regards,

Yezinki.

It is to do with Microsoft support that costs a lot of money.  Microsoft thinks they can support you better if you are a gold member.  But it is just Microsoft marketing as normal. 

If you never known that, then you have nothing to worry about.

---

### Post by linux23dragon on 2008-11-24
> **sondosia said:**
> THANK YOU, linux23dragon! That did the trick.

Do you know if there's any chance I could still get the webcam working now, too? I'm almost scared to mess with it anymore...but all the steps I took seemed to have worked, and yet when I plug it in, still no video0 in /dev/. :confused:

Have a look at the kernel log When you plug in the webcam.  It will give you an output in regards to the driver been loaded (if supported or working).

Please post that kernel log output.

---

### Post by Hyperion_1984 on 2008-11-24
> **linux23dragon said:**
> Have a look at the kernel log When you plug in the webcam.  It will give you an output in regards to the driver been loaded (if supported or working).

Please post that kernel log output.

Hello Linux23dragon,

Where do you find the kernel logs? I'm monitoring this post because I'm still trying to make my Logitech Quick-cam for notebook work.

---

### Post by Hyperion_1984 on 2008-11-24
> **Hyperion_1984 said:**
> 
Where do you find the kernel logs? 

Allright, I guess it's ```
$ dmesg
``` ](*,)

Well, now I'm able to compile gspca module using Linux23dragon's technique from this post. However, when i try to load it, I get:

```
$ modprobe gspca
FATAL: Error inserting gspca (/lib/modules/2.6.27-8-generic/kernel/drivers/usb/media/gspca.ko): Operation not permitted
```

```
$ dmesg | grep gspca
[13486.851276] gspca: disagrees about version of symbol video_register_device
[13486.851278] gspca: Unknown symbol video_register_device
[13486.851473] gspca: disagrees about version of symbol video_usercopy
[13486.851474] gspca: Unknown symbol video_usercopy
[13486.851513] gspca: disagrees about version of symbol video_device_release
[13486.851514] gspca: Unknown symbol video_device_release
```

I'm totally confused

---

### Post by linux23dragon on 2008-11-25
> **Hyperion_1984 said:**
> Allright, I guess it's ```
$ dmesg
``` ](*,)

Well, now I'm able to compile gspca module using Linux23dragon's technique from this post. However, when i try to load it, I get:

```
$ modprobe gspca
FATAL: Error inserting gspca (/lib/modules/2.6.27-8-generic/kernel/drivers/usb/media/gspca.ko): Operation not permitted
```

```
$ dmesg | grep gspca
[13486.851276] gspca: disagrees about version of symbol video_register_device
[13486.851278] gspca: Unknown symbol video_register_device
[13486.851473] gspca: disagrees about version of symbol video_usercopy
[13486.851474] gspca: Unknown symbol video_usercopy
[13486.851513] gspca: disagrees about version of symbol video_device_release
[13486.851514] gspca: Unknown symbol video_device_release
```

I'm totally confused

Your webcam uses the ***uvcvideo*** driver that had been installed with the new ***GSPCA*** drivers.

The driver should automatically load itself once you plug in your webcam.   Test the new driver with Ekiga

---

### Post by linux23dragon on 2008-11-26
> **Hyperion_1984 said:**
> Allright, I guess it's ```
$ dmesg
``` ](*,)

```
$ modprobe gspca
FATAL: Error inserting gspca (/lib/modules/2.6.27-8-generic/kernel/drivers/usb/media/gspca.ko): Operation not permitted
```



So the 2.6.27-8-generic does not have the webcam fix implemented yet?

---

### Post by Hyperion_1984 on 2008-11-26
> **linux23dragon said:**
> So the 2.6.27-8-generic does not have the webcam fix implemented yet?

It doesn't seem so.

---

### Post by cyrulution on 2008-11-26
Now I tried everything I could try out. Still the same: the webcam (Logitec Communicate STX) just brings scrambled colours in Skype. 

The webcam is working fine in cheese and xawtv. The camera's built in mic is working fine in skype as well.

HELP!  Any idea??

---

### Post by Yezinki on 2008-11-27
> **cyrulution said:**
> Now I tried everything I could try out. Still the same: the webcam (Logitec Communicate STX) just brings scrambled colours in Skype. 

The webcam is working fine in cheese and xawtv. The camera's built in mic is working fine in skype as well.

HELP!  Any idea??

The webacam has no Linux/Ubuntu support!

Regards!

Yezinki.

---

### Post by cyrulution on 2008-11-27
> **Yezinki said:**
> The webacam has no Linux/Ubuntu support!

Even though it works fine with Cheese and xawtv.
So I assume there's something wrong with Skype video.

---

### Post by Yezinki on 2008-11-27
Does it function in aMSN??

---

### Post by rs2pl on 2008-11-27
I actually really enjoy reading your blog. Glad you’re sticking around! And I must say, I absolutely love the title of your blog .

---

### Post by kkady32 on 2008-11-27
i solved this problem for my webcam Z-Star Vimicro ZC0303 with install new libv4l from:[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

---

### Post by Yezinki on 2008-11-27
> **kkady32 said:**
> i solved this problem for my webcam Z-Star Vimicro ZC0303 with install new libv4l from:[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

Linux23dragon compiled one too.

Only good for Ekiga.

Zstar works with Ekiga even with out it.

But never functions either with aMSN or Skype.

Regards,

Yezinki.

---

### Post by kkady32 on 2008-11-27
work and with gyache

---

### Post by Yezinki on 2008-11-27
Whats gyache...does it function with a window user?

---

### Post by cyrulution on 2008-11-27
[SIZE="3"]I finally found the solution:[/SIZE]
[SIZE="3"]the "Test"-button in Skype is the problem.[/SIZE]
When clicking "Test" there's still green garbage.

As soon as I clicked the "Apply" button I had an excellent picture. Even a cheap webcam from the supermarket did work fine as well.

---

### Post by Yezinki on 2008-11-27
Great I shall try when I install 8.10.

What do I need to compile, after installation & software upgrade?

Regards,

Yezinki.

---

### Post by cyrulution on 2008-11-27
> **Yezinki said:**
> Great I shall try when I install 8.10.

What do I need to compile, after installation & software upgrade?

I must confess: I don't really know. I tried out everything I found here, but I never did hit the "apply" button, I always just clicked on "Test".

So: libv4l is not bad, the gspa drivers are not bad, removing the backports and reinstalling the restricted modules is not bad.

But don't ask me if anything of these was really needed. It all did no harm. I never found a hint about clicking the "apply" button instead of the "test" button in Skype-options here in the forum. So the camera might just work without all the hints and tricks. Mine did work in Hardy without problems ...

---

### Post by Hyperion_1984 on 2008-11-27
Cyrulution,

I confirm, I also have webcam functions in Skype although I have green garbage when I press on test. 

With aMSN, I cannot see any image when I configure the webcam, but I can use it in a conversation. There's still one problem: I only see 1/4 of my webcam field of view (top left). Did someone ever experience such thing?

---

### Post by Yezinki on 2008-11-27
> **cyrulution said:**
> I must confess: I don't really know. I tried out everything I found here, but I never did hit the "apply" button, I always just clicked on "Test".

So: libv4l is not bad, the gspa drivers are not bad, removing the backports and reinstalling the restricted modules is not bad.

But don't ask me if anything of these was really needed. It all did no harm. I never found a hint about clicking the "apply" button instead of the "test" button in Skype-options here in the forum. So the camera might just work without all the hints and tricks. Mine did work in Hardy without problems ...

Let Linux King have a look....if it was so simple I would have my cam woking in Skype/aMSN......& the real issue is video exchange btw Ubuntu & Windows....for that only Logitech Quick Cam Pro 9000 works.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-28
> **kkady32 said:**
> i solved this problem for my webcam Z-Star Vimicro ZC0303 with install new libv4l from:[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

Thanks for that report kkady32.  The v4L libs is something I have overlooked.

So is the updated V4L libs already available for download?  I have not had the chance to check.

Then again, it is possible that it will be updated with the future kernel fix.

---

### Post by linux23dragon on 2008-11-28
> **cyrulution said:**
> I must confess: I don't really know. I tried out everything I found here, but I never did hit the "apply" button, I always just clicked on "Test".

So: libv4l is not bad, the gspa drivers are not bad, removing the backports and reinstalling the restricted modules is not bad.

But don't ask me if anything of these was really needed. It all did no harm. I never found a hint about clicking the "apply" button instead of the "test" button in Skype-options here in the forum. So the camera might just work without all the hints and tricks. Mine did work in Hardy without problems ...

Most issues at this time seem to be related with both webcam driver and V4L.
If future bug fix updates (kernel and V4L libs) fix the aMSN issues is yet to be seen.  I have not tested the new V4L libs at all.

---

### Post by MTHarden on 2008-11-28
This had worked for me until today. Today was a kernel update to 2.6.27-9 and so after the update I restarted, and my webcam wasn't working. So I re-ran the command that is suggested at the start of the post, but to no avail. My Microsoft VX-1000 just has a solid on-light and no software seems to detect it for input. I'm not sure what information to gather to post here, but if you let me know I'll do my best.

---

### Post by Yezinki on 2008-11-28
Mine works using Ekiga with V4L not V4L2, whether drivers compiled, softwares/kernels updated or not...

But wont work with aMSN or Skype.

I mean the Z micro cam.

But windows is more handy no bugs lol

---

### Post by cyrulution on 2008-11-28
> **Yezinki said:**
> But windows is more handy no bugs lol

Sorry, there is one bug: the operating system.

---

### Post by Hyperion_1984 on 2008-11-28
> **cyrulution said:**
> Sorry, there is one bug: the operating system.

I couldn't agree more.

---

### Post by Yezinki on 2008-11-28
I know most dont like windows...do do I.

But keep in mind my age, profession, to learn a OS at this stage of my life.

I would love to have a customized DVD of Ubuntu 8.10 using Remastersys.....having all its ulities installed like desktop, Compiz, Vbox, Wine, Vista & MS Office Eneterprise installed in Vbox....of course I shall send you the keys & the money. lol

I pay to MS so why not pay if some one take a load of my head.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-28
Hey LINUX KING!!

How did the Thanks Giving go.....hope you had a chill.

KING care to answer my posts about:

 1. External Graphic card in Hardware section.

2. Partition Utility queries in Other OS> Windows.

My Best Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-29
Quality of Quick cam Pro 9000 in Ubuntu 8.10.

---

### Post by Yezinki on 2008-11-29
[IMG]http://i4.photobucket.com/albums/y129/eDOC/Picture2.jpg[/IMG]

Who says Quick Cam Pro 9000 doesn't work AWESOME in 8.10.....with only 128 MB of Video......imagine if I had a PCI card & not a built in Intel 128 graphics........no wonder am so desperate to install a PCI card.

Regards,

Yezinki.

---

### Post by Bladze DCOTL on 2008-11-29
Hello,

I have an Asus F3 laptop with built in Syntek webcam that worked under the 8.04 edition but I still have not been able to get it to work with 8.10.  The system seems to recognize the cam but it just won't start it.  I have been through many posts and tryed quite a few of the possible solutions including the ones in this post, but still no joy.  All I ever get is Video device not found, or missing /dev/video0....

~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1410:4100 Novatel Wireless U727
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any ideas here?

---

### Post by linux23dragon on 2008-11-29
***[B][I]UPDATE 29-11-08*** :- The kernel today (29-11-08 ) has been updated to 2.6.27-9.  These installation instructions have not been tested with this new Ubuntu kernel.
                   Please post a bug at [***_[COLOR="Blue"]Luanchpad[/COLOR]_***]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506") if you come across any webcam issues and help test the patch fixes that has been submitted.  The next kernel update may include the fixes.  Currently there is updates for libV4l and kernel fixes that has not yet been implemented.   

Due to my own [***_[COLOR="Blue"]personal studies[/COLOR]_***]("http://www.adam.com.au/linux23d") on Investing, Trading and time spent on market research, I will no longer be able to support people in a timely manner.  This means that I won't be able to constantly update instructions to support later Ubuntu kernel updates or give anyone immediate support.   [/B][/I]

---

### Post by csseurg6 on 2008-11-29
Hi,

the method doesn't work with this webcam:

```
ID 046d:0870 Logitech, Inc. QuickCam Express
```

a labtec webcam, and she works great on ubuntu 7.10 or 8.04.


Bye :)

---

### Post by csseurg6 on 2008-11-30
Always doesnt'work with the 2.6.27-10 kernel in -proposed :(

bye

---

### Post by jawohls on 2008-11-30
I could use some help here as I am confused.....



my webcam is a new Logitech Quickcam Communicator MP

and works flawlessly on my desktop which was 7.10 upgraded to 8.4 upgraded to 8.10 (kernel 2.6.27-9-generic)

but does not work on my laptop with a fresh install of of 8.10 (kernel 2.6.27-9-generic). Cheese will start the webcam but no display (i.e active light comes on)


lsusb on laptop report :

 lsusb
Bus 001 Device 003: ID 046d:09a1 Logitech, Inc. 
Bus 001 Device 002: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg on laptop:

[ 1260.327574] Linux video capture interface: v2.00
[ 1260.570265] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
[ 1260.590520] input: UVC Camera (046d:09a1) as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input11
[ 1260.594579] usbcore: registered new interface driver snd-usb-audio
[ 1260.597019] usbcore: registered new interface driver uvcvideo
[ 1260.598916] USB Video Class driver (v0.1.0)


Should I follow the instructions listed at the start of this thread or could there be something else....???????

---

### Post by ivainsencher on 2008-12-04
solved? really?
$ lsusb
Bus 005 Device 006: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 005: ID 05ca:183a Ricoh Co., Ltd 
Bus 005 Device 002: ID 054c:02d5 Sony Corp. 
Bus 005 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 147e:2016  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1366x768+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
looking for available devices
port 80-95
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

port 96-96
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

might this be the culprit?
$ sudo modprobe gspca
FATAL: Module gspca not found.

---

### Post by bro on 2008-12-08
I wonder too. My webcam doesn't work properly. It works only in Skype. Not in cheese or camorama (can't connect to /dev/video0).

---

### Post by lolwhites on 2008-12-09
Having the same problem as bro. Since upgrading to 2.6.27-10, my 150 Spacecam Portable is no longer detected by most applications. Skype can see it but the picture is awful.

Edit - AMSN can see it, but not Camorama

---

### Post by linux23dragon on 2008-12-09
As already stated, the instructions are not tested with the latest kernel updates.  

All code has been removed to prevent future issues.

Thread should be clossed.

---

### Post by MTHarden on 2008-12-14
Well I had done the code that used to be here (which maybe we should leave here just strike-through or something) on the previous kernel, and it worked. Then with the recent kernel update I have problems again (solid green on light, not detected in cheese etc.). So even if what used to be here, wouldn't work to fix my problem this time, do I need to UNDO what I had done? If so... how?

I wish this "just worked"

Which Webcams do just work?

---

### Post by wonderer on 2009-01-27
Hi Guys,

I had mega problems like you are having and found this site: [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
download and install the packs you need and I hope it will fly for you as well.Specially for skype, I could use ekiga and cheese but not skype, now deinstall the skype you got and install it from there you need common first and then skype.

---

### Post by wonderer on 2009-01-27
Check my post #241 on this forum.

---

### Post by eddielad on 2009-02-09
To echo MTHarden's question in post #240 

"Which Webcams do just work?"

I am in the fortunate position of having no webcam at all at the moment - so all I want to know is the name / model of an OK 1.3 Mega Pixel camera that will work with Ubuntu 8.10 (Skype etc) out-of-the box. 

Does anyone have a list of known good webcams ?

It appears that buying the wrong kit can lead to a lot of messing about.

Any suggestions appreciated ?  :)

---

### Post by eddielad on 2009-02-22
OK then, to provide "an answer" to the question above - I can confirm that the Logitech QuickCam E3500 does work straight out of the box with the troublesome Ubuntu 8.10. Skype picks it up without any issues whatsoever which seems to be the acid test according to other forums and posts. Mine cost £13 from Amazon.co.uk but other on-line retailers are available.

I have heard good things about the Logitech range generally w.r.t compatibility but can't confirm that any other model will definitely work.

---

### Post by linux23dragon on 2009-02-25
> **eddielad said:**
> OK then, to provide "an answer" to the question above - I can confirm that the Logitech QuickCam E3500 does work straight out of the box with the troublesome Ubuntu 8.10. Skype picks it up without any issues whatsoever which seems to be the acid test according to other forums and posts. Mine cost £13 from Amazon.co.uk but other on-line retailers are available.

I have heard good things about the Logitech range generally w.r.t compatibility but can't confirm that any other model will definitely work.

Sorry, I have been busy making money for free.  Well actually with out having to work for money.  Please see my [[COLOR="Blue"]web page[/COLOR]]("http://adam.com.au/linux23d") for more info.

In regards to known working web cams?  please see this link.
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by monkotronic on 2009-03-12
Thank You!!!  My skype is working with my logitech quickcam communicate STX!  after at least 6 other suggestions from other pages, yours was the one that worked!

(see post #241)

---

### Post by question-authority on 2009-05-18
Hey linuxdragon, 

I just bought a Dynex webcam and I can not get anything to acknowledge it in ubuntu 8.10. I am a complete noob with all this too. Do you know where I should start?

Thanks, Tim

---

### Post by RavanH on 2009-10-28
> **wonderer said:**
> Hi Guys,

I had mega problems like you are having and found this site: [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
download and install the packs you need and I hope it will fly for you as well.Specially for skype, I could use ekiga and cheese but not skype, now deinstall the skype you got and install it from there you need common first and then skype.

Thanks wonderer, I was having trouble with the latest Skype (2.1something) and your tip (going back to the 2.0 version in Medibuntu) fixed all cam (Logitech QuickCam Communicator STX) problems for me too! 

Golden!

---

