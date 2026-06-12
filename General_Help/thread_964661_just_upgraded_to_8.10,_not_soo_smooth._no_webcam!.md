---
title: "just upgraded to 8.10, not soo smooth. no webcam!"
date: 2008-10-31
forum: General Help
---

### Post by Cew27 on 2008-10-31
as the title says just upgraded to 8.10, while most things work better my webcam does not work under cheese anymore all i see is a blank screen. 
how do i fix this?
also transmittion no longer goes into the notification area

---

### Post by PsychedelicReaction on 2008-10-31
i had also some troubles with cheese after upgrading, i think you should test if it is a cheese or a webcam problem. is the webcam working with other software (i.e. skype)?

---

### Post by btermeli on 2008-10-31
I have the same problem, only the diffence is, it works under cheese and amsn and not in skype.

---

### Post by GorBo on 2008-10-31
I have a similar problem -- webcam worked fine in Skype in 8.04 (and was I glad). I did an upgrade yesterday and although it does detect the Logitech Quickcam, video does not work.

Ekiga shows video OK, so I upgraded Skype from 2.0.0.68 to 2.0.0.72, but that didn't solve the problem.

---

### Post by btermeli on 2008-10-31
my webcam is also logitech, may be something is wrong with skype :(

---

### Post by Cew27 on 2008-10-31
mine is a dell xps m1330webcam, the on in the led baclit display

---

### Post by MilesCrew on 2008-10-31
FWIW, I have a Dell Latitude D610 that I installed Intrepid on yesterday. I'm a Windows SysAdmin but a Linux noob so I've been learning a lot. I've got a Logitech Quickcam Pro and mine works great with Skype. At first I wasn't so sure because when I plugged it in there was no notification anywhere that it had been plugged in (like an icon in Windows' tray). However, I installed Skype and tested it and it worked fine.

---

### Post by btermeli on 2008-10-31
I will re-install skype...

---

### Post by btermeli on 2008-10-31
I will re-install skype.

---

### Post by dennis_k85 on 2008-10-31
I also have an issue with my webcam in 8.10. But I am tryitn to use it with motion and cammora, which both worked fine in 8.04. I think the issue must be with the web cam drivers in 8.10. 

Dennis

---

### Post by seetchoo on 2008-10-31
I have same problems with cheese after upgrading to 8.10, but vlc works fine

---

### Post by El Viejo Lobo on 2008-11-02
The same here, since I installed Ubuntu 8.10 my webcam - D-Link DSB-C320 is not showing image buy some kind of statics. It is the same with skype and Camorama. The light on the webcam is working too. It mast be something with the Ubuntu 8.10. The webcam is found by the command lsusb:
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
We will need some help here.

---

### Post by El Viejo Lobo on 2008-11-05
There are 12 threads os the problem and no fix was offered.

---

### Post by tgirardi on 2008-11-06
Same problem. 
AMSN + webcam worked fine on ubuntu 7.04. 
Installed 8.10 and now it doesn't work in:
- skype
- kopete
- amsn
It works fine in cheese.
My webcam uses gspcav driver, which seems to be loaded by default in kernel 2.6.27-7.
I downloaded the sources and tried to compile, but finally I got bored of getting troubles with missing headers which I could not solve (asm/semaphore.h).
If anybody knows about a fix please post it.
Hope this is fixed fast, because it is my only complaint (and a big one) towards kubuntu 8.10.

---

### Post by El Viejo Lobo on 2008-11-06
I found this link a minute ago, I hope I can make it work..

[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

---

### Post by williamts99 on 2008-11-06
> **Cew27 said:**
> 
also transmittion no longer goes into the notification area

Because the default option is for it not to have the tray icon.  You can change this in the menu View>Tray Icon.

Best Regards

---

### Post by tgirardi on 2008-11-07
haven't seen the link that "El Viejo Lobo" posted. Maybe tomorrow I will give it a try. However, for those who don't mind returning to an older kernel, this WORKED for me:
-installed kernel 2.6.25-2-386 (gspcav was not loaded by default so I compiled and installed it)
-downloaded gspcav sources and compiled it (used module-assistant to make all things more easy).
-had a trouble compiling because headers 2.6.25-2-386 had various simbolic links to headers 2.6.25-2 which didn't exist and where not in the repositories. I copied the content from linux-ports-headers-2.6.25-2 (supposed they where the same as 2.6.25-2) to a directory I made named linux-headers-2.6.25-2 (in /usr/src obviously) and everything worked fine.
-installed the module
-inserted it to the kernel using "modprobe gspca"
And webcam started working in amsn.

---

### Post by patrickballeux on 2008-11-07
There is a lot of modifications on the V4L(2) stuff and lots of source code it not compiling anymore...

To test your webcam, you should use "gstreamer-properties".  In the Video tab, for Capture, you have a "Test" button which will help find out if your webcam is working or not.

About Cheese...  it's Cheezy so forget about it!  I hope it will be fixed or remove.  (I had problems also in 8.04...)

If you really want to have fun with your webcam and do some broadcasting, have a look at Webcamstudio for GNU/Linux: [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

---

### Post by El Viejo Lobo on 2009-02-18
Hi

Lately I needed to install Intrepid and I found out that no news about Webcam,Skype and libv4l problem. 
What I do now is: Booting with the 2.6.24... kernel and I have no problem with my webcam.
I do hope that the coming Ubuntu 9.04 will have this problem fixed and will not have major new problems.

---

### Post by prvteprts on 2009-02-28
I just installed 8.10. I have an A4 tech PK-635, and it was recognized "out-of-the-box", however it won't work with Kopete, Camorama, and VLC. In Kopete, I just get a blank screen. When running Camorama, I get an error message, "could not connect to video device". However, it works fine in Ekiga and Cheese.

I think this is more of an Intrepid problem. But I don't know, this is the first time I tried Ubuntu lol. Ubuntu rocks by the way :guitar:

---

### Post by gwm on 2009-12-31
I have the same problem. this web cam worked with 7.04. I tried the suggestion to run **gstreamer-properties** from the terminal and then test the video device under the video tab. There, the camera works fine. I guess that skype, vlc and the like, don't use gstreamer.

I am running Karmic Koala (9.10) so this problem is still unresolved. Oh well, dual boot again! Pity, Karmic really feels nice and polished. I long for the day that I can finally say goodbye to Microsoft.

---

