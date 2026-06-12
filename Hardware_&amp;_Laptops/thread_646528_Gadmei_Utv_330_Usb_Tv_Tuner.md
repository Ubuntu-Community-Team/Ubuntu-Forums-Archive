---
title: "Gadmei Utv 330 Usb Tv Tuner"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by mmDush on 2007-12-21
hey guys.
I bought the GADMEI UTV 330 USB tv tuner card day b4 yesterday
with the hope of that I could get is installed in my ubuntu lap top,


I followed the guid in V4L wiki which indicates that it supports my card 
in the documentation. 

when I try 

```
v4l-config
```

it ends up with the error

```
could not open /dev/video0 : no such file or directory
```


when looked into my _**dmesg**_, It indicates that 
```

the v4l module can't auto detect my device since it doesn't have a eeprom and 
pass card=<n> into insmod
```

after above message, it displays a list of devises the it suports and my tv card is in the 37 location


I'm  really confuced, where I have got it wrong,?  coz in the v4l wiki it lists a person who have got workin with the same devise.

can any body help me out please, anybody who got through this..

thanx

---

### Post by mmDush on 2007-12-23
hey guys..

After having my brain to my breakfast I could figure it out over the weekend :lolflag:

though there ain't any reply to my previous message I'll put down the steps, so anybody who
get  through this that problem try following and see... :)


01. Unplug the card from your PC (if you have already plugged it  )

02. To run V4L (Video4Linux) Driver in system, you need following packages, make sure you add them through your Synaptic Package Manager.

```
mercurial
gcc
build-essential
linux-source
```

AND 

type following to download and install your linux headers which is compatible with  your kernel
```

sudo apt-get install linux-headers-`uname -r`
```

03. You must get a copy of the V4L (Video4Linux) Driver to do so tap the following code in a terminal

```
$ mkdir tvdrviver
$ cd tvdriver
$ hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel
```

above commands will download a copy of V4l Driver into your tvdriver folder.

04. Now we have to build the V4L driver and install it into the kernel. to so take following lines in your terminal window.

```
$ cd v4l-dvb-kernel
$ make 
$ sudo make install 
```

if every thing goes good it will install the driver in few mins without any errors.

At this point your must REBOOT your box (b4 you do so remeber to book mark this page :) )


05. You have installed your driver, now it's time to load the Driver. Before we do that I have to tell you this is where my problem was, coz the Driver couldn't detect my device automatically 

so until it can't detect the device it will not give you ***/dev/video0*** 

so what we have to do is we have to do detecting part manually. how we do it..?  this is how.

The em28xx accepts the parameter 'card=<n>' when it's loading, <n> is where you have to mention your device number from the driver device list. so my device is listed on 37th location in the list  
So I'll load my device in to the driver as follows

```
$ sudo modprobe em28xx card=37
```


onece you have followed above command. try following command to verify that it went right

```
dmesg
``` 

if you got it right, the output should be something like this.

```
[ 2397.416000] Linux video capture interface: v2.00
[ 2397.544000] em28xx v4l2 driver version 0.0.1 loaded
[ 2397.544000] usbcore: registered new interface driver em28xx
```

now it's time to plug your device in, so go ahead..

one you are done 

try following code again

```
dmesg
```


then the output will be like this.

```
[ 2549.628000] EEPROM ID= 0x9567eb1a
[ 2549.628000] Vendor/Product ID= eb1a:2861
[ 2549.628000] AC97 audio (5 sample rates)
[ 2549.628000] 500mA max power
[ 2549.628000] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 2549.632000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[ 2549.632000] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
[ 2549.632000] attach inform (default): detected I2C address c0
[ 2549.632000] tuner 0x60: Configuration acknowledged
[ 2549.632000] tuner 1-0060: type set to 69 (Tena TNF 5335 and similar models)
[ 2549.656000] saa7115 1-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[ 2549.684000] attach_inform: saa7113 detected.
[ 2549.692000] em28xx #0: V4L2 device registered as /dev/video0
[ 2549.692000] em28xx #0: Found Gadmei UTV330
[ 2549.692000] em28xx audio device (eb1a:2861): interface 1, class 1
[ 2549.692000] em28xx audio device (eb1a:2861): interface 2, class 1
[ 2549.900000] usbcore: registered new interface driver snd-usb-audio

```


if you got somthing like that Congrats.. you've made it 

ok the bad part it i couldn't get the sound working yet so, currently m watching TV silent mode :lolflag: meanin m working on it. so onece I go through I'll put those steps too so untill that... :popcorn: some motion without sound :)

---

### Post by mmDush on 2007-12-25
Merry Christmas  guys...

Well i was trying all nyt yesterday with no audio problem.. I home someone would have some light to share over here :confused:

---

