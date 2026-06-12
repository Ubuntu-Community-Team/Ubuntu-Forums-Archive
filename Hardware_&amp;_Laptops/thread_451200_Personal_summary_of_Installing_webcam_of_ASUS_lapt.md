---
title: "Personal summary of Installing webcam of ASUS laptop"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by chunchengch on 2007-05-22
I finally successfully install the **Syntek Semicon DC-1125** driver and enable the webcam of my **ASUS F3Jc** laptop in the Ubuntustudio, and I suppose it should be also available for other models of ASUS laptops, [COLOR="Red"]however there is still a problem needs to be solved, that is the image is **black-and-white**[/COLOR],  if anyone knows how to set it to be colored, please post it here, thanks a lot!


**1.Update the library of hardwares PCI and USB:**
       $ sudo update-pciids
       $ sudo update-usbids

**2.Make sure your ASUS laptop has really one webcam syntek?**
         $ lsusb 
         Bus 005 Device 003: ID 05e1:0501 **[COLOR="Red"]Syntek[/COLOR]** Semiconductor Co., Ltd 
         Bus 005 Device 001: ID 0000:0000  
         Bus 002 Device 003: ID 046d:c019 Logitech, Inc. 
         Bus 002 Device 001: ID 0000:0000  
         Bus 001 Device 001: ID 0000:0000  
         Bus 003 Device 001: ID 0000:0000  
         Bus 004 Device 001: ID 0000:0000  
         $ 

**3.Install some dependences:**
       $ sudo apt-get install bin86
       $ sudo apt-get install libqt3-headers
       $ sudo apt-get install libqt3-mt-dev
       $ sudo apt-get install libncurses5-dev
       $ sudo apt-get install libusb-dev
       $ sudo apt-get install libsane-dev
       $ sudo apt-get install libsane-extras-dev
       $ sudo apt-get install exuberant-ctags
       $ sudo apt-get install camorama
       $ sudo apt-get install subversion

       (all these packages could be installed in Synaptic)

**4.Download the sources and compile it:**
       $ cd ~
       $ svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver)
       $ cd syntekdriver/trunk/driver
       $ make
       $ sudo modprobe videodev
       $ sudo modprobe v4l1-compat
       $ sudo insmod stk11xx.ko

**5.Press ALT+F2 and executes ‘gksu gedit /etc/modules’ then adds the lines:**
       # modules for infrastructure to support the video
       videodev
       v4l1-compat

**6.Press ALT+F2 and executes ‘gksu gedit /etc/rc.local’ then adds the following line:**
       insmod /home/<YourloginName>/syntekdriver/trunk/driver/stk11xx.ko    
       ([COLOR="Red"]this line must be added before last line “ exit 0 ”[/COLOR])

