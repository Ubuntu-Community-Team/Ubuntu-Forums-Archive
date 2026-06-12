---
title: "webcam installation SN9C201 (Sonix)"
date: 2008-07-29
forum: Hardware
---

### Post by mbooma on 2008-07-29
Bonsoir

I instal my new webcam in windows and it say "USB 2.0 pc camera (SN9c201)".

I want instal it in ubuntu 8.04, I try with Amsn to see if it's detected but he doesn't detect it



LSUSB

Bus 007 Device 003: ID 0c45:6262 Microdia
Bus 007 Device 001: ID 0000:0000 
Bus 006 Device 002: ID 058f:6366 Alcor Micro Corp.
Bus 006 Device 001: ID 0000:0000 
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000


I think webcam ID 0c45:6262 Microdia


can I make it working in ubuntu 8.04 ??





i make some search with google and I have this If it can help to help me :lolflag:

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

[http://groups.google.com/group/microdia/browse_thread/thread/2a8232ddf447e6db](http://groups.google.com/group/microdia/browse_thread/thread/2a8232ddf447e6db)

i don't know how to use patch file in 3rd link...



someone can help me ??



tanks for all :)

---

### Post by aomlives on 2008-07-29
Did you try everything on [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)?

EasyCam worked for me...

Otherwise maybe [this link]("http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7") may help, as mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=569252").

Good luck.

---

### Post by mbooma on 2008-07-29
thanks aomlives

I think Easycam is just a software who work with webcam when it was installed...

I Try last version here [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/) with gdebi but it say that I must instal **linux-image-generic** and I verifie in synapric and it's already installed.....i reinstal but I have same message :confused:

