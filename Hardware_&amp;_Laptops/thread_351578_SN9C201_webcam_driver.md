---
title: "SN9C201 webcam driver?"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by YooDa on 2007-02-02
Hello,

I am searching for my webcam driver:

Bus 005 Device 004: ID 0c45:624f Microdia 

Its a Sonix SN9C201 webcam.
[http://www.sonix.com.tw/sonix/product.do?p=SN9C201](http://www.sonix.com.tw/sonix/product.do?p=SN9C201)

thanks...

---

### Post by tama on 2007-04-03
Hi,

Did you find anything?
I've got a Microdia 0c45:627b according with lsusb. And I think it uses the same driver you're asking for :-s

Hope we can work it out!
Cheers

---

### Post by jjordan on 2007-04-04
Looks like you guys need the UVC driver

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

kind of a  bear to get it to work.  Have to use V4L2 also.

-j

---

### Post by tama on 2007-04-04
linux uvc won't work here. sn9c201 doesn't seem to be Video Class compliant.

I was rather wondering whether any of you had a webcam with this chipset working and which drivers do you use.

thanks

---

### Post by YooDa on 2007-08-20
Is there now a webcam driver for my SN9C201 webcam?

---

### Post by vivalant on 2007-08-29
Have you tried the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) ?

---

### Post by motin on 2007-09-09
According to Luca, the SN9CXXX driver developer, this model will be supported "soon", as in a version later than the current 2.07. 

Source:
[http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=286&forum=6#forumpost1064](http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=286&forum=6#forumpost1064)

---

### Post by deoncarr on 2007-09-27
Has anybody tried using the drivers from linux-projects? I have tried version 2.07 but find the output extremely blocky. I think it is a driver issue. Has anyone else tried this and had any success.

---

### Post by mrpurple on 2007-11-16
nothing new for microdia 0c45:624f ? i still looking for some driver. Does anybody installed ?
thank you

---

### Post by vivalant on 2007-11-17
There's a binary-only driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by bdonkey on 2007-11-24
Unfortunately, that driver is non-free trialware. The time-limited .deb I tried didn't install, either.

Does anyone know if the gspca guys are working on it?

EDIT: I just checked their mailing list. Looks like there's still plenty of people who want sn9c201 support. :-)

---

### Post by laurentmartin on 2007-12-02
Hello,

I have a usb camera with same usb signature:
Bus 004 Device 005: ID 0c45:6270 Microdia

The driver at linux-projects is not free, so not what I am looking for.

I contacted the customer support at Sonix.

They kindly sent a linux driver (snxcam-fc6.ko).
This is free but proprietary... still no source code.

This driver is compiled for fedora core 6...
it does not load on ubuntu, dmesg gives:
snxcam: Unknown symbol __spin_lock_init
snxcam: Unknown symbol page_address
snxcam: Unknown symbol __might_sleep

I managed to recompile the kernel to have those symbols known...
I added the parameters: (make xconfig)
CONFIG_HIGHMEM4G=y
CONFIG_HIGHMEM=y
CONFIG_DEBUG_SPINLOCK=y
CONFIG_DEBUG_HIGHMEM=y
CONFIG_DEBUG_SPINLOCK_SLEEP=y

Now the driver loads with:
sudo modprobe -f snxcam
after having copied the module in the module dir and depmod...

still, it does not work, as xawtv does not find /dev/video0...


Anyone has similar experience ?


Merci
Laurent

---

### Post by RavanH on 2007-12-05
I have the same issue but WEIRD results! This my camera (X-Gear) according to **lsusb** :
```
0c45:613c Microdia 
```

I could not get the camera working and at one point had the **gspca** AND **uvcvideo** AND **sn9c102**  drivers installed. In that setup, SOMETIMES the camera would work with **camorama -D** but most times it would result in an error "VIDIOCGCAP  --  could not get camera capabilities, exiting....."

There did not seem to be any cause to make the cam work or not. It would just work (but with relatively poor image) and then a few minutes later, the camera would no longer be accessible.

The cam never did anything in Skype (no devices detected) and was only detected by Wengophone  (openwengo.com) but did not show any image.

Now I have only the **uvcvideo** driver and the cam simply does not perform anymore to camorama. Never. Nor is it recognized by Wengophone. While on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) (scroll way down, at the bottom of the list) I read that the Microdia is supported by the linux-UVC project driver.