**7. Reboot and then open [B]Camorama** to check if the webcam works.[/B]
       Applications > Art or something? (&#32654;&#24037;&#32362;&#22294;) > Camorama
       ( I use Chinese Ubuntustudio, so please check the path yourself)

---

### Post by chunchengch on 2007-05-22
It is odd, I typed the address "[COLOR="Red"]**syntekdriver.svn.sourceforge.net/svnroot/syntekdriver**[/COLOR]" in the thread, while the forum system automatically transfered it to be "**syntekdriver.svn.sourceforge...t/syntekdriver**", and this will cause problem while downloading driver. please modify it yourself, thanks!

I can not type http:// before the address, otherwise the address will be shortened by forum system, I suppose.

---

### Post by Xephrey on 2007-05-24
Okay, it was alright until I got to  

$ svn co [https://syntekdriver.svn.sourceforge...t/syntekdriver](https://syntekdriver.svn.sourceforge...t/syntekdriver)

then I got svn: Client error in parsing arguments


Help? I have an ASUS FJ3m

---

### Post by chunchengch on 2007-05-24
Xephrey,

Please read the reply #2, you may find the correct web site address.

---

### Post by Xephrey on 2007-05-24
Oh I see...   alright. 

Well, I was able to get through all those steps, and my cam is displaying Blue only. and when I run camorama it still says 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

in the terminal followed by a:
"Could not connect to video device (dev/video0)
Please check connection"

Suggestions?

Thanks.

---

### Post by chunchengch on 2007-05-25
5.Press ALT+F2 and executes ‘gksu gedit /etc/modules’ then adds the lines:
# modules for infrastructure to support the video
videodev
v4l1-compat

6.Press ALT+F2 and executes ‘gksu gedit /etc/rc.local’ then adds the following line:
insmod /home/<YourloginName>/syntekdriver/trunk/driver/stk11xx.ko
(this line must be added before last line “ exit 0 ”)

---

### Post by Xephrey on 2007-05-25
okay, not its coming up and functioning, but its flashing on and off... I'm so close to having it actually function! 

What can I do to stop it from flashing on and off like crazy?

---

### Post by jefe on 2007-07-10
Hi, same problem here. I'm using Feisty on Asus F5R laptop, I've done exactly as written above but still got message that there isn't any /dev/video0. Any solution, please?

---

### Post by Alexander_Corvinus on 2007-07-31
same problem here 
"could not connect to video device (dev/video0) please check connection"

Asus A7M (using feisty)

---

### Post by jefe on 2007-08-22
Try the newest version, maybe it s will work now.

---

### Post by canceLinux on 2007-09-11
is there anybody have "already complied stk***.ko"

please send it here.. for ubuntu x86 feisty :)

---

### Post by rmalleman on 2007-09-12
I compiled everything but now my image shows up upside down in camorama.  Is anyone else having this problem

---

### Post by inzaneg on 2007-09-22
hi. thanks for this guide :) worked great

I to have black and white and mirror image. I added the color correction and mirror filter in camorama to fix it. You have to add the filters each time you start the program though

---

### Post by Ev1L on 2007-10-18
> **rmalleman said:**
> I compiled everything but now my image shows up upside down in camorama.  Is anyone else having this problem

here's the solution ;)