[http://img244.imageshack.us/img244/4467/captureyl5.png](http://img244.imageshack.us/img244/4467/captureyl5.png)

any other proposition please :roll:

---

### Post by mbooma on 2008-07-29
Hi again

i see some users have same probleme here [http://ubuntuforums.org/showthread.php?t=584847](http://ubuntuforums.org/showthread.php?t=584847)


any solution please ??

---

### Post by aomlives on 2008-07-29
I did some ultimate researching and all things come back to the solutions discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=351578](http://ubuntuforums.org/showthread.php?t=351578)

If your cam isn't supported on this site ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) and the driver from linux-projects.org didn't work (understandably, it was an old distro version after all, the others are time-limited) then I regret to say there isn't much you can do to make your webcam work...

Looks like many people are searching for a GPL licensed Ubuntu driver for this specific type of webcam. Maybe it'll come out soon, I don't know, but from what I see, there's no free way of getting your cam to work at the moment :(

I'm sorry but it seems to be the only answer...

---

### Post by mbooma on 2008-07-29
Ok...I will try this ^^

it's not very easy for me because I am beginer and i have never instal driver with ubuntu

also I will try this free project


> **mbooma said:**
> 
[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

[http://groups.google.com/group/microdia/browse_thread/thread/2a8232ddf447e6db](http://groups.google.com/group/microdia/browse_thread/thread/2a8232ddf447e6db)

take a look please and tell me if it's intested ??


thanks again !!

---

### Post by aomlives on 2008-07-29
I don't know much about drivers either I'm afraid. I have to say this project looks rather promising, although I don't know why it isn't as known as it should be considering it's free...

Anyway did you try installing the driver in the second link? Looks like that might work and is indeed applicable on your cam.

About the third link at first glance I haven't got a clue what to do with those files. I hope someone more experienced than I could explain that... :)

I'll have a closer look when I have a little more time though, in the meantime can you say whether the second link worked?

---

### Post by mbooma on 2008-07-30
Up...

---

### Post by mbooma on 2008-08-01
Up......

---

### Post by intel on 2008-08-20
0c45:6262 works with the Microdia driver please go here
[https://groups.google.com/group/microdia/](https://groups.google.com/group/microdia/)

if you need any sort of help in installing that driver on ubuntu,
just join that google group and ask for help there, they will help you.

how to apply patches is explained here as well
[https://groups.google.com/group/microdia/msg/9689ca3ebc34eca2](https://groups.google.com/group/microdia/msg/9689ca3ebc34eca2)

---

### Post by kushykush on 2008-09-17
Mbooma:  Were you able to install your webcam?  I have a "Rosewill" webcam, but it uses the same SONIX 201 driver.  I have the audio but no picture.  It is very disappointing.  As a fall back I have Windows Vista. Which is why I do not rely on Linux.  However, I expect better from the Ubuntu team. How can these people ignore webcams for so long?  Anyway, if you found a solution, and if your webcam is working under Ubuntu 64 bit, then please post the solution.  Thanks!

---

### Post by man_bash on 2009-01-15
As a possible solution, I am trying to use windows drivers via ndiswrapper. I have installed the driver executable via wine, ran ndiswrapper, looked at the errors, found the files needed by the setup, uninstalled, put all the needed files into one folder, and installed again. ndiswrapper reported a success, but I cannot test by a restart right now, maybe tomorrow. I have also zipped the files needed, and uploaded them to mediafire (the first free file storage google gave me lol), named Sonixwindriver.zip, about 2.76 Mb.

so, to install a camera:
1)   install ndiswrapper via Synaptic
2)   download a .zip file from [http://www.mediafire.com/?d2cyydmb2cj](http://www.mediafire.com/?d2cyydmb2cj)
3)   extract all the files from the archive to an easy directory (say, /home/username/sonix)
4)   in terminal, run ```
 sudo  ndiswrapper -i /filepath/filename.inf
in this case
sudo  ndiswrapper -i /home/user/sonix/snp2std.inf
```
5)   reboot
6)   test!!!

I use Intrepid Ibex, 64-bit.

---

### Post by man_bash on 2009-01-15
> **kushykush said:**
> However, I expect better from the Ubuntu team. How can these people ignore webcams for so long?
Ubuntu team does a FANTASTIC job at what they do - making a great operating system. Hardware drivers are a responsibility of the hardware makers, you wouldn't expect Microsoft to make drivers for your sound/video/LAN card, would ya? If you wanna b!tch at someone because your webcam is not supported - try Sonix 1-st and foremost. Maybe with enough pressure they will make a driver for linux.........

---

### Post by ytmin1983 on 2009-03-25
Please SEE the following link:
[http://fun.0110.cn/viewthread.php?tid=404317&extra=&page=1](http://fun.0110.cn/viewthread.php?tid=404317&extra=&page=1)
[http://wiki.ubuntu.org.cn/index.php?title=%E4%BD%BF%E7%94%A8EasyCam%E5%AE%89%E8%A3%85%E6%91%84%E5%83%8F%E5%A4%B4&variant=zh-tw](http://wiki.ubuntu.org.cn/index.php?title=%E4%BD%BF%E7%94%A8EasyCam%E5%AE%89%E8%A3%85%E6%91%84%E5%83%8F%E5%A4%B4&variant=zh-tw)

---

### Post by ytmin1983 on 2009-03-25
Please SEE the following link:
[http://fun.0110.cn/viewthread.php?tid=404317&extra=&page=1](http://fun.0110.cn/viewthread.php?tid=404317&extra=&page=1)
[http://wiki.ubuntu.org.cn/index.php?title=%E4%BD%BF%E7%94%A8EasyCam%E5%AE%89%E8%A3%85%E6%91%84%E5%83%8F%E5%A4%B4&variant=zh-tw:guitar:](http://wiki.ubuntu.org.cn/index.php?title=%E4%BD%BF%E7%94%A8EasyCam%E5%AE%89%E8%A3%85%E6%91%84%E5%83%8F%E5%A4%B4&variant=zh-tw:guitar:)

---

### Post by raix on 2009-04-29
Hey,

has anobody a microdia cam running under Ubuntu 9.04?

I tried to get my old cam up, which worked like a charm with 7.10.

It's an Microdia 0c45:613b like lsusb tells us:


```

Bus 001 Device 005: ID 0c45:613b Microdia Win2 PC Camera

```


I followed the instructions at this google-group:
[http://groups.google.com/group/micro...er-draft?pli=1](http://groups.google.com/group/micro...er-draft?pli=1)

But after plugging in the Camera dmesg shows me this:

```

[ 1363.665933] usbcore: registered new interface driver sn9c20x
[ 1363.665941] sn9c20x: SN9C20x USB 2.0 Webcam Driver v2009.01 loaded
[ 1380.925060] usb 1-4.4: USB disconnect, address 4
[ 1380.925775] usb 1-4.4: Disconnecting SN9C1xx PC Camera...
[ 1380.925782] usb 1-4.4: V4L2 device /dev/video0 deregistered
[ 1386.244180] usb 1-4.4: new full speed USB device using ehci_hcd and address 5
[ 1386.337131] usb 1-4.4: configuration #1 chosen from 1 choice
[ 1386.337526] usb 1-4.4: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[ 1386.387396] usb 1-4.4: OV7660 image sensor detected
[ 1386.574767] usb 1-4.4: Initialization succeeded
[ 1386.574876] usb 1-4.4: V4L2 device registered as /dev/video0
[ 1386.574881] usb 1-4.4: Optional device control through 'sysfs' interface disabled
[ 1386.622471] usb 1-4.4: usb_submit_urb() failed, error -28

```

And of course camorama etc. can't get a connection to the camera.
So i tried blacklisting the kernel-modules of gspca and uvcvideo, because i remember doing the same in 7.10. Just replacing gspca with the self-compiled microdia-driver.

Has anyone got a hint for me?

---

### Post by raix on 2009-04-29
I found my obvious mistake.
The cam is a sn9c102 and not a sn9c2xxx
So I moved to the sn9c102-driver and now I'Ve a picture.
But it's very laggy....

---

### Post by OuahabiX on 2011-02-08
I'm still struggling with the same 0c45:6262 (SN9C201 + OM6802) webcam to run on my Ubuntu up to this day, I've played with the Microdia Base code a little bit, but all I got is a green image with my shadows; so, yes, I was communicating with the cam but not as it should.

The driver was using the V4L as a backend to handle the transmitted data, and I think I should go back to learning the basics, i.e. I2C drivers' simple programming before trying to use something related to the V4l for instance.

All I need is some free time after this exams finish (I don't have it right now), the OM6802 data sheet (I have it), some I2C documentation (I have it), and a coder-partner to chit-chat with about this issue (I don't have any at the moment, but we may find one through this thread, for motivation purposes only!). Or may be we can go on working on other projects too :)

---