I amd on a Gutsy AMD64 setup, so that might explain some of the weird behaviour but I am sure there is more to it. Under Feisty (also 64bit) it just worked perfectly! :confused:

Anybody any suggestions? Anybody got this working under Gutsy?

---

### Post by RavanH on 2007-12-12
Figuring the abundance of drivers would not be benificial to the cams performance, I decided to try to get rid of all but the sn9c102 driver... 

By doing ```
 sudo gedit /etc/modprobe.d/blacklist
``` and adding ```
blacklist gspca
``` on a new line, the gspca driver was easily prevented from loading at boot. I have no clue why this did not work for the uvcvideo driver... 

I finally removed it from my system by doing ```
sudo locate uvcvideo
``` which returned the location of the ko file. I then deleted it with ```
sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko
```

After this, rebooted and checked to make sure only sn9c102 loaded with ```
$ lsmod | grep videodev
videodev               31360  1 sn9c102
v4l2_common            21888  2 compat_ioctl32,videodev
v4l1_compat            15364  1 videodev
```

Sadly, after that, my cam still does not work so I returned to ```
 sudo gedit /etc/modprobe.d/blacklist
``` and changed the line ```
blacklist gspca
``` to ```
blacklist sn9c102
```

After this, my cam works... Doing, ```
camorama -D
``` in a terminal window, results in a very dark but live cam image. I find it impossible to adjust it to an acceptable brightness level but at least it is something ;)

