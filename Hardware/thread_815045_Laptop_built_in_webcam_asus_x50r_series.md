---
title: "Laptop built in webcam asus x50r series"
date: 2008-06-01
forum: Hardware
---

### Post by inspectorgecko on 2008-06-01
basically installed ubuntu couple of days ago over vista and v impressed and happy to stick with it however the only problem i have is getting the interrogated webcam to work, any help would be apprieciated 

ryan

---

### Post by linuxwizard on 2008-06-01
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by hotweiss on 2008-06-01
I also have an Asus notebook, this is how I got my webcam working:

A) First we’ll need to install the files needed to build the driver by typing the following in Terminal:
> sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
> cd /usr/src
and then
> sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
> cd trunk
and then
> sudo make
and then
> sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.

---

### Post by inspectorgecko on 2008-06-01
rite i tried the advice and methods given but not much has happened really, so where do i go next, hoping to hear soon 

ryan@ryan-laptop:~$ lsusb
Bus 006 Device 003: ID 0c45:624f Microdia 
Bus 006 Device 002: ID 0bda:0116 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ryan@ryan-laptop:~$

---

### Post by linuxwizard on 2008-06-01
For Microdia webcams this is the driver you need > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

Bus 006 Device 003: ID 0c45:624f Microdia

---

### Post by inspectorgecko on 2008-06-02
right well i tried to install both the packages but i got errors claiming they were's supported, so i'm back at square one really, any other suggestions or a walkthrough to do it manually would be nice

---

### Post by hotweiss on 2008-06-02
> **inspectorgecko said:**
> right well i tried to install both the packages but i got errors claiming they were's supported, so i'm back at square one really, any other suggestions or a walkthrough to do it manually would be nice

I don't know what to tell you at this point. Try Linux Mint, it is based on Ubuntu. It has a lot of improvements and some functionality that Ubuntu does not provide out of the box. For example, my webcam worked out of the box with Mint.

[http://linuxmint.com/](http://linuxmint.com/)

---

### Post by linuxwizard on 2008-06-02
inspectorgecko

After you installed the driver package did you reboot your computer ? Than try using Ekiga again work with the settings.

---

### Post by intel on 2008-06-03
LinuxWizard: kindly ask 0c45:xxxx to inquire for support here
                    http://groups.google.com/group/microdia/

inspectorgecko: 0c45:624f is supported by Microdia webcma kernel driver
                       check here http://groups.google.com/group/microdia/

and stop suggesting linux-projects.org for 0c45:xxxx webcams using sn9c20x chips.

---

### Post by linuxwizard on 2008-06-03
intel
I don't use or have a Microdia webcam. I suggest the linux-projects.org because it does work for people that are in need of a driver for their webcams. I have seen comments on >  [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) > that it is a joke and a waste of time and no help. I have not been to that website. I have no reason to so I will suggest what I know that has worked for others in the past.

---

### Post by vixmusic01 on 2008-06-04
Hi All,
I have a built in webcam on an A8M Asus notebook.

It doesn't work.

Camorama says "Could not connect to video device (dev/video/0)

Etiga and Camera Monitor have similar results.

My config is a bit different,

victoria@u-live:~$ lsusb
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. USB 2.0 Webcam
Bus 001 Device 001: ID 0000:0000  

I tried one of the fixes, but got to the connection part and was refused.Partial quote from terminal.

Setting up linux-headers-2.6.24-18-rt (2.6.24-18.32) ...
Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu5) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
victoria@u-live:~$ cd /usr/src 
victoria@u-live:/usr/src$ sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk 
svn: Can't connect to host 'svn.berlios.de': Connection refused
victoria@u-live:/usr/src$ sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk 
svn: Can't connect to host 'svn.berlios.de': Connection refused

Any thoughts?

Victoria

---

### Post by linuxwizard on 2008-06-04
vixmusic01
First off you are trying to install the wrong driver for your webcam. This is your cam > Bus 001 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. USB 2.0 Webcam > listed here > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > this is the driver you need > [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Your cam is not listed for the driver your are installing > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/).

---

### Post by steveneddy on 2008-06-04
> **linuxwizard said:**
> intel
I don't use or have a Microdia webcam. I suggest the linux-projects.org because it does work for people that are in need of a driver for their webcams. I have seen comments on >  [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) > that it is a joke and a waste of time and no help. I have not been to that website. I have no reason to so I will suggest what I know that has worked for others in the past.

I have the Microdia web cam in my laptop and I used the driver from 

[http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)

If it is a joke and a waste of time, then why does it seem to work for everyone with this type of web cam pre-installed in Asus type laptops?

If you read the entire page about installing the web cam driver and then modprobe a couple of different libs then restart the Microdia cam will run.

[Here is the link]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft") to tell you how to compile and install the Microdia driver on your laptop.

---

### Post by intel on 2008-06-15
> **linuxwizard said:**
> intel
I don't use or have a Microdia webcam. I suggest the linux-projects.org because it does work for people that are in need of a driver for their webcams. I have seen comments on >  [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) > that it is a joke and a waste of time and no help. I have not been to that website. I have no reason to so I will suggest what I know that has worked for others in the past.

Same thing can be said about Linux, why don't you go around and recommend,
that people use Windows instead, coz you know... and I quote your logic
[quote=linuxwizard]
.........................
I will suggest what I know that has worked for others in the past.[/quote]

My problem is not you recommending another driver, but recommending a closed source binary only driver, that is only available for older kernels & single architecture
and refusing to acknowledge another alternate open source driver that has had a better record of success reports.

intel

---