[http://sourceforge.net/forum/forum.php?thread_id=1787770&forum_id=616183](http://sourceforge.net/forum/forum.php?thread_id=1787770&forum_id=616183)

---

### Post by 0graham0 on 2007-10-22
Thank you...these instructions worked great for me on an Asus F3Sv, with a few tweaks:

The color is a little strange, but it is in color, and the orientation i correct.

I followed instructions #1-#3, and then instead of instruction #4-#6 I followed this process:

4. I downloaded the driver at [http://sourceforge.net/project/showfiles.php?group_id=178178](http://sourceforge.net/project/showfiles.php?group_id=178178) , expanded the archive on the desktop and renamed the folder from "stk11xx-1.1.0" to "camdriver". I then opened the terminal and ran:
```
cd Desktop
sudo mv camdriver /etc/
cd /etc/camdriver
sudo make
sudo modprobe videodev
sudo modprobe v4l1-compat
sudo insmod stk11xx.ko
```

5.Press ALT+F2 and execute ‘gksu gedit /etc/modules’ then add the lines and save:
# modules for infrastructure to support the video
videodev
v4l1-compat

6.Press ALT+F2 and execute ‘gksu gedit /etc/rc.local’ then add the following line:
insmod /etc/camdriver/stk11xx.ko
(this line must be added before last line “ exit 0 ”)

7. Reboot and then open Camorama (Applications -> Graphics -> Camorama

---

### Post by Bunro on 2007-10-29
I reached until the point to give the make command but I am getting the following answer:
 robert@notebook:~$ cd syntekdriver/trunk/driver 
 robert@notebook:~/syntekdriver/trunk/driver$ ls 
 doxygen.cfg  Makefile.standalone  stk11xx-buf.c  stk11xx-sysfs.c  stk11xx-v4l.c 
 Kbuild       README               stk11xx-dev.c  stk11xx.txt 
 Makefile     stk11xx-bayer.c      stk11xx.h      stk11xx-usb.c 
 robert@notebook:~/syntekdriver/trunk/driver$ make 
 make: *** No targets.  Stop. 
 robert@notebook:~/syntekdriver/trunk/driver$  
 robert@notebook:~/syntekdriver/trunk/driver$  
 

 I now this is a very basic question but I am stuck here hopefully there is some one who can help me out here?
 Regards, Robert

---

### Post by linuxmangr on 2007-12-28
Hi , I have not Asus but the same cam on my no name Laptop , Syntek USB2.0 Camera
I follow this guide 
[http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=1]("http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=1")

After I add some some coomands from this post [http://ubuntuforums.org/showpost.php?p=2699093&postcount=1]("http://ubuntuforums.org/showpost.php?p=2699093&postcount=1")

and Cam is work , with the sudo modprobe stk11xx vflip=1  Image is ok , but when PC start up I have some errors and can't find what's wrong , if some one have the same in dmesg when cam start up or when pc start up and find what is wrong ? 
This is errors :
> [ 2705.520000] stk11xx: Syntek USB2.0 Camera release resources video device /dev/video0
[ 2712.660000] stk11xx: Syntek USB2.0 webcam driver startup
[ 2712.660000] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[ 2712.660000] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A51.
[ 2712.660000] stk11xx: Release: 0005
[ 2712.660000] stk11xx: Number of interfaces : 1
[ 2712.660000] stk11xx: Initialize USB2.0 Syntek Camera
[ 2712.912000] stk11xx: Check device return error (0x0201 = 51) !
[ 2712.916000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.924000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.928000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.932000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.932000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.932000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.936000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.936000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.936000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.940000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.944000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.944000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.944000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.948000] stk11xx: Check device return error (0x0201 = 51) !
[ 2712.952000] stk11xx: Check device return error (0x0201 = 51) !
[ 2712.956000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.956000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.956000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.960000] stk11xx: Check device return error (0x0201 = 51) !
[ 2712.964000] stk11xx: Check device return error (0x0201 = 91) !
[ 2712.968000] stk11xx: Check device return error (0x0201 = 51) !
[ 2712.976000] stk11xx: Check device return error (0x0201 = 91) !
[ 2712.980000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.980000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.980000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.984000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.984000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.984000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.988000] stk11xx: Check device return error (0x0201 = 91) !
[ 2712.988000] stk11xx: Check device return error (0x0201 = 31) !
[ 2712.992000] stk11xx: Check device return error (0x0201 = 11) !
[ 2712.996000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.000000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.000000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.004000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.012000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.012000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.016000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.020000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.020000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.032000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.036000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.036000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.040000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.044000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.048000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.052000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.056000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.064000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.064000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.068000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.080000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.080000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.088000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.092000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.096000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.104000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.108000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.112000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.120000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.120000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.124000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.132000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.140000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.144000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.148000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.152000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.160000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.164000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.164000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.168000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.172000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.176000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.176000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.180000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.180000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.184000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.188000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.192000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.200000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.200000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.204000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.204000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.212000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.216000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.220000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.224000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.228000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.232000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.232000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.236000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.240000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.244000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.244000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.244000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.248000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.248000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.252000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.256000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.256000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.256000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.264000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.272000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.276000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.280000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.280000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.284000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.284000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.288000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.292000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.292000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.296000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.296000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.296000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.300000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.308000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.312000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.324000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.324000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.324000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.328000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.332000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.336000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.344000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.344000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.348000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.352000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.356000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.364000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.372000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.372000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.380000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.384000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.388000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.392000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.392000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.396000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.396000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.400000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.404000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.412000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.424000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.428000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.428000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.432000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.432000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.436000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.440000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.440000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.444000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.444000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.448000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.448000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.460000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.464000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.464000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.472000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.472000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.480000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.480000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.484000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.488000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.492000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.496000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.500000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.504000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.508000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.516000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.520000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.524000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.528000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.532000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.532000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.536000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.540000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.544000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.548000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.548000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.552000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.556000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.556000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.560000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.560000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.560000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.560000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.564000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.568000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.568000] stk11xx: Check device return error (0x0201 = 91) !
[ 2713.572000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.572000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.576000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.580000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.584000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.588000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.592000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.592000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.600000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.604000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.608000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.608000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.616000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.620000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.624000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.624000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.624000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.632000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.636000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.640000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.640000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.644000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.652000] stk11xx: Check device return error (0x0201 = 51) !
[ 2713.656000] stk11xx: Check device return error (0x0201 = 31) !
[ 2713.656000] stk11xx: Check device return error (0x0201 = 11) !
[ 2713.660000] stk11xx: Syntek USB2.0 Camera is ready
[ 2713.660000] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[ 2713.660000] usbcore: registered new interface driver usb_stk11xx_driver
[ 2713.660000] stk11xx: v1.3.0 : Syntek USB Video Camera
This is show when i try to run this commands :
sudo rmmod stk11xx  and after :
sudo modprobe stk11xx vflip=1
Thanks if some one have the solution .
Happy New Year .

---

### Post by madc0wpl on 2008-01-14
i also can't compile the drivers. (no objects) anyone can send me the .deb? :(
or mb i have the other cam cause in lsusb i get
```

Bus 006 Device 002: ID 174f:6a33  
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 0000:0000  

```

---

### Post by Tuxor on 2008-01-16
> **Bunro said:**
> I reached until the point to give the make command but I am getting the following answer:
 robert@notebook:~$ cd syntekdriver/trunk/driver 
 robert@notebook:~/syntekdriver/trunk/driver$ ls 
 doxygen.cfg  Makefile.standalone  stk11xx-buf.c  stk11xx-sysfs.c  stk11xx-v4l.c 
 Kbuild       README               stk11xx-dev.c  stk11xx.txt 
 Makefile     stk11xx-bayer.c      stk11xx.h      stk11xx-usb.c 
 robert@notebook:~/syntekdriver/trunk/driver$ make 
 make: *** No targets.  Stop. 
 robert@notebook:~/syntekdriver/trunk/driver$  
 robert@notebook:~/syntekdriver/trunk/driver$  
 

 I now this is a very basic question but I am stuck here hopefully there is some one who can help me out here?
 Regards, Robert

Same for me. I tried *make -f Makefile.standalone* and that did it.

---

### Post by knocz on 2008-01-25
I still get Could not connect to video device (/dev/video0).

Does anybody have ideas?

---

### Post by Sheogorath on 2008-03-03
i got the same message: could not connect to video device (/dev/video0). please check connection
i have Gutsy on Asus G1

---

### Post by Sheogorath on 2008-03-03
thanks for the link econlab it works for me, no errors after reboot
link:[http://www.geekplanet.fr/index.php?o...id=25&Itemid=1](http://www.geekplanet.fr/index.php?o...id=25&Itemid=1)
:guitar:

---

### Post by linuxmangr on 2008-03-04
Welcome but on my PC-Laptop I think is the same cam but not work without errors .

---

### Post by Elderlygent on 2008-03-17
This works fine until I get the following prompt:

david@david-laptop:~/syntekdriver/trunk/driver$ make
make: *** No targets.  Stop.

Any ideas anyone?

Cheers

---

### Post by Elderlygent on 2008-03-17
This works fine until I get the prompt:

david@david-laptop:~/syntekdriver/trunk/driver$ make
make: *** No targets.  Stop.

Any ideas, anyone?

Cheers

---

### Post by Elderlygent on 2008-03-19
Those who have Asus A7C series laptops might like to go to Ubuntu-es (Spain) and then search for Asus7CC. There are complete installation instructions for Gutsy including the webcam. You don't really need Spanish to understand the instructions.Just one point: you have to remember to reboot at the end of the process.

---

### Post by Mouth on 2008-04-27
WebCam works out-of-the-box for me with Hardy 64bit fresh install and Camorama

---

