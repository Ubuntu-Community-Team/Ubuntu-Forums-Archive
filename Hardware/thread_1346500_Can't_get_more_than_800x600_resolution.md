---
title: "Can't get more than 800x600 resolution"
date: 2009-12-05
forum: Hardware
---

### Post by benjamonk on 2009-12-05
I have installed Ubuntu 9.10 on my Sony VAIO PCG-QR20 notebook. I've had a couple of issues which are now solved. This remaining major issue I have is that only 50% of the screen is being utilised, i get a black border all around the Ubuntu desktop window. I can only get a max of 800x600 resolution and I need 1024x768.

I have also posted this on lanchpad techanswers a couple of days ago but I have not had a response [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/92704](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/92704)


I am new to ubuntu and linux and don't know what to do about this.

Can anybody help? I have look at other similar answers posted here but the responses appear to depend on the precise specification / chipset of the individual PC.

In case it is helpful, here are my lspci outputs from my machine:

ben@Ubuntu-Bag:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:02.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
ben@Ubuntu-Bag:~$

Also I do not have a xorg.conf file in my file system.

If anyone can help I would be very, very grateful.

Ben

---

### Post by rhythmiccycle on 2009-12-05
do you know how to open a terminal?

if you do what do you get when you enter the code

```

cvt 1024 768

```

---

### Post by benjamonk on 2009-12-06
Hi, thank you for getting back to me.

when I enter CVT 1024 768 i get the output:ben@Ubuntu-Bag:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

---

### Post by benjamonk on 2009-12-06
Hi,

Made some progress - created a xorg.conf file, edited it - but then couldn't log in!

[http://ubuntuforums.org/showthread.php?t=1347562](http://ubuntuforums.org/showthread.php?t=1347562)

B

---

### Post by rhythmiccycle on 2009-12-06
what is the output of:

```

xrandr

```

?

---

### Post by benjamonk on 2009-12-06
right now xrandr is outputing

```

ben@Ubuntu-Bag:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  

```Although i've now removed the xorg.conf file which fixed resolution but couldn't / wouldn't login. (felt so close....!) 

I've previously managed to addmode a mode of 1024x768 using xrander commands but:
a) maximum as quoted by xrandr as still 800x600
b) although the new 1024x768 mode now existed in the display settings screen i got an error message if i tried to apply it.

---

### Post by rhythmiccycle on 2009-12-06
ok, try this:

first copy what "cvt" gave you, after "xrandr --newmode" like this:
```

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

```

then the "xrandr" code tells me that the name of you monitor is "default", so you now add the newmode you just made in the last code to the monitor

```

xrandr --addmode default 1024x768_60.00

```

and finally activate the mode using this code:
```

xrandr -s 1024x768

```

that is what I did. if that works let me know, because there is still a couple of other thing you should know about it.

I hope that work for you

---

### Post by Yellow Pasque on 2009-12-06
Post/pastebin /var/log/Xorg.0.log

---

### Post by benjamonk on 2009-12-07
> **rhythmiccycle said:**
> ok, try this:

first copy what "cvt" gave you, after "xrandr --newmode" like this:
```

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

```then the "xrandr" code tells me that the name of you monitor is "default", so you now add the newmode you just made in the last code to the monitor

```

xrandr --addmode default 1024x768_60.00

```and finally activate the mode using this code:
```

xrandr -s 1024x768

```that is what I did. if that works let me know, because there is still a couple of other thing you should know about it.

I hope that work for you

