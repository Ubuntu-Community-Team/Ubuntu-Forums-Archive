---
title: "Help With Infrared Touch Screen:"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by mkincheloe on 2007-04-18
I'm trying to get a USB based IRTOUCHSYSTEMS model K15 touch screen to work with Ubuntu 6.1.  Several drivers for linux based systems are available on their website.  Included in most of these packages are three files:

tkusb.o
unitouch_drv.o
and a readme.txt which is pasted below.

I'm having trouble getting the panel to work in Ubuntu and I'm not even sure which driver I should really use.  Also I'm not sure of the validity of the instructions in the readme.

Any advice or tips?

-Matthew

----------

IRTOUCHSYSTEMS Co.Ltd  USB Touch Screen setup:
 
The version of USB touch screen driver composed of¡¡two parts. irtouch.o , a kernel module to
represent a serial interface to user programs. and a¡¡X Input module unitouch_drv.o.
 
The following are steps:
1. Copy irtouch.o to a directory, I'll assume "/usr/irtouch".
2. run: "cd /dev/usb"
3. run: "mknod irtouch0 c 180 180"
2. copy unitouch_drv.o to "/usr/X11R6/lib/modules/input". 
3. Add one line to /etc/rc.d/rc.local: 
insmod /usr/irtouch/irtouch.o before the line startx.
 
4.Setup the /etc/X11/xorg.conf as follows:
a) Add one line:

InputDevice    "irtouch" "SendCoreEvents"
to Section SererLayout.
 
b) Add one section InputDevice as follows:
 
Section "Inputdevice"
              Identifier "irtouch"
              Driver "unitouch"
              Option "Device" "/dev/usb/irtouch0"
              Option "AlwaysCore"
              Option "screenno" "0"
              Option "MinX"  "70"
              Option "MaxX"  "4055"
              Option "MinY"  "4095"
              Option "MaxY"  "90"
              Option "UntouchDelay" "3"
              Option "ReportDelay" "1"
EndSection

Possbile problems:
 
 after run insmod irtouch.o and before entering X11,
run: "od -h < /dev/usb/irtouch0", if you can see output, the installation is right, or something bad happens, such as ,
you haven't plug touch screen or touch screen is bad.

If you encounter any problem, please don't hesitate to let me know

---

### Post by dorincioran on 2008-04-18
I found your post searching for help with IRtouch touchscreen drivers in ubuntu... 
Since I finally managed to make them work i thought I'd share the experience. I know I might be "a bit" late, but at least someone else may benefit.

I managed to get things going on ubuntu 7.10
This is how i did it:

First of all I could not get unitouch_drv.o working with Ubuntu. I used the .so file that comes as driver for Mandriva and Suse. Since I installed the touchscreen on serial port only the file unitouch_drv.so was needed. 

So what to do with the file? This is a Xorg input module and you need to copy it to the folder where Xorg keeps all the other input modules. Just look in your /var/log/Xorg.0.log file for an entry indicating from where Xorg loads it's input modules (such as kbd or ouse drivers). In my case (and i think this is valid for most ubuntu systems) I found: 

(II) LoadModule: "mouse"                                                        
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so 

so this is the path:
/usr/lib/xorg/modules/input/

i copyed the unitouch.so file to that folder.

Now all you need to do is instruct  Xorg how to use it. This is achieved by editing the xorg.conf file (/etc/X11/xorg.conf)

add this to the file:

a) Add one line:
InputDevice    "unitoptouchscreen" "SendCoreEvents"
to Section ServerLayout.

b) Add one section InputDevice as follows:
Section "Inputdevice"
              Identifier "unitoptouchscreen"
              Driver "unitouch"
              Option "Device" "/dev/ttyS0"
              Option "AlwaysCore"
              Option "screenno" "0"
              Option "MinX"  "70"
              Option "MaxX"  "4055"
              Option "MinY"  "4095"
              Option "MaxY"  "90"
              Option "UntouchDelay" "3"
              Option "ReportDelay" "1"
EndSection

# note: this is what worked for me. it is a combination of 2 xorg configurations sugested by the manufacturer. also, i changed the values for MinY and MaxY since the pointer moved in reversed direction on the OY axis, and this did the trick.

now save the file and restart X (ctrl + alt + backspace)

you should now have a working touchscreen.

well... not quite. there still is a problem: the pointer has some kind of "delay".... and that I find to be very disturbing. I could not find a solution to this problem. 

So, if you (or anybody) managed to get things going the right way, please post back. I would appreciate help on this matter. 
Also, do the linux drivers have some of the features the windows drivers have ? Such as hiding the mouse pointer (which i find rather nice for a touchscreen)?? If yes, how do i access them ? I could not find any documentation for linux drivers....

Best of luck with your touchscreen!!
Let me know how it works out.

---

