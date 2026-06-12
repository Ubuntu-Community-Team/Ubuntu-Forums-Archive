---
title: "trouble with bison cam or alicorp m5602 webcam on joybook s31v"
date: 2009-11-10
forum: Hardware
---

### Post by marcinau on 2009-11-10
I know there have been a lot of posts about this driver but i've looked through them and unless i've missed something there is no existing solution to my problem.  I've tried following other ppls instructions but had no luck.

Can anyone pls help me get my webcam working? I'm using 9.10

In ekiga or in skype or in camorama or in cheese or in vlc and even xawtv i get no joy.

Here is the output of lsusb:

```
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

here is the output of lsmod | grep m5602:

```
gspca_m5602            48360  0 
gspca_main             22812  1 gspca_m5602
```

here is the output of v4lctl -c /dev/video0 list

```
ioctl: VIDIOC_G_STD(std=0x804f07bbfe33a68 [PAL_H,PAL_D,PAL_D1,PAL_N,PAL_60,NTSC_M,NTSC_M_JP,SECAM_B,SECAM_D,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | (null)  | (null)  |
input      | choice | ALi m56 | ALi m56 | ALi m5602
bright     | int    |     125 |     126 | range is 0 => 255
Whitebalan | bool   | off     | off     |
Gamma (sof | int    |    1281 |    1000 | range is 500 => 3000
exposure   | int    |      32 |       0 | range is 0 => 60
gain       | int    |     113 |     113 | range is 0 => 255
horizontal | bool   | off     | off     |
vertical f | bool   | off     | off     |
```

The best i have gotten is a green blocky screen.   I've heard of others saying with karmic koala it works out of the box.

Cheers for any help you can give :)

Marc

---

### Post by marcinau on 2009-11-10
i should also mention that i've tried to view it in vlc with v4l2://(some line i cant recall)/

---

### Post by Lateralis on 2009-11-10
Try ```
gstreamer-properties
```  Under the Video tab and Default Input section, select the appropriate plugin (v4l2 should work, but there are others there).  You should see your hardware listed in a drop down menu called Device.  If you see it you can test it.  If you can test it and if it does work, then the drivers are fine and Ubuntu knows how to work your webcam.  I guess then the problem then moves on to configuring Skype, Ekiga etc.  

If you can't see your webcam in gstreamer-properties, then it will be a hardware thing.  In the first instance, can you check what kernel you're running:

```

uname -r

```

For some reason some people's upgrades from Jaunty to Karmic haven't resulted in the Karmic kernel (2.6.31-14) being left out of the grub start up menu.  If this is a fresh install of 9.10 then there's no need to do the above and I'm out of immediate ideas.

---

### Post by marcinau on 2009-11-10
this is the second time i've seen this. in gstreamer properties i get this image (which i can't figure out how to upload) of coloured bars and static in the bottom right corner.
This is what i got once in cheese.  I think my computer is capable of watching dvb-tv...

---

### Post by marcinau on 2009-11-11
can you see that?

---

### Post by chicoinc on 2009-11-12
i'm listening in on this tread. As I have the exact same problem. 
Hope it's ok

I have a Pacard bell Laptop with integrated webcam

Michael

---

### Post by marcinau on 2009-11-12
does your one have some kind of dvb tv system too?

---

### Post by ian.xerl on 2009-12-22
I have an ACER Aspire 5102 with this built-in AliCorp webcam. I recently installed Ubuntu 9.10, and for the first time since I started using Ubuntu, the webcam actually works!! (sometimes).

After entering ```
gstreamer-properties
``` the dialog shows the images captured by my webcam. So it works. However, it doesn't work in skype (latest version: 2.1.0.47-1 for amd64). And there is not a lot of possibility to configure the webcam in Skype. What can I do?

---

### Post by Erik Andrén on 2009-12-23
Hi, 
Could both of you having attach the output of executing "dmesg" in a terminal window?

---

### Post by martinschiel on 2010-01-12
I hope it is alright if I just come into this thread. I have the exact same problem as mentioned above. I have got the same webcam. Testimage with gstreamer-properties works alright. *Camorama* is not able to capture camera image and Skype shows a greenish picture (see attachment).
As attechment I also sent the output if dsmeg.

Thanks for help.
Martin

P.S Sorry I had to comprimize dsmeg.txt. It was too big.

---

### Post by martinschiel on 2010-01-12
I just found out, that starting Skype wit

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

works fine!!!

I don't know what it does, but it works perfect.

Greets
Martin

---

### Post by marcinau on 2010-01-13
hmm interesting parts about the sensor after gspca

```

[   12.799256] gspca: main v2.6.0 registered
[   12.849072] yenta_cardbus 0000:0a:09.0: CardBus bridge found [17ff:0560]
[   12.849105] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   12.849108] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   12.849116] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01a21b22, devctl 0x66
[   12.866922] gspca: probing 0402:5602
[   12.866927] ALi m5602: Probing for a po1030 sensor
[   12.881310] ALi m5602: Probing for a mt9m111 sensor
[   12.898942] ALi m5602: Probing for a s5k4aa sensor
[   12.929309] ALi m5602: Probing for an ov9650 sensor
[   12.973553] ALi m5602: Sensor reported 0xffff
[   12.973557] ALi m5602: Probing for a s5k83a sensor
[   13.000429] ALi m5602: Detected a s5k83a sensor
[   13.066959] gspca: probe ok
[   13.066984] usbcore: registered new interface driver ALi m5602
[   13.066988] ALi m5602: registered

```

---

### Post by danielpryjma on 2010-02-18
Hey,

I'm very new to the whole Linux thing... I just started yesterday and I'm having the webcam problem. I tried everything here but it still doesn't work. I think I managed to get the camera working cause the led that shows when it's on turns on with skype.

I never programmed anything before, but I'm learning things quite fast.

If you can help me, please do...

Thanks a lot

---

### Post by marcinau on 2010-02-19
here is my dmesg

---

### Post by carandraug on 2010-03-10
> **martinschiel said:**
> I just found out, that starting Skype wit

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

works fine!!!

I don't know what it does, but it works perfect.

Greets
Martin

Using an Asus laptop A6 line(can't see the model anymore). I used to have the same problems. With Ubuntu 9.10 everything worked just fine except skype. I tried this and now it works even in Skype.

From what I read online it seems this commands forces skype to load that file at startup which is a library that deals with video in linux (v4l = video for linux).

[QUOTE=wikipedia]
The dynamic linker can be influenced into modifying it's behavior during either the programs execution or the programs linking. Examples of this can be seen with the ld (unix) manual page. A typical modification of this behavior is the use of the LD_PRELOAD and LD_LIBRARY_PATH environment variables. **The previously mentioned variables adjust the executables linking process by searching for shared libraries at alternative locations and by forcefully loading and linking libraries that would otherwise not be loaded and linked.**
[/QUOTE]

Problem SOLVED for me! :D

---

### Post by marcinau on 2010-06-15
even after a fresh 10.04 install it won't work

maybe i'll submit a bug for it

---

### Post by zurkkruz on 2010-07-06
Hello, i have this same bison webcam on a clevo laptop, and i got to work for me on ubuntu 10.04 by doing the following:

1- Power on the camera, in my case i have to press FN + F10
2- Open console and run gstreamer-properties
3- Go to video and switch between v4ls and v4l until the camera is recognize as a device in v4ls.
4- test it, and after you get the video close it and the console window
5- open cheese and wait a couple of seconds, you should have a image, however i appears to be inverted.
6- open skype
7- go to options, and video options.
8- press test video, and it should recognize the camera.

I do not if it will work for anyone else or if you can actually use it to make a video call, but i hope it helps.

thx

---

### Post by utilitytrack on 2010-10-24
> **chicoinc said:**
> ...As I have the exact same problem.
I have a Pacard bell Laptop with integrated webcam

> **danielpryjma said:**
> ...I'm having the webcam problem. I tried everything here but it still doesn't work.

> **marcinau said:**
> even after a fresh 10.04 install it won't work... maybe i'll submit a bug for it

All who have troubles with ALi Corp. 5602 webcam (PCI vendor/device code is 0402:5602). Here is new ticket on Kernel Bugzilla that describes the problem. Please share your own comments, experiences, logs and patches:
[https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575")

---

