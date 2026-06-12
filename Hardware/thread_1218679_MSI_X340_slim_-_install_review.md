---
title: "MSI X340 slim - install review"
date: 2009-07-20
forum: Hardware
---

### Post by 090178 on 2009-07-20
Hi there,

i've been digging around the web and ubuntuforums.org for information, feedback nad conversation on MSI X340 Slim UBUNTU install. Not much.

It may start from here then.

The machin :
MSI X340 Slim (no cd reader)
Vista (no choice)
Partition 50% to window
50% to linux


install through wubi of the ubuntu 9.04

No WIFI
No Sound

It remembers me the install of ubuntu on my MSI wind.


Is anyone facing the same problems ?

Could you share links and methodology to get my wifi up ?

looking forward to read from you.

---

### Post by danboy on 2009-07-23
I installed ubuntu netbook first then used synaptic to install gnome etc.. worked like a charm, wireless, sound both work great.

Had to compile webcam drivers. And touchpad doesn't handle multi touch, but some people have had success patching the kernel for that.

---

### Post by 090178 on 2009-07-28
Hey Danboy,

thanks for your feedback and reply. I am downloading the netbook remix and will try tonight. You made my day ! I so pissed off using MS.

I'll certainly share my own comments on the forums for other readers.

Can you advice where you found your webcam drivers ? Any helpful how-to online ?

Thanks

090178

---

### Post by Fuchur777 on 2009-08-12
> **danboy said:**
> I installed ubuntu netbook first then used synaptic to install gnome etc.. worked like a charm, wireless, sound both work great.

Had to compile webcam drivers. And touchpad doesn't handle multi touch, but some people have had success patching the kernel for that.

@ Danboy: Can you publish your compiled webcam drivers somewhere?
Or email them to me? Or give a little explanation how to?

Downloading the NBR at the moment.

Warm Regards

Fuchur

---

### Post by chiel-s on 2009-10-15
Hi,

I installed Ubuntu 9.04 on my MSI x340 successfully. What i did:


[LIST]
[*]Download the latest ubuntu image file and make your usb stick bootable by using [unetbootin]("http://unetbootin.sourceforge.net/")
[*]Plug your stick into your MSI X340, boot it up, choose boot options en choose the right usb device.
[*]Follow the setup instructions
[/LIST]
Everything works out of the box, except the webcam and front mic. Install the linux uvc driver for fixing up the webcam. Follow this guide: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC). I have tested it with Cheese and it works!

I haven't found any solution for the front mic [yet]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1737729.html").

Cheers :)

Chiel

---

### Post by sshlyk on 2009-10-16
Could you please describe your steps getting **webcam** to work on msi x340.
I am running Ubuntu 9.10. lsusb shows 

Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. 

However skype does not detect camera. I tried to compile uvc but got

uvcvideo-214c94aa62aa/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory

Help

---

### Post by sshlyk on 2009-10-16
I was able to compile uvc (by disabling this module in Makefile)
However, when I run

*sudo modprobe uvcvideo*

I get

[I]WARNING: Error inserting videodev (/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/videodev.ko): Invalid module format
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Invalid module format[/I]

---

### Post by sshlyk on 2009-10-16
I got it to work. Compiled against wrong headers first time. Now time to fix mic :)

---

### Post by parthab on 2009-10-28
Did you back up your window partition or in any shape or form make a Windows installation disk in case anything goes wrong with that partition?

Thanks,
Partha

---

### Post by sshlyk on 2009-11-13
> **parthab said:**
> Did you back up your window partition or in any shape or form make a Windows installation disk in case anything goes wrong with that partition?

Thanks,
Partha

No :) screw windows

---

### Post by sshlyk on 2009-11-13
fix for the touchpad should be released with a new kernel .32

---

### Post by iztok.jeras on 2009-12-11
Ciao,

I installed Ubuntu Karmic (9.10) 64bit on my MSI x340 (the version with the SU3500 cpu).

The installation went smooth except for the next things:
- camera
- mic
- touchpad
- SM card reader, I have not tried it yet
- Adobe flash (links not working, maybe mouse clicks not working?)

The camera problem was easy, since the new kernel has USB camera support integrated, all I had to do, was to manualy enable it (Fn+F6).

I am not sure about the mic, it might not have been working properly at the beginning, but now it works fine. I did a kernel update to 2.6.32 and back to 2.6.31, and played with the configuration (check if it is not muted).