Even Wengophone (on AMD64!) shows the cam image. Only Skype (32bit) still reports 'No device found' :(

Maybe reïnstalling the uvc driver without the other ones interfering (by blacklisting them both) will prove to get me a better image... If so, I will report about it here.

---

### Post by SqRt7744 on 2007-12-16
Nice, but according to your usbid, the camera you have is a SN9C120 *not* a SN9C201... so your approach is unlikely to work for the rest of us.  Actually to be honest it just flat out won't work.  But thanks anyway!  :)

-p

---

### Post by vivalant on 2008-01-05
For those Microdia webcams, try the most recent version of the SN9CXXX at [http://www.linux-projects.org](http://www.linux-projects.org) . It works for me.

---

### Post by dm215 on 2008-01-06
I am running Gutsy on a 64-bit system, and I have this camera 0c45:624f Microdia, SN9C201.  I would load and run this driver from Luca Risiola, SN9CXXX, if it would work on my 64-bit system.  Luca seemed to indicate in his FAQ that there was a 64-bit version available, but when I couldn't find it I emailed him, and in his response he said there wasn't one -- surely he would tell me if I could just load the 32-bit version, right?  He directed me back to his FAQ, where he says that he'll write me one for EUR 50-100, but of course I can't do that since the camera itself is probably not worth even EUR 50.

But, if anyone knows otherwise with the 32-bit version of this driver, I'd gladly try it out on my system as well.  Otherwise, I guess I'm waiting for the gspca version, or getting a new camera.


Best,
-David

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

details like SN9C201 SN9C202 bridges, while chips like OV7660 need to be reported

---

### Post by motin on 2008-01-08
> **intel said:**
> For all those with microdia (0c45:xxxy) webcams, please visit this website

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

details like SN9C201 SN9C202 bridges, while chips like OV7660 need to be reported

Doesn't your camera work with the latest linux-projects.org drivers?
[http://www.linux-projects.org/modules/news/article.php?storyid=136](http://www.linux-projects.org/modules/news/article.php?storyid=136)

---

### Post by intel on 2008-01-11
I would like to know your reason for suggesting the following site
http://www.linux-projects.org/modules/news/article.php?storyid=136

People don't buy "cheap" webcams only to spend more for "half assed drivers",
(more than what the webcam is worth?, are you bad at math? Cost Vs Benefit ?)

besides, when U plug in a pendrive, do you expect to go to buy a driver just for that pen drive?

It should be Plug'N Play, webcams should be Plug'NPlay, that means the drivers should be in the linus tree.

Instead of suggesting newbies to go to the above site, instead you should tell them to buy another webcam that is already working under linux (plug'N play).

---

### Post by motin on 2008-01-11
> **intel said:**
> I would like to know your reason for suggesting the following site
[http://www.linux-projects.org/modules/news/article.php?storyid=136](http://www.linux-projects.org/modules/news/article.php?storyid=136)

People don't buy "cheap" webcams only to spend more for "half assed drivers",
(more than what the webcam is worth?, are you bad at math? Cost Vs Benefit ?)

besides, when U plug in a pendrive, do you expect to go to buy a driver just for that pen drive?

It should be Plug'N Play, webcams should be Plug'NPlay, that means the drivers should be in the linus tree.

Instead of suggesting newbies to go to the above site, instead you should tell them to buy another webcam that is already working under linux (plug'N play).

I don't know if you've ever considered that there are people like me that actually threw Windows in a bin and started using Ubuntu. I had formerly bought a "cheap" webcam which formerly was plug'n'play but now had no available driver. 

To pay $14 for a driver instead of buying a new cam for $40+ is valid in my cost vs benefit calculation. Why recommend others to buy new cams instead?

I agree that 1. existing linux users planning to buy web cam preferably should choose a supported one and 2. it would be great if the driver was available in Linus' tree, free and open source. 

But, as long as you or other haven't written those drivers (or convinced the closed-source driver author to release the drivers under an open license) I don't see anything negative in recommending that site so that users can have a choice of whether or not to pay for a driver if he/she wants to use his/hers webcam before it is supported by free and open source drivers. Do you?

---

### Post by motin on 2008-01-11
Question at hand is what we can do to make this driver freely available. 

First, here is the relevant post in Luca's FAQ:

> 4. Q: Will you release the source code one day?
   A: It's likely I will never release the source code, unless I have
      financial proposals. The best candidate is the manufacturer of these
      controllers. If you would like to see this driver released under
      the GPL to everyone, please send them a personal request.
      The more requests they will see, the more they will consider this driver.
   
      Another way is to collect the money once from all the potential
      users, according to the principles of the ransom model:
      "A publishing model where copyrighted works (such as books, software,
       or music) remain proprietary until a total amount of money is
       collected or a certain date arrives, at which point the work is
       automatically freed to the public."
      The terms of this approach will require a preliminary discussion
      between me and a group of interested users. Contact me in this case.

I just wrote on [http://www.sonix.com.tw/sonix/fae.do:](http://www.sonix.com.tw/sonix/fae.do:)

> Hi!

Have you considered releasing open source linux drivers for your Video/Image controllers?

Luca Risolia has just release an updated version of his closed-source driver that supports the SN9C2XX controllers ([http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7))

If you consider making a financial proposal to Luca in order to make the driver available for more linux systems you can and will expect a lot of credit, Goodwill and new customers. 

Please don't ignore my inquiry, but respond on what your stand is in this question. 

Cheers,

Fredrik

Various ways to go from here:

1. Collecting a "ransom" donation through an independant group - a donation that Luca will receive when he releases the driver under an open license. 
2. Pushing Sonix to make a financial proposal to Luca in order to release the driver under a less restrictive license.
3. Reverse engineering the webcam under a supported OS and writing new drivers which will be released under an open license. 

What should we do?

---

### Post by vivalant on 2008-01-11
> **intel said:**
> I would like to know your reason for suggesting the following site
[http://www.linux-projects.org/modules/news/article.php?storyid=136](http://www.linux-projects.org/modules/news/article.php?storyid=136)

People don't buy "cheap" webcams only to spend more for "half assed drivers",
(more than what the webcam is worth?, are you bad at math? Cost Vs Benefit ?)

besides, when U plug in a pendrive, do you expect to go to buy a driver just for that pen drive?

It should be Plug'N Play, webcams should be Plug'NPlay, that means the drivers should be in the linus tree.

Instead of suggesting newbies to go to the above site, instead you should tell them to buy another webcam that is already working under linux (plug'N play).

Sorry, but I do not agree with you here. I have many webcams but NONE is really working out of the box with any application, apart my SN9C201 with that binary-only SN9CXXX driver. The gspca driver does not support the 2XX and V4L2 and even with V4L1 gives some problems. I think the author has put a lot of efforts in writing the driver and so far it's worth my $14. Okay, $14 for each version of the kernel might be too much, but I think it's also a pain to for the author to make packages for every kernel version change and keep track of the payments. As far as I know, he does prefer to be paied once by either all the users or Sonix. Personally, I would prefer pushing SoNix to contact him for an agreement and see the driver in the mainline kernel soon. However, the "ransom" idea is not so bad too.

---

### Post by intel on 2008-01-14
not everyone's $14 are equal, there's the concept of utility, a rich man's $14 is not of the same utility as a poor man's $14,

and in this case $14 from driver is not acceptable for a max $22 webcam.

Sonix does not need to pay anyone to write drivers, they have the specs,
they have already demonstrated that they can write a driver
http://microdia.googlegroups.com/web/SN9C201(driver-linux-FC4).tar.gz
They stopped distributing it, due to legalities with binary kernel module.

Sonix will not release the programming info, since then they would have to actually compete *Gasp*

If currently the webcams are not plug'n play, then its all our fault, bug the kernel developers, V4L2/uvc/etc developers & chat client developers(in that order)

Luca Risola, the code that made it into 2.6 was good, about the website linux-projects.org here is what Michel xhaard had to say

> > The following page says: "Compared to the opensource SN9C1XX and the
> *obsolete GSPCA driver*, the Generic SN9CXXX driver provides better video
> quality at higher framerate, supports more hardware and works with any
> application". It's true?
>
> Ref: [http://www.linux-projects.org/modules/news/article.php?storyid=136](http://www.linux-projects.org/modules/news/article.php?storyid=136)

Ho!! you should not goes to this "devil" website ;-)
Gspca is not dead despite what Luca say
regards
[COLOR=#888888]--
Michel Xhaard
[http://mxhaard.free.fr]("http://mxhaard.free.fr/")
[/COLOR]

I have no problem if Luca prefers to be paid for code,(we all do), 
but this is not a custom software job, 
If you prefer to pay for everyday/mundane/routine/software please visit this website http://www.microsoft.com

---

### Post by peatrap on 2008-01-15
Who has a web cam that works, what brand is it and why did i buy a radio shack giga ware web cam, oooo i remember they were 2 for $19.00, they do work on xp but I do not want to use xp Do the hardware builder see what they are missing out on by not providing support, now i must take them back. Wheres my receipt

---

### Post by vivalant on 2008-01-15
> **intel said:**
> not everyone's $14 are equal, there's the concept of utility, a rich man's $14 is not of the same utility as a poor man's $14,
and in this case $14 from driver is not acceptable for a max $22 webcam.


Ok.. this might be better discussed with Luca. At his homepage I can see thousands of downloads, if every user donated $3, not $14, for each download, i think it would fairly satisfy Luca's requirements. The "ransom" idea is not bad here in my opinion.

> **intel said:**
> 
Sonix does not need to pay anyone to write drivers, they have the specs,
they have already demonstrated that they can write a driver
[http://microdia.googlegroups.com/web/SN9C201(driver-linux-FC4).tar.gz](http://microdia.googlegroups.com/web/SN9C201(driver-linux-FC4).tar.gz)
They stopped distributing it, due to legalities with binary kernel module.


I cannot say anything about their driver, as now it's for a very old Fedora distribution and I have never tested it in the past, but I don't think that they had legal problems, UNLESS they had included some GPL'ed stuff into their driver, which just shows up they do not have the know-how to write a whole driver by themselves..

---

### Post by tiepoe on 2008-07-15
I have 3 old Microdia webcams, 2 of them show up as exactly the same usb devices even tho they are very different externally. lsusb lists them thus:

Bus 003 Device 002: ID 0c45:6029 Microdia Triplex i-mini PC Camera
Bus 002 Device 004: ID 0c45:6029 Microdia Triplex i-mini PC Camera
Bus 005 Device 012: ID 0c45:600d Microdia

on both my amd64 and x86 kubuntu 8.04.1 systems the sn9c102 driver modules do not work. The gspca driver modules however work fine. camstream  and v4l-info identifies them all 3 exactly the same as:
 "Sonix sn9c10x + Pas106 sensor"   

They are all pretty poor pictures and only 352x288 max pixels (color).

---

