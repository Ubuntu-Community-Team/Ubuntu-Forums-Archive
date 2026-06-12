---
title: "Smartcam"
date: 2008-11-04
forum: General Help
---

### Post by pedrom169 on 2008-11-04
has anyone got this program to work on ubuntu. it has a linux port

[http://sourceforge.net/projects/smartcam]("http://sourceforge.net/projects/smartcam")

and has anyone got it to work with amsn?

---

### Post by luxten on 2009-04-25
Hi pedrom169

I recently installed the smartcam for linux and my nokia 6120c and after a while i got it working.

I put here the general process that i made, i made it work on Fedora 10. i hope it works for you under Ubuntu.

Get the latest version of smartcam for linux

[http://sourceforge.net/project/downloading.php?group_id=197856&filename=smartcam_v_2008.09.18.2.zip&a=68574644](http://sourceforge.net/project/downloading.php?group_id=197856&filename=smartcam_v_2008.09.18.2.zip&a=68574644)

if you have a kernel 2.6.28.x you will have to patch the smartcam
get the patch

[http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch](http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch)

then unzip the smartcam
[COLOR=#cc6600]
$ unzip smartcam_v_2008.09.18.2.zip[/COLOR]
$ cd smartcam/
$ patch -p0 < smartcam-linux-2.6.27.1.patch 
patching file src/driver/smartcam.c

then compile the driver

$ cd src/driver
$ make -C /lib/modules/`uname -r`/build M=`pwd` modules  # <-- To compile it
make: Entering directory `/usr/src/linux-2.6.27.21'
  Building modules, stage 2.
  MODPOST 1 modules
make: Leaving directory `/usr/src/linux-2.6.27.21'

$ sudo insmod smartcam.ko            # <-- To load it
$ lsmod | grep smartcam              # <-- To check if it's loaded

smartcam                5720  0 
videodev               29376  2 smartcam,pwc

$ cd ../..                           # <-- Return to the smartcam directory


at this time you should have compiled it
make sure you have **[COLOR=#660000]libbluetooth-dev , [/COLOR]****[[COLOR=#3366ff]bluez library[/COLOR]]("http://www.gp32x.com/board/%5C%22http://bluez.sourceforge.net/%5C%22") , **


then execute 

./release/smartcam

more probably you should do this, if it returns an error that you don't have libbluetooth.so.2 , what i did to solve it was create a symbolic link of this way  
           $ sudo  ln -s   /usr/lib/libbluetooth.so.3.2.0    /usr/lib/libbluetooth.so.2 
the try again the above command to compile.

$ cd src/app
$ gcc `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lbluetooth smartcam.c -o smartcam
$ ./smartcam
Found smartcam device file: /dev/video0
port = 1


Get the smartcam 1.3 for S60 3rd edition phone
[http://www.easy-share.com/c/1903225886](http://www.easy-share.com/c/1903225886)
or [http://www.ziddu.com/download/3161365/SmartCam_v1.3.zip.html](http://www.ziddu.com/download/3161365/SmartCam_v1.3.zip.html)

then install the SmartCamS603rdEd_v1_3.sis on the phone
in sourceforge there is the 1.4 for S60 but it has problem running with the bluez package at least to me it didn't work.

in the directory    smartcam/src/driver       
as root run
$sudo cp smartcam.ko   /lib/modules/2.6.27.21-170.2.56.fc10.i686/extra/

$ sudo  /sbin/modprobe videodev
$ sudo  /sbin/insmod smartcam.ko

then run 
$ /sbin/lsmod | grep smartcam

it should give you some like this

smartcam               10008  0 
videodev               32000  1 smartcam

 if you wish you can copy smartcam to /usr/local/bin    to all users

inside    /smartcam/src/app
$ sudo cp smartcam   /usr/local/bin/smartcam

I did a script for starting the service 

$ nano /etc/init.d/smartcam

and  i write

#!/bin/sh
cd /home/user/smartcam/src/driver
/sbin/insmod smartcam.ko
/sbin/modprobe smartcam


that's all run the smartcam on linux

./smartcam/src/app/smartcam

then run the application on the phone. Enjoy it. :)

---

### Post by ukblacknight on 2009-04-30
> **luxten said:**
> Hi pedrom169

I recently installed the smartcam for linux and my nokia 6120c and after a while i got it working.

I put here the general process that i made, i made it work on Fedora 10. i hope it works for you under Ubuntu.

Get the latest version of smartcam for linux

[http://sourceforge.net/project/downloading.php?group_id=197856&filename=smartcam_v_2008.09.18.2.zip&a=68574644](http://sourceforge.net/project/downloading.php?group_id=197856&filename=smartcam_v_2008.09.18.2.zip&a=68574644)

if you have a kernel 2.6.28.x you will have to patch the smartcam
get the patch

[http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch](http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch)

then unzip the smartcam
[COLOR=#cc6600]
$ unzip smartcam_v_2008.09.18.2.zip[/COLOR]
$ cd smartcam/
$ patch -p0 < smartcam-linux-2.6.27.1.patch 
patching file src/driver/smartcam.c

then compile the driver

$ cd src/driver
$ make -C /lib/modules/`uname -r`/build M=`pwd` modules  # <-- To compile it
make: Entering directory `/usr/src/linux-2.6.27.21'
  Building modules, stage 2.
  MODPOST 1 modules
make: Leaving directory `/usr/src/linux-2.6.27.21'

$ sudo insmod smartcam.ko            # <-- To load it
$ lsmod | grep smartcam              # <-- To check if it's loaded

smartcam                5720  0 
videodev               29376  2 smartcam,pwc

$ cd ../..                           # <-- Return to the smartcam directory


at this time you should have compiled it
make sure you have **[COLOR=#660000]libbluetooth-dev , [/COLOR]****[[COLOR=#3366ff]bluez library[/COLOR]]("http://www.gp32x.com/board/%5C%22http://bluez.sourceforge.net/%5C%22") , **


then execute 

./release/smartcam

more probably you should do this, if it returns an error that you don't have libbluetooth.so.2 , what i did to solve it was create a symbolic link of this way  
           $ sudo  ln -s   /usr/lib/libbluetooth.so.3.2.0    /usr/lib/libbluetooth.so.2 
the try again the above command to compile.

$ cd src/app
$ gcc `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lbluetooth smartcam.c -o smartcam
$ ./smartcam
Found smartcam device file: /dev/video0
port = 1


Get the smartcam 1.3 for S60 3rd edition phone
[http://www.easy-share.com/c/1903225886](http://www.easy-share.com/c/1903225886)
or [http://www.ziddu.com/download/3161365/SmartCam_v1.3.zip.html](http://www.ziddu.com/download/3161365/SmartCam_v1.3.zip.html)

then install the SmartCamS603rdEd_v1_3.sis on the phone
in sourceforge there is the 1.4 for S60 but it has problem running with the bluez package at least to me it didn't work.

in the directory    smartcam/src/driver       
as root run
$sudo cp smartcam.ko   /lib/modules/2.6.27.21-170.2.56.fc10.i686/extra/

$ sudo  /sbin/modprobe videodev
$ sudo  /sbin/insmod smartcam.ko

then run 
$ /sbin/lsmod | grep smartcam

it should give you some like this

smartcam               10008  0 
videodev               32000  1 smartcam

 if you wish you can copy smartcam to /usr/local/bin    to all users

inside    /smartcam/src/app
$ sudo cp smartcam   /usr/local/bin/smartcam

I did a script for starting the service 

$ nano /etc/init.d/smartcam

and  i write

#!/bin/sh
cd /home/user/smartcam/src/driver
/sbin/insmod smartcam.ko
/sbin/modprobe smartcam


that's all run the smartcam on linux

./smartcam/src/app/smartcam

then run the application on the phone. Enjoy it. :)

Hi Luxten,

Cheers for proving a comprehensive guide for this!! I'm trying to get it working for my Nokia N96.

I've patched the driver, and now I'm trying to do the "insmod" line, however i'm getting this:

```
tom@blacknight:~/Downloads/Firefox/Smartcam/smartcam/src/driver$ sudo insmod smartcam.ko
insmod: error inserting 'smartcam.ko': -1 Unknown symbol in module

```

Any ideas what this is?  Also, in your codes, you always have "#" at the end, I'm assuming that isn't supposed to be part of the commands?

If I could get this working it'd be great!

I'm running Ubuntu 9.04 x86_64.

---

### Post by luxten on 2009-05-05
Hi Ukblacknight

I reproduced the error you're having.
While trying to load first the module smartcam.ko inside the folder where it was compiled.

the same error even running as root

#  insmod: error inserting 'smartcam.ko': -1 Unknown symbol in module

Try to load first the videodev with

sudo  /sbin/modprobe videodev

then inside /smartcam/src/driver

run as root

sudo  /sbin/insmod smartcam.ko 

 it should not return an error, if you are here now. check 


/sbin/lsmod | grep smartcam

smartcam               10008  0 
videodev               32000  1 smartcam


If you see something like this, the module smartcam is loaded.
 
I hope it works.

---

### Post by luxten on 2009-05-05
Sorry Ukblacknight

exactly where appears the # at the end doesn't form part of the code, then is a comment.

Could you compile the smartcam successfully?

after applying the patch?


Regards

---

### Post by ukblacknight on 2009-05-05
Hi Luxten,

**Driver**

I did the insmod command, in which it said Segmentation fault, *however*, checking the kernel for the module shows:

```

smartcam               16380  1 
videodev               45184  1 smartcam

```

Plus, trying the command again says that it's already loaded!

**Application**

Trying to execute ./release/smartcam gives:

```

tom@blacknight:~/Downloads/Firefox/Smartcam/smartcam$ ./release/smartcam
./release/smartcam: error while loading shared libraries: libbluetooth.so.2: cannot open shared object file: No such file or directory

```

I've created the symbolic link as in the description.

Now then, I'm unable to compile the application, as it churns out lots of errors when I run the gcc command!

The first 7 lines look like the following:

```

smartcam.c:25:33: error: bluetooth/bluetooth.h: No such file or directory
smartcam.c:26:30: error: bluetooth/rfcomm.h: No such file or directory
smartcam.c:27:27: error: bluetooth/sdp.h: No such file or directory
smartcam.c:28:31: error: bluetooth/sdp_lib.h: No such file or directory
smartcam.c:57: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
smartcam.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
smartcam.c:79: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token

```

I'd really like this application to work, as it saves me buying a web cam when I have one already sitting on my desk!

---

### Post by ukblacknight on 2009-05-05
Well, I've made some advances, to the point where the application is half working!

I deleted the smartcam.* files and started again, this time the driver was added successfully.

I then tried the compile of the application, which again failed.

**Important**

```
sudo apt-get install gnome-common libbluetooth-dev
```

This prevents the compile errors I get when trying to compile the application.

I can install the J2ME apps to my phone, however the .SIS versions say that the certificate has expired.  Now, I've managed to make it transmit - but only a picture.  The phone constantly asks for permission for the application to access the camera, in which when you press yes, it takes a photo, sends it to the smartcam app, and then the phone requests permission again!

It does this on both my Nokia N95 and N96.  I'll try it on my N73 (yes, I have many phones lying around :P)

I'd rather have the .SIS version, as I'd imagine the security problem wouldn't be so bad!

---

### Post by luxten on 2009-05-05
hi ukblacknight

Did you get the   SmartCam_v1.3.zip (0.4 MB)  from
 [http://www.easy-share.com/c/1903225886](http://www.easy-share.com/c/1903225886)


I also had that inconvenient with the java application, and with version sisx 1.4 caused an unknow error while communicating with the smartcam on linux, so i found the sisx version 1.3 i installed it and it's working since that installation.

When you said 
I then tried the compile of the application, which again failed.

You mean at this point?, when you run it does it cause an error or not?.

$ cd src/app
# gcc `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lbluetooth smartcam.c -o smartcam
$ ./smartcam
Found smartcam device file: /dev/video0
port = 1


As i hear you said you have half working, so try installing the 1.3 sisx version.

---

### Post by luxten on 2009-05-05
Sorry i said sisx file, but inside of the compressed file there is a file named SmartCamS603rdEd_v1_3.sis that is the program i'm using.

:popcorn:

---

### Post by ukblacknight on 2009-05-06
Cheers luxten, that did the trick!

I'd had it working yesterday but the application kept crashing, something about X server.  Seems to be OK now though...

Do you need to run your application as root in order for it to work?

---

### Post by luxten on 2009-05-06
Hi

After creating the symbolic link try updating the dependences.

$  sudo /sbin/depmod -a

Then be sure to run gcc into the directory /smartcam/src/app

gcc `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lbluetooth smartcam.c -o smartcam

If you run gcc into the /src/driver directory you get some errors like these:

smartcam.c:28:26: error: linux/module.h: No such file or directory
smartcam.c:31:27: error: linux/vmalloc.h: No such file or directory
smartcam.c:34:22: error: linux/mm.h: No such file or directory
smartcam.c:40:29: error: linux/interrupt.h: No such file or directory
smartcam.c:41:30: error: media/v4l2-ioctl.h: No such file or directory
smartcam.c:42:31: error: media/v4l2-common.h: No such file or directory
smartcam.c:96: warning: parameter names (without types) in function declaration
smartcam.c:107: warning: ‘struct file’ declared inside parameter list
smartcam.c:107: warning: its scope is only this definition or declaration, which is probably not what you want


Once you have loaded the smartcam module look at 

$ ls -l  /dev/video*
lrwxrwxrwx 1 root root     6 2008-11-15 13:59 /dev/video -> video0
crw-rw—- 1 root root 81, 0 2008-11-15 13:59 /dev/video0 

those nodes are created when loading the module, as you see they are available for root, so you have to modify the permissions editing an udev file which allow the user to access that resource.

as root edit

nano **/lib/udev/rules.d/50-udev-default.rules**
or 
gedit **/lib/udev/rules.d/50-udev-default.rules**

Search for the video4linux and change the line that reads:
 **KERNEL==”video0&#8243;,               SYMLINK+=”video”**
 

to this:


**KERNEL==”video0&#8243;,               SYMLINK+=”video”, MODE=”0666&#8243;**

Remove and reload the SmartCam kernel module. 

$ sudo /sbin/modprobe -r smartcam


$ sudo  /sbin/modprobe videodev

then inside /smartcam/src/driver

run as root

$ sudo  /sbin/insmod smartcam.ko 

Now verify that the permissions for the nodes have changed to allow all users

$ ls -l /dev/video*
lrwxrwxrwx 1 root root     6 2008-11-15 14:05 /dev/video -> video0
crw-rw-rw- 1 root root 81, 0 2008-11-15 14:05 /dev/video0

:P

---

### Post by dmanresa on 2009-05-15
I followed all the instructions you recomend here, but I still have a Segmentation fault running insmod.
I am running Ubuntu 9.04 32bits.

These are the instructions I followed:

Get the version 1.3 of smartcam for linux (I also tryed with the last version 1.4)

[http://sourceforge.net/project/downl...zip&a=68574644]("http://sourceforge.net/project/downloading.php?group_id=197856&filename=smartcam_v_2008.09.18.2.zip&a=68574644")

As I have a kernel 2.6.28.x I have to patch the smartcam
Get the patch [http://launchpadlibrarian.net/192222...2.6.27.1.patch]("http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch")

And patch:

```
$ unzip smartcam_v_2008.09.18.2.zip
$ cd smartcam/
$ patch -p0 < smartcam-linux-2.6.27.1.patch 
patching file src/driver/smartcam.c
```Before compiling I installed some bluetooth stuff that is recomended in this post.

```
sudo apt-get install gnome-common libbluetooth-dev
```I also did the link to the bluetooth libs recomended in this post.

```
$ sudo  ln -s   /usr/lib/libbluetooth.so.3.2.1    /usr/lib/libbluetooth.so.2 
```I compiled the driver without problems.

```
$ cd src/driver
$ make -C /lib/modules/`uname -r`/build M=`pwd` modules
```Then I loaded the drivers in this order (without this order i got a insmod: error inserting 'smartcam.ko': -1 Unknown symbol in module)

```
sudo  /sbin/modprobe videodev
sudo  /sbin/insmod smartcam.ko 

```But then I still get a Segmentation fault. 

***[ukblacknight]("http://ubuntuforums.org/member.php?u=426783")*** says that he had the same problem and starting from scratch solves the problem, but there should be something more.

Any ideas?

---

### Post by ukblacknight on 2009-05-15
Hmm I really should of written down here what I did to fix that!  When you run one of the commands it makes a load of smartcam.* files.  I deleted all of them except smartcam.c and kept trying to compile it.

I can't remember if I did anything extra.  Make sure you use

```
sudo /bin/insmod
```

I'll try to remember what I did in the meanwhile, however, just keep trying at it, it will work eventually.

---

### Post by C0p3rn1c on 2009-05-22
sudo /sbin/insmod smartcam.ko
insmod: error inserting 'smartcam.ko': -1 File exists

---

### Post by Cyr4x on 2009-05-25
So that means the module has been loaded before. Reboot and try again.

Segmentation fault for me too. Any solution?

EDIT:
Solution found. Just uncomment line 603 in smartcam.c before compiling the driver. Segmentation fault doesn't occure anymore.

EDIT 2:
Did anyone get to work symbian app v1.4? For me it causes an error while connecting via bluetooth. 1.3 works perfect, but only in QCIF (176x144) resolution. My camera in Nokia 6120 classic can record 320x240 video and 1.4 app can do it too, but doesn't work.

After trying to connect with 1.4, smartcam does:
[http://www.wklej.org/id/96379/](http://www.wklej.org/id/96379/)

---

### Post by dominic1134 on 2009-06-28
Hello,

i have some problems with smartcam on my  2.6.28-13-generic jackelope..

The ./smartcam app is loading and prompting me the following error message 
 **"Could not find smartcam device file. Please load (insmod) the driver and try again."**


1) I did compile the driver correctly && loaded it correctly
2) i patched the driver with the smartcam-linux-2.6.27.1.patch before compiling
3) i have installed the gnome-common and libbluetooth-dev packages, before compiling



```
root@desktop:/root/smartcam/src/app#   ./smartcam 
Cannot identify '/dev/video0': 2, No such file or directory
Cannot identify '/dev/video1': 2, No such file or directory
Cannot identify '/dev/video2': 2, No such file or directory
Cannot identify '/dev/video3': 2, No such file or directory
Cannot identify '/dev/video4': 2, No such file or directory
Cannot identify '/dev/video5': 2, No such file or directory
Cannot identify '/dev/video6': 2, No such file or directory
Cannot identify '/dev/video7': 2, No such file or directory
Cannot identify '/dev/video8': 2, No such file or directory
Cannot identify '/dev/video9': 2, No such file or directory
stop server, record = 0, sdp_session = 0, client_sock = -1, server_sock = -1

``````
root@desktop:/root/smartcam/src/app#    lsmod | grep smartcam
smartcam               14942  1 
videodev               41600  1 smartcam

```

Any ideas?

thanks in advance!

---

### Post by Cyr4x on 2009-07-22
There's a new v1.4.0 Linux app for download on Smartcam's Sourceforge page. Now as a deb too, but only the app. You have to download sources and compile the smartcam.ko driver. I thought it will work with included Symbian v1.4 app, but still nothing. The same error as listed above. We have to use v1.3 app.

---

### Post by zache on 2009-08-02
> **Cyr4x said:**
> There's a new v1.4.0 Linux app for download on Smartcam's Sourceforge page. Now as a deb too, but only the app. You have to download sources and compile the smartcam.ko driver. I thought it will work with included Symbian v1.4 app, but still nothing. The same error as listed above. We have to use v1.3 app.

  Hmm, v1.4.0 symbian app seems to work with N78 nicely, but linux driver crashes when smartcam app is started. I made a small patch which fixes the kernel oops of smartcam.ko for kernel 2.6.29.4.  

- [http://zache.kapsi.fi/misc/smartcam-2.6.29.4.patch](http://zache.kapsi.fi/misc/smartcam-2.6.29.4.patch)  

to apply the patch:  

$ cd smartcam-1.4.0/driver_src 
$ wget [http://zache.kapsi.fi/misc/smartcam-2.6.29.4.patch](http://zache.kapsi.fi/misc/smartcam-2.6.29.4.patch) 
$ patch -p0 < smartcam-2.6.29.4.patch 
$ make -C /lib/modules/`uname -r`/build M=`pwd` modules 
$ sudo rmmod -f smartcam.ko 
$ sudo insmod ./smartcam.ko  

After that program crashes also if sdp_connect fails in CommHandler.cpp file and I needed to do stop and start bluetooth subsystem before smartcam could connect to sdp.    

$ sudo /sbin/init.d/bluetooth stop 
$ sudo /sbin/init.d/bluetooth start  

Note:  for some reason "sudo /sbin/init.d/bluetooth restart" didn't work for this.

---

### Post by Cyr4x on 2009-08-07
Problem solved. 1.4.0 works out of the box. I just had an old binary in /usr/local/bin and didn't knew about it.

EDIT:
On 9.10 are problems with compiling the driver again:
[http://www.wklej.org/id/198260/](http://www.wklej.org/id/198260/)

---

### Post by gyterpena on 2009-11-22
Patch for 2.6.31-14-generic (9.10) is here [http://en.pastebin.ca/1666682](http://en.pastebin.ca/1666682)
more info [http://sourceforge.net/projects/smartcam/forums/forum/702661/topic/3397401](http://sourceforge.net/projects/smartcam/forums/forum/702661/topic/3397401)

---

### Post by fatihsanli58 on 2009-11-23
hi
is there any patch for he kernel 2.6.31-15?

---

### Post by fatihsanli58 on 2009-11-23
hi again,
problem solved. here what i have done:
1. download the following files.
([http://sourceforge.net/projects/smartcam/files/smartcam_linux/smartcam_linux_v_1.4.0/smartcam-1.4.0.tar.gz](http://sourceforge.net/projects/smartcam/files/smartcam_linux/smartcam_linux_v_1.4.0/smartcam-1.4.0.tar.gz))
smartcam-1.4.0.tar.gz
smartcam_1.4.0_i386.deb
2. cd smartcam-1.4.0/driver_src/
3. patch the smartcam.c file with the patch which is attached
patch -p0 < karmic.patch smartcam.c
4.sudo apt-get install linux-headers-$(uname -r)
5.sudo apt-get install build-essential
6.sudo apt-get install libgtk2.0-dev
7.sudo make -C /lib/modules/`uname -r`/build M=`pwd`
8.gksu gedit /etc/modules add this line 
videodev
9./sbin/modprobe videodev
10./sbin/insmod smartcam.ko

that is all. hope it works.
(source [http://forum.ubuntu-it.org/index.php?topic=262984.msg2145165](http://forum.ubuntu-it.org/index.php?topic=262984.msg2145165))

---

### Post by fatihsanli58 on 2009-11-23
every time you should repeat the last two steps. could not find a solution yet.

---

### Post by Cyr4x on 2009-11-23
Yes, it works! Now the driver compiles without problems.

---

### Post by FranJPR on 2009-11-24
I have followed the above instructions and I get this, when compiling the driver,

: .../driver_src$ sudo make -C /lib/modules/`uname -r`/build M=`pwd`                                                                                                               
                                                                                     
make: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'                                        
  LD      .../driver_src/built-in.o                                     
  CC [M]  .../driver_src/smartcam.o                                     
.../driver_src/smartcam.c:554: warning: initialization from incompatible pointer type                                                                                                    
.../driver_src/smartcam.c:555: warning: initialization from incompatible pointer type                                                                                                    
  Building modules, stage 2.                                                                                     
  MODPOST 1 modules                                                                                              
  CC      .../driver_src/smartcam.mod.o                                 
  LD [M]  .../driver_src/smartcam.ko                                    
make: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'

I continue anyways and I load the driver, open the app in my pc and open the jar app in my mobile. It seems it is going to work because the app in the mobile try to connect via bluetooth, it recognizes the pc, and starts the connection. The screen of the mobile becomes black for a while and the app crashes with the following message: 

javax.microedition.media.MediaException: Encoding is invalid
Msg: Encoding is invalid SmartCam will now exit !


Any idea???

:-k

---

### Post by fatihsanli58 on 2009-11-24
which kernel you are using?

---

### Post by FranJPR on 2009-11-24
2.6.31-14-generic

---

### Post by FranJPR on 2009-11-25
I am running Kubuntu Karmic 9.10, I have upgraded to kernel 2.6.31-15-generic and compiled everything again, with the same warnings when compiling the driver, and the same result with the jar app.


#-o

---

### Post by deion on 2009-11-26
the java mobile (j2me) version of SmartCam is no longer compatible with version 1.4.x of the PC application (windows or linux). It is still compatible with version 1.3 of the PC app, so you could use that version...

---

### Post by FranJPR on 2009-11-26
hmmm... 
Compiling the app, version 1.3, I get,

.../src/app$ gcc `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lbluetooth smartcam.c -o smartcam
smartcam.c: In function ‘stop_server’:
smartcam.c:352: warning: format ‘%x’ expects type ‘unsigned int’, but argument 2 has type ‘struct sdp_record_t *’
smartcam.c:352: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘struct sdp_session_t *’

... and I  get the same result as post #16. 

Bad luck!

---

### Post by victor0000 on 2009-11-27
HELLO!!!
ubuntu 9.10
smartcam_1.4.0_i386.deb
```

victor0000@victor0000:~$ uname -r
2.6.31-15-generic-pae
victor0000@victor0000:~$ smartcam
smartcam: registered DBUS service "org.gnome.smartcam"
Found smartcam device file: /dev/video0
smartcam: started comm thread
smartcam: port = 1
Segmentation fault
victor0000@victor0000:~$ dmesg | grep smartcam
[ 1382.467855] smartcam[2188]: segfault at 8 ip 00f0282a sp b6ff90f0 error 4 in libbluetooth.so.3.4.0[ef6000+15000]
victor0000@victor0000:~$ 

```
Help! Please!

---

### Post by alesi_27 on 2009-12-01
Hi, all

First of all thanks for instructions and patch, it worked very well for me both on 2.6.14 and 2.6.15 kernel.
I wish I could insmod smartcam.ko on boot, so I copyed smartcam.ko into

/lib/modules/`uname -r`/kernel/drivers/media/video/

and added videodev and smartcam.ko to /etc/modules

I was hoping that could be enough to insmod smartcam at boot, but it looks like it isn't :)

So I wonder if someone here solved this little issue!!

thanks again,
bye

---

### Post by alesi_27 on 2009-12-01
Sorry, I must be idiot or something, I found that my previous post happen to work

just copying smartcam.ko into /lib/modules/`uname -r`/kernel/drivers/media/video/

and appending to /etc/modules the following lines

videodev
smartcam

is enough to insmod smartcam at boot.

bye.

---

### Post by victor0000 on 2009-12-04
ubuntu 9.10
1. smartcam_1.4.0_i386.deb
2. smartcam1.tar.gz
3. cp smartcam1 /usr/bin/
4. smartcam1
settings -> tcp/wifi -> ok -> ctrl+c
5. smartcam

YES!
:popcorn:

---

### Post by victor0000 on 2009-12-04
OR
gconf-editor
/apps/smartcam/connection_type
0 - bluetooth
1 - TCP (WIFI)
:popcorn:

---

### Post by victor0000 on 2009-12-06
Automatic record Smartcam video!
Installation package ttyrec rand
Shortcut commands 
```

bash -c "ttyrec -e smartcam > ~/smartcam.log"

```

Bash script: smartcamrecord
```

#!/bin/bash
n="0"
y="1"
while true;
do
r1=$(rand)
r2=$(rand)
r3=$(rand)
f=$r1$r2$r3-smartcam.mpg
getlog=$(tail -n 1 ~/smartcam.log | awk '{print $2}')
if [ "$getlog" = "accepted" ];  then
echo "accepted"
if [ "$n" = "0" ]; then
killall mplayer 2>/dev/null
f1=$f
ffmpeg -f video4linux2 -s 320x240 -i /dev/video0 ~/$f1 -y 2>/dev/null &
y="0"
n="1"
fi
fi
if [ "$getlog" = "disconnected"  ]; then
if [ "$y" = "0"  ]; then
killall -9 ffmpeg
mplayer ~/$f1 2>>/dev/null &
y="1"
fi
n="0"
fi
sleep 2
done;

```
:popcorn:
bye

---

### Post by mohwaqas12 on 2009-12-09
I did it . it combiled and is working. but how do i use it in any app.Do  i have to run smartcam app in background to make it work in messengers or will it load itself from /dev/video0

---

### Post by philpk on 2009-12-15
Hello
First, sorry for my english;)

Ubuntu 9.10 2.6.31-16
smartcam_1.4.0_i386.deb
smartcam-1.4.0.tar.gz

It can't compile smartcam.ko

I have installed 1.4deb and extract tar.gz in my download folder.
I connect my Nokia N82 to my pc via bluetooth and it works well:I can see the videocam from my phone in my pc.:)

The problem is that I want use in a third-party app and then I need smartcam.ko.

Here is copy of what it returns:
phil@phil-laptop:~/Téléchargements/smartcam-1.4.0/driver_src$ make -C /lib/modul
es/2.6.31-16-generic/build M=`pwd` modules
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.31-16-generic »
  CC [M]  /home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.o
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:563: warning: initialization from incompatible pointer type
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:599: error: ‘VID_TYPE_CAPTURE’ undeclared here (not in a function)
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:601: warning: initialization from incompatible pointer type
make[1]: *** [/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.o] Erreur 1
make: *** [_module_/home/phil/Téléchargements/smartcam-1.4.0/driver_src] Erreur 2
make: quittant le répertoire « /usr/src/linux-headers-2.6.31-16-generic »

Wher is the mistake ?](*,)

Thanks for your answer
Phil

---

### Post by philpk on 2009-12-15
OK
Problem  with the tuto of fatihsanli58 page3

Smartcam.ko is ok and work well with Skype.

Just one little problem: I have to type "sudo /sbin/insmod smartcam.ko" from smartcam folder everytime I boot ubuntu.

How to make this command automatic when ubuntu boots?

Thanks

---

### Post by philpk on 2009-12-15
Sorry, I forgot one important word::D
Problem **SOLVED** with the tuto of fatihsanli58 page3

---

### Post by alekokk on 2009-12-22
Hei

$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2009-12-22 19:59 /dev/video0

$ lsmod | grep smartcam
smartcam                6132  0 
videodev               36736  1 smartcam

$ smartcam
smartcam: registered DBUS service "org.gnome.smartcam"
Found smartcam device file: /dev/video0
smartcam: started comm thread
smartcam: port = 1




Smartcam do not show anything to me. I have nokia e65 and smartcam works ok there and im connected over BT
The only thing that shows the error, it would be like:

$ dmesg | grep smartcam
[17776.868439] smartcam[6815]: segfault at 14 ip 0804d1ea sp bfb3cd50 error 4 in smartcam[8048000+b000]
[18758.527377] smartcam[7112]: segfault at 14 ip 0804d1ea sp bfdd1670 error 4 in smartcam[8048000+b000]


i dont have any idea no more. 
Whats still wrong? :confused:

---

### Post by BM_Hackerman on 2009-12-25
Hi guys, I am a newbie in Linux and I can not understand the solutions you offer. I know some basic commands but nothing special. So is it possible anyone to rewrite the easiest way to make this nice app to work with skype ?
I have install the deb file and it works but nor skype nor amsn recognize the device.
Please Helpppppp!

---

### Post by sandy8925 on 2010-01-01
It works for me!!!! I'm using Karmic and an N70 and it works well. Thank you guys so much for telling us about the karmic patch. That's all I needed to compile and get smartcam.ko. Tried it with skype 2.1 beta and it works !!! You guys rock !!  Not to mention I only had to spend a few hours to do this.

---

### Post by sandy8925 on 2010-01-01
I forgot to mention I'm using smartcam 1.4 and the .sis file for the phone.

---

### Post by sandy8925 on 2010-01-01
Great it works with skype. So....does anyone know how to transmit audio as well ?

---

### Post by sandy8925 on 2010-01-01
@BM_Hackerman:

You have to compile and install the driver for it to work with skype,amsn etc. Follow the instructions given by fatihsanli58 in this thread. It's on page 3.

---

### Post by fatihsanli58 on 2010-01-19
hi to all
here is a dead end!!!
I got the same warning with FranJPR on the page 3 after doing a regular update. I try to re install the driver and the everything related to smartcam. Phone connects with Bluetooth but no image shown. here is the error message shown during the module installation:
[COLOR="Red"].../driver_src/smartcam.c:554: warning: initialization from incompatible pointer type 
.../driver_src/smartcam.c:555: warning: initialization from incompatible pointer type[/COLOR]

and I do not know what to do.....any HELP!!!!

---

### Post by Lanexbg on 2010-02-22
Hi there. I have a problem with smartcam. I did everything sayd in the tuto on page 3, but I could't see enything on my pc, there is /dev/video0, the phone is connected with BT, but the smartcam pc app doesn't show enything. Also, the phone is takeing pictures insted of video. And I can't use it with skype, cheese or camorama - 'no camera found ...'
I can't do wifi connection, the phone sayz the pc app is not started.

smartcam 1.4
kernel 2.6.31-20
nokia 5800

10x in advance

---

### Post by segalion on 2010-02-22
Anybody know how to compile for 2.6.33 (rc6)...

With the 2.6.31 patch give me this error...

```
/smartcam.c:529: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
```


Thanks in advance.

---

### Post by segalion on 2010-02-22
Solved!
You have to include 

#include <linux/sched.h>

over the 2.6.31 patch

---

### Post by Lanexbg on 2010-02-23
I solve my problem with a little bit more reading. I don't know why but I was useing the .jre file, now with the S603rdEd v1.4.sis file skype works, only camorama and cheese don't works

---

### Post by azhtar on 2010-03-16
How can I compile this for Lucid? I can't.

This is what I get

> azhtar@azhtar-laptop:~/Escritorio/smartcam/driver_src$ sudo make -C /lib/modules/`uname -r`/build M=`pwd`
make: se ingresa al directorio `/usr/src/linux-headers-2.6.32-16-generic'
  CC [M]  /home/azhtar/Escritorio/smartcam/driver_src/smartcam.o
/home/azhtar/Escritorio/smartcam/driver_src/smartcam.c:564: warning: initialization from incompatible pointer type
/home/azhtar/Escritorio/smartcam/driver_src/smartcam.c:600: error: &#8216;VID_TYPE_CAPTURE&#8217; undeclared here (not in a function)
/home/azhtar/Escritorio/smartcam/driver_src/smartcam.c:602: warning: initialization from incompatible pointer type
make[1]: *** [/home/azhtar/Escritorio/smartcam/driver_src/smartcam.o] Error 1
make: *** [_module_/home/azhtar/Escritorio/smartcam/driver_src] Error 2
make: se sale del directorio `/usr/src/linux-headers-2.6.32-16-generic'

---

### Post by greatboss on 2010-05-06
Hi

I am trying to compile the driver for kernel 2.6.32-21-generic on lucid.

I am using the karmic.patch file for this but the error I get is as below.

make: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.o
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c: In function ‘vidioc_s_fmt_cap’:
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:173: error: dereferencing pointer to incomplete type
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c: In function ‘smartcam_write’:
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:528: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:528: error: (Each undeclared identifier is reported only once
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:528: error: for each function it appears in.)
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c: At top level:
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:553: warning: initialization from incompatible pointer type
/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.c:554: warning: initialization from incompatible pointer type
make[1]: *** [/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src/smartcam.o] Error 1
make: *** [_module_/home/vidulajoshi/Desktop/smartcam-1.4.0/driver_src] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'

---

### Post by Volochanin on 2010-05-10
hi. What about ubuntu 10.04LTS? I failed to compile driver.

---

### Post by greatboss on 2010-05-10
I am also trying to install it on Ubuntu 10.04 LTS but no luck compiling it.

Experts, waiting for your advice.

---

### Post by kaustubhatzenith on 2010-05-11
Using 10.04 can''t compile:-



make: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /home/kaustubh/smartcam-1.4.0/driver_src/built-in.o
  CC [M]  /home/kaustubh/smartcam-1.4.0/driver_src/smartcam.o
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c: In function ‘vidioc_s_fmt_cap’:
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:174: error: dereferencing pointer to incomplete type
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c: In function ‘smartcam_write’:
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:529: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:529: error: (Each undeclared identifier is reported only once
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:529: error: for each function it appears in.)
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c: At top level:
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:554: warning: initialization from incompatible pointer type
/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.c:555: warning: initialization from incompatible pointer type
make[1]: *** [/home/kaustubh/smartcam-1.4.0/driver_src/smartcam.o] Error 1
make: *** [_module_/home/kaustubh/smartcam-1.4.0/driver_src] Error 2



PLz Help

---

### Post by ashwin.venkat on 2010-05-15
got it working in Ubuntu 10.04 !!!!! Thank you!
most of the instruction was from fatihsanli58  in  page 3 , after patching smartcam.c I followed instruction by  segalion in page no 5  i.e added this line " #include <linux/sched.h>  in patched smartcam.c , after doing this the file compiled with out any errors :)  then again follow instruction from fatihsanli58.

started the application in this order :
Before running smartcam, the driver must be loaded in the kernel; if not the PC application is 
pretty much useless. To load the driver, open a shell as root in src/driver path and type:

    /sbin/modprobe videodev
    /sbin/insmod smartcam.ko

After this start the application on the PC, start the phone application and connect it to your PC.
You should now see video images on the PC application window
Source : [http://forum.ubuntu-it.org/index.php?topic=262984.msg2145165](http://forum.ubuntu-it.org/index.php?topic=262984.msg2145165)

---

### Post by greatboss on 2010-05-15
Hi Ashwin

Can you list down the exact steps that you did and the files that you used to get this working under 10.04. 

Also what I am not clear is what to install on the cellphone. 

Would be a great help.

Regards
greatboss

---

### Post by Lanexbg on 2010-05-15
This is it:
in smartcam.c add #include <linux/sched.h> in the beging with the other includes
and use the 'manual' at page 3

I just did this and smartcam is again working

Thanks ashwin.venkat for this trck (and the others ofcourse)

---

### Post by ashwin.venkat on 2010-05-20
Hi Greatboss :)

1. you must install a .sis file , i have a nokia N95 so i used this [file ]("http://sourceforge.net/projects/smartcam/files/smartcam_symbian/SmartCamS60_v1_4/SmartCamS603rdEd_v1_4.sis/download").
    If you are using another version then go to [download ]("http://sourceforge.net/projects/smartcam/files/")page and download a mobile version that fits your    phone.
2. You install the Linux PC application,so for Ubuntu its [this.]("http://sourceforge.net/projects/smartcam/files/smartcam_linux/smartcam_linux_v_1.4.0/smartcam_1.4.0_i386.deb/download")
3. the steps in page 3 should be followed now.
Hope it helps.

P.S : need some help to make it load at boot :( i have to do it manually :( and always copy smartcam.ko

---

### Post by dineon on 2010-05-22
Hi all, I found this package for Lucid : [https://launchpad.net/~mgorven/+archive/ppa/+builds?build_state=built](https://launchpad.net/~mgorven/+archive/ppa/+builds?build_state=built)

No loading driver problem, works well with amsn.
Just tested, didn't try with other IM.

Hope it'll help.

---

### Post by ashwin.venkat on 2010-05-22
Thank you so much [dineon]("http://ubuntuforums.org/member.php?u=1070149") :) It worked for me too :)
I dont have to load driver everytime :) so much easy :)
t:popcorn:

---

### Post by cyril.andrieu on 2010-05-26
I confirm, works for me too with Ubuntu 10.04 and nokia 6210 navigator ....
THANKS !!!!!

---

### Post by fatihsanli58 on 2010-06-14
yes it works but if you have an intel based graphic card (such as i855gm) X will crash when you try to use smartcam with skype. any solution?????:(

---

### Post by Sal Z on 2010-10-15
Sorry if i'm necroing this thread, but under ubuntu 10.10 the module smartcam.ko gives the following error message:


```
insmod: error inserting './smartcam.ko': -1 Unknown symbol in module
```

while dmesg output the following error:


```
[  102.751430] smartcam: Unknown symbol video_ioctl2 (err 0)
[  102.751729] smartcam: Unknown symbol video_unregister_device (err 0)
[  102.751900] smartcam: Unknown symbol video_register_device (err 0)
[  102.752106] smartcam: Unknown symbol video_device_release_empty (err 0)
```

any suggestion?

---

### Post by shunmugachamy on 2010-10-18
I tried with that (2.6.32) SmartCam package It is installed successfully.
Camera also says connected status. but i am not receiving the video on the PC Screen .i need help ...

I am getting like this..

smartcam: registered DBUS service "org.gnome.smartcam"
Found smartcam device file: /dev/video0
smartcam: started comm thread
smartcam: port = 1
sdp_connect: sdp cannot connect No such file or directory

---

### Post by ixkuklin on 2010-11-23
> **philpk said:**
> Hello
First, sorry for my english;)

Ubuntu 9.10 2.6.31-16
smartcam_1.4.0_i386.deb
smartcam-1.4.0.tar.gz

It can't compile smartcam.ko

I have installed 1.4deb and extract tar.gz in my download folder.
I connect my Nokia N82 to my pc via bluetooth and it works well:I can see the videocam from my phone in my pc.:)

The problem is that I want use in a third-party app and then I need smartcam.ko.

Here is copy of what it returns:
phil@phil-laptop:~/Téléchargements/smartcam-1.4.0/driver_src$ make -C /lib/modul
es/2.6.31-16-generic/build M=`pwd` modules
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.31-16-generic »
  CC [M]  /home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.o
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:563: warning: initialization from incompatible pointer type
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:599: error: ‘VID_TYPE_CAPTURE’ undeclared here (not in a function)
/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.c:601: warning: initialization from incompatible pointer type
make[1]: *** [/home/phil/Téléchargements/smartcam-1.4.0/driver_src/smartcam.o] Erreur 1
make: *** [_module_/home/phil/Téléchargements/smartcam-1.4.0/driver_src] Erreur 2
make: quittant le répertoire « /usr/src/linux-headers-2.6.31-16-generic »

Wher is the mistake ?](*,)