The touchpad is a problem, it is a Sentelic not a Synaptics, there are problems on windows too (scroll not working) see this post:
[http://slashstar.com/blogs/alex/archive/2009/06/02/msi-x340-touchpad-driver.aspx](http://slashstar.com/blogs/alex/archive/2009/06/02/msi-x340-touchpad-driver.aspx)
There is a GPL driver for this touchpad and it should be present in kernel 2.6.32, but I was not yet able to make it work.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869)

I will spend some more time trying to fix the touchpad and later probably create a PPA with the fix, but I have to find some help first.

About the flash problem, I will probably wait for Adobe to release the 4bit flash 10.1

Iztok Jeras

---

### Post by sshlyk on 2010-01-24
Does anyone have problems with the fan when computer is Idling?   It adjusts to the load but never stops, which I find annoying :(

---

### Post by koekiemonster on 2010-02-15
i managed to fix the touchpad issues and made a howto. its post 30 and 31 in the launchpad topic:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869)

---

### Post by gregology on 2010-02-18
I'm very impressed with MSi X340, it's worked out of the box on Mint 8 i386 (ubuntu 9.10)

---

### Post by gregology on 2010-03-10
I'm really struggling with the mouse pad, it's nearly a two handed job, I'm a bit disappointed :(

---

### Post by gregology on 2010-03-11
Now my hard drive is failing and the z key is intermittent... arrrgh... Not happy after only 3 weeks.

"Disk has many bad sectors, backup all data and replace disk"

I'll be getting in contact with MSi.

---

### Post by whatname on 2010-03-12
> **sshlyk said:**
> Does anyone have problems with the fan when computer is Idling?   It adjusts to the load but never stops, which I find annoying :(
I have MSI x600 and I have the same issue, have you addressed it yet?

---

### Post by blah500 on 2010-04-30
I have the X-Slim 600. I installed lynx and my toggle fn+f6 does not turn on the webcam like it doe in windows. Is there a way to do this with code or as root or something?

---

### Post by gregology on 2010-05-24
I'm back baby! New x340 is working a treat, running 9.10. everything works except the inbuilt mic which is odd because the mic input works. I'm pretty sure it must be a switch somewhere.

---

### Post by kvizz on 2010-06-10
Does anyone have suspend and hibernate working correctly on msi x340 and Lucid?

---

### Post by gpalouk on 2010-06-25
YES! All are working Perfectly (Suspend & Hibernate)!!!

---

### Post by udomwattawee on 2010-06-25
Does anybody know if Asus N61JQ with core i7 and ATI 5730 will work on Ubuntu?

---

### Post by abhilashkumar on 2010-07-06
I have been reading this thread, and I have a very basic question regarding the install of Ubuntu on the X340.

Can't I just use an external DVD Drive and boot the Ubuntu live CD from there and install?

Is it necessary to go through the USB disk route?

I am actually planning to buy the x340 and I already have an external DVD drive. I am sure that the bios has the option to set the boot device to DVD/CD drive right!

Correct me if I am wrong so that I don't end up having to fight during install :-)

---

### Post by ddarko on 2010-07-08
I did that the day before yesterday. Worked fine.

Edit:
Has anyone tried out the bluetooth? I just noticed that its not working on my x340 with 10.04!

---

### Post by abhilashkumar on 2010-07-08
> **ddarko said:**
> I did that the day before yesterday. Worked fine.

That's great! So no need to mess around with Bootable USBs and stuff.

---

### Post by ddarko on 2010-07-12
Working with ubuntu 10.04 on my x340 i now noticed some bugs. Does someone have problems with bluetooth? The Fn+F9 combination doesn't work, no word in dmesg. The second thing is, when i deplug the power cable, it always shows up a notification, saying that it failed to go in suspend/hibbernation mode and my accu power is enough for 2min. After clicking cancel to all, its still running and the accu-meter says 2hours power left.

Any suggestions?

---

### Post by sshlyk on 2010-08-07
> **ddarko said:**
> Working with ubuntu 10.04 on my x340 i now noticed some bugs. Does someone have problems with bluetooth? The Fn+F9 combination doesn't work, no word in dmesg. The second thing is, when i deplug the power cable, it always shows up a notification, saying that it failed to go in suspend/hibbernation mode and my accu power is enough for 2min. After clicking cancel to all, its still running and the accu-meter says 2hours power left.

Any suggestions?

I experience same bug. Just google it, and you will find the way to disable this policy as a quick fix.

---

### Post by MR_se7en on 2012-09-24
Anyone get the x340 to overclock? It would be nice to watch some full screen youtube videos without it freezing. I know its been a long time since this laptop was published but it would still be fun.

---

### Post by overdrank on 2012-09-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