Thanks for getting back - when i follow those commands, the switch mode command (-s 1024x768 makes the screen flicker but resolution does not change. Although xrandr now outputs that 1024x76 is max resolution

```
ben@Ubuntu-Bag:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 1024 x 768
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   1024x768_60.00   59.9  

```

Also 1024 x 768 selectable through GUI display settings, but if I try to apply it i get error message "UNABLE TO CONFIGURE CRT 0098" ?

I'll post the log file in just a moment

---

### Post by benjamonk on 2009-12-07
I think this is the log file i need to post?

---

### Post by Yellow Pasque on 2009-12-07
[http://ubuntuforums.org/showpost.php?p=8457321&postcount=5](http://ubuntuforums.org/showpost.php?p=8457321&postcount=5)

---

### Post by benjamonk on 2009-12-08
Thank you for your post and link - It makes sense that the monitor is not being detected properly.
 
I am sorry but I have no experience of ubuntu / linux - i'm trying for the first time. I don't know how to tweak the settings in the xorg.conf file.
 
Can you help please or give me more information on how to go about it?
 
Thank you again for your help.

---

### Post by Yellow Pasque on 2009-12-08
Just use what I posted as your /etc/X11/xorg.conf file. You don't need to alter it since it's already set for 1024x768

---

### Post by benjamonk on 2009-12-08
I tried the file you posted at [http://ubuntuforums.org/showpost.php?p=8457321&postcount=5](http://ubuntuforums.org/showpost.php?p=8457321&postcount=5)

This didn't work either I'm afraid. I thought you meant for me to tweak the the Horizsync and Vertrefresh rates, but not sure what to set them to.

---

### Post by Yellow Pasque on 2009-12-08
Try to find the specs for your display.

---

### Post by benjamonk on 2009-12-09
> **Temüjin said:**
> Try to find the specs for your display.
 
Yeah i'm keeping looking on that - I found a data sheet for the intel chipset but i've got no way (currnently) of knowing the specs of teh actual screen in the laptop. Nothing in the manual to tell me the specs or what make / model screen componants are installed..... No luuck on the worldwideweb so far but i'll keep looking.
 
Thanks for all your advice, i appreciate it.

---

### Post by ktinwards on 2010-09-11
> **rhythmiccycle said:**
> ok, try this:

first copy what "cvt" gave you, after "xrandr --newmode" like this:
```

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

```then the "xrandr" code tells me that the name of you monitor is "default", so you now add the newmode you just made in the last code to the monitor

```

xrandr --addmode default 1024x768_60.00

```and finally activate the mode using this code:
```

xrandr -s 1024x768

```that is what I did. if that works let me know, because there is still a couple of other thing you should know about it.

I hope that work for you








hey that accualy does wrk for me. but when i reboot i have the same issue and have to do it all again. how do i make changes perm? idk if this will alreat me to a response. if u want to email me the last bit of info u was talking about it would be appreciated. [email]ktinwards@yahoo.com[/email]

---

### Post by ktinwards on 2010-09-11
i tried  [http://ubuntuforums.org/showpost.php...21&postcount=5]("http://ubuntuforums.org/showpost.php?p=8457321&postcount=5") and it worked well for me. t/y guys/gals
















> **ktinwards said:**
> hey that accualy does wrk for me. but when i reboot i have the same issue and have to do it all again. how do i make changes perm? idk if this will alreat me to a response. if u want to email me the last bit of info u was talking about it would be appreciated. [EMAIL="ktinwards@yahoo.com"]ktinwards@yahoo.com[/EMAIL]

---

### Post by BoyRoy on 2010-10-26
New to Ubuntu, running v10.10 netbook flavour.

I have the same problem and what looks like the same hardware (Toshiba Portege R100).

Following the instructions above, all works up to running the following command:

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

When I run this in terminal it errors as follows:
"xrandr: Failed to get size of gamma for output default"

Hmmph...any ideas?

Thanks in advance.

---

### Post by BoyRoy on 2010-10-28
Update- 1024x768 achieved.

After a bit of digging around, this forum helped me fix my "800x600 max res in a little window" problem:
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/53006]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/53006")

I used the example xorg.conf file Costas Valakas gave on 2009-01-01.

I now have the correct resolution.  Woo.  Monitor still says "Unknown" but not too fussed.

H/W: Toshiba Portege R100 (model no: PPR10E-213M5-EN).

---