Thanks for your answer
Phil



I have exactly the same problem, but didn't catch how philpk solved it. Can anyone explain me please?

---

### Post by javad.safaie on 2010-12-06
Hi
dear sirs
i am beginner on ubuntu 
i tried to compile smartcam-1.4.0, but it does not work (sudo make -C/lib/modules/`uname -r`/build M=`pwd`)
i also tried with patch before compiling (patch -p0 <karmic.patch smartcam.c) with same result
my kernel version is 2.6.35.23
thanks alot for you attention

---

### Post by javad.safaie on 2010-12-25
Hi
Dear all
i can solve my problem
i think this problem(i explained it before) happen because smartcam software has 32bit structure but my PC has 64bit architecture,
so by forcing the smartcam_1.4.0_i386.deb file (sudo dpkg -i --force -all ) to install, my problem has solved
and it work realy nice with my nokia N95 8G

---

### Post by luctor on 2010-12-30
YES ! got it working thanks to the karmic.patch and #include <linux/sched.h>

see proof here. not very usefull, just me jumping with joy in my work room :-p

[http://bambuser.com/channel/rghvdberg/broadcast/1292845](http://bambuser.com/channel/rghvdberg/broadcast/1292845)

ubuntu 10.10 amd64
 2.6.35-24-generic #42-Ubuntu SMP

---

### Post by luctor on 2010-12-30
mmm I should really add this to my ppa ...

---

### Post by fchiyenda on 2011-01-03
:confused: Can someone please help me on how to get smartcam running on ubuntu 10.04 2.6.35-22-generic kernel

Thanks in advance.

---

### Post by l0xin on 2011-02-02
The easiest way it to get [Y PPA Manager](http://www.webupd8.org/2011/01/y-ppa-manager-004-released-with-new.html), search for "smartcam" and the first PPA that comes up has smartcam and smartcam-driver packages, which work flawlessly on Maverick with the latest kernel.

---

### Post by nuunkotad on 2011-03-08
hello.
works fine on my nokia N82 + Lucid :smile:
1. [https://launchpad.net/~mgorven/+archive/ppa/+builds?build_text=smartcam&build_state=built]("https://launchpad.net/%7Emgorven/+archive/ppa/+builds?build_text=smartcam&build_state=built") (latest available smartcam build)
2.[http://sourceforge.net/projects/smartcam/files/smartcam_symbian/](http://sourceforge.net/projects/smartcam/files/smartcam_symbian/) (latest .sisx build)
3.install on phone and PC
4.launch on PC and in phone 
5.make correct setting in phone app (connection type, front/rear camera etc.)
6.in phone app press connect

---

### Post by killerloop8 on 2011-04-29
> **nuunkotad said:**
> hello.
works fine on my nokia N82 + Lucid :smile:
1. [https://launchpad.net/~mgorven/+archive/ppa/+builds?build_text=smartcam&build_state=built]("https://launchpad.net/%7Emgorven/+archive/ppa/+builds?build_text=smartcam&build_state=built") (latest available smartcam build)
2.[http://sourceforge.net/projects/smartcam/files/smartcam_symbian/](http://sourceforge.net/projects/smartcam/files/smartcam_symbian/) (latest .sisx build)
3.install on phone and PC
4.launch on PC and in phone 
5.make correct setting in phone app (connection type, front/rear camera etc.)
6.in phone app press connect
Thanks for the link mate... was doin all messy work guide(1st page of this thread) which i'm not familiar with but for no use... thanks for the noob friendly package

---

### Post by gyvermac on 2011-05-02
I installed Smartcam and works well on amsn... but it doesn't work with Skype (the small screen appears black). Any ideas?

---

### Post by kapusa176 on 2011-05-06
hi, can anyone help me i tried installing smartcam on ubuntu 11.04 but I can't compile the driver I hope someone could help me with this one...



make: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /smartcam-1.4.0/driver_src/smartcam.o
/smartcam-1.4.0/driver_src/smartcam.c: In function ‘vidioc_s_fmt_cap’:
/smartcam-1.4.0/driver_src/smartcam.c:174:9: error: dereferencing pointer to incomplete type
/smartcam-1.4.0/driver_src/smartcam.c: In function ‘smartcam_write’:
/smartcam-1.4.0/driver_src/smartcam.c:529:2: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/smartcam-1.4.0/driver_src/smartcam.c:529:2: note: each undeclared identifier is reported only once for each function it appears in
/smartcam-1.4.0/driver_src/smartcam.c: At top level:
/smartcam-1.4.0/driver_src/smartcam.c:554:2: warning: initialization from incompatible pointer type
/smartcam-1.4.0/driver_src/smartcam.c:555:2: warning: initialization from incompatible pointer type
make[1]: *** [/smartcam-1.4.0/driver_src/smartcam.o] Error 1
make: *** [_module_/smartcam-1.4.0/driver_src] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'

---

### Post by sandy8925 on 2011-05-07
looks like an error in the code. isn't there a precompiled .deb file?

---

### Post by Trav0 on 2011-05-14
just compiled the driver on 10.04

applied the karmicpatch.zip file by putting it in the driver dir
and typing

patch -p0 < karmic.patch smartcam.c

then added 

#include <linux/sched.h> 

to smartcam.c and it compiled no problems.

Running the program ends in a segmentation fault and my guess is its because the bluetooth in my laptop has stopped working does anyone know how to compile without bluetooth??

---

### Post by ccunarro on 2011-06-12
> **shunmugachamy said:**
> I tried with that (2.6.32) SmartCam package It is installed successfully.
Camera also says connected status. but i am not receiving the video on the PC Screen .i need help ...

I am getting like this..

smartcam: registered DBUS service "org.gnome.smartcam"
Found smartcam device file: /dev/video0
smartcam: started comm thread
smartcam: port = 1


i am having the same problem running under debian squeeze 64 bit and nokia n97.

On the phone it says connected, but no image on pc screen

Could anyone resolve it?

---

### Post by mmzq on 2011-08-13
can anyone please help with compiling drivers for natty? searched all over the web, tried a whole lot of solutions, but all of em -- straight down the hole.](*,)

i'm a  noob :(, and step-by step instructions would be highly appreciated.

thanks!

kernel ver: 2.6.38-10

---

### Post by almourasel on 2011-10-22
Can anyone helps me pls , i tried all steps from the begining and still don't work .

tarek@tarek-laptop:~/Téléchargements/smartcam/smartcam-1.4.0/driver_src$ sudo make -C /lib/modules/`uname -r`/build M=`pwd`
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.32-34-generic »
  LD      /home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/built-in.o
  CC [M]  /home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.o
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c: In function &#8216;vidioc_s_fmt_cap&#8217;:
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:175: error: dereferencing pointer to incomplete type
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c: In function &#8216;smartcam_write&#8217;:
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:530: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:530: error: (Each undeclared identifier is reported only once
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:530: error: for each function it appears in.)
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c: At top level:
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:555: warning: initialization from incompatible pointer type
/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.c:556: warning: initialization from incompatible pointer type
make[1]: *** [/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src/smartcam.o] Erreur 1
make: *** [_module_/home/tarek/Téléchargements/smartcam/smartcam-1.4.0/driver_src] Erreur 2
make: quittant le répertoire « /usr/src/linux-headers-2.6.32-34-generic »
tarek@tarek-laptop:~/Téléchargements/smartcam/smartcam-1.4.0/driver_src$ 


Kernel generic  2.6.32-34.

PLease share all steps one by one because i am new in linux domain.

---

### Post by amanita on 2012-01-01
Hello there, 

I would like to share my troubles with you, perhaps someone could help me to get it running again. I installed Smartcam 1.4.0 lucid package and got it working with Skype. 

However, after reboot, I am able to see a picture from my cam (Nokia C05-3) in Smartcam application window but no longer I am able to select device in my Skype Video devices. 

Also, when I start Smartcam application I receive following error:

"Could not find Smartcam device file."
"Please load (insmod) the driver and chmod 666 /dev/videoX"

Here is the output from shell:

```
smartcam: registered DBUS service "org.gnome.smartcam"
Cannot identify '/dev/video0': 2, No such file or directory
Cannot identify '/dev/video1': 2, No such file or directory
Cannot identify '/dev/video2': 2, No such file or directory
Cannot identify '/dev/video3': 2, No such file or directory
Cannot identify '/dev/video4': 2, No such file or directory
Cannot identify '/dev/video5': 2, No such file or directory
Cannot identify '/dev/video6': 2, No such file or directory
Cannot identify '/dev/video7': 2, No such file or directory
Cannot identify '/dev/video8': 2, No such file or directory
Cannot identify '/dev/video9': 2, No such file or directory
smartcam: started comm thread

```

I tried reinstall Smartcam, Skype and it did not helped. Then I upgraded to Lucid 2.6.32-37 install Smartcam and again after reboot the same...

Any ideas how to fix it? Thanks.

---

### Post by amanita on 2012-01-01
OK now, I finally got it. I had to load driver manually ```
modprobe smartcam
``` and downgrade Skype versions from 2.2.0.35 (only black screen) to 2.1.0.47 version.

Here are steps to replicate:

1.Download and install package smartcam_1.4.0-0ubuntu2~lucid1_i386.deb

2. When you get this annoying message (usually after computer restart):

> "Could not find Smartcam device file."
"Please load (insmod) the driver and chmod 666 /dev/videoX"

then

```
sudo gedit /etc/modules
``` add at the end of the file.```
smartcam
``` 

3. Install Skype 2.1.0.47 (any version later than 2.1.0.47 seems to be bugged)

```
wget -O skype-ubuntu-current_i386.deb http://download.skype.com/linux/skype-debian_2.1.0.47-1_i386.deb
sudo dpkg -i skype-ubuntu-current_i386.deb
sudo rm skype-ubuntu-current_i386.deb

```

4. Install app. to you mobile 

5. Restart computer

6. Run smartcam app, connect it with your phone and then run Skype.

PS You can also run video tests ```
gstreamer-properties
``` and see if it is working (don't rely on skype video devices test only).









> **amanita said:**
> Hello there, 

I would like to share my troubles with you, perhaps someone could help me to get it running again. I installed Smartcam 1.4.0 lucid package and got it working with Skype. 

However, after reboot, I am able to see a picture from my cam (Nokia C05-3) in Smartcam application window but no longer I am able to select device in my Skype Video devices. 

Also, when I start Smartcam application I receive following error:

"Could not find Smartcam device file."
"Please load (insmod) the driver and chmod 666 /dev/videoX"

Here is the output from shell:

```
smartcam: registered DBUS service "org.gnome.smartcam"
Cannot identify '/dev/video0': 2, No such file or directory
Cannot identify '/dev/video1': 2, No such file or directory
Cannot identify '/dev/video2': 2, No such file or directory
Cannot identify '/dev/video3': 2, No such file or directory
Cannot identify '/dev/video4': 2, No such file or directory
Cannot identify '/dev/video5': 2, No such file or directory
Cannot identify '/dev/video6': 2, No such file or directory
Cannot identify '/dev/video7': 2, No such file or directory
Cannot identify '/dev/video8': 2, No such file or directory
Cannot identify '/dev/video9': 2, No such file or directory
smartcam: started comm thread

```

I tried reinstall Smartcam, Skype and it did not helped. Then I upgraded to Lucid 2.6.32-37 install Smartcam and again after reboot the same...

Any ideas how to fix it? Thanks.

---

### Post by amanita on 2012-01-01
You don't have to compile just get build package smartcam_1.4.0-0ubuntu2~lucid1_i386.deb from ```
https://launchpad.net/~mgorven/+archive/ppa/+build/1711255
```

Then it is straightforward.

---

### Post by dansanti on 2012-05-31
just uncoment line 28 ```
//#include <linux/module.h>   

``` on driver_src/smartcam.c
and compile again, after insert the driver smartcam.ko. this work for me.
[http://probandoubuntu.blogspot.com/2012/05/smartcam-usando-tu-movil-como-camara.html]("http://probandoubuntu.blogspot.com/2012/05/smartcam-usando-tu-movil-como-camara.html")

Spanish**

---

### Post by hamletscatrex on 2013-02-12
Hy guys, I am new here. I am using ubuntu 11.04, I can not connect my nokia 5530 to smartcam via tcp/ip (wifi) it says: could not connect, request timed out , and when i try to connect via bluetooth it says: Disconnected -18. Please help!
Thanks.

---

