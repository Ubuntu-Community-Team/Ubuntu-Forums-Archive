---
title: "Webcam not working - NEO ELAN L2280 N"
date: 2010-07-10
forum: Hardware
---

### Post by Tuna Caserole on 2010-07-10
Hi.  I'm new to Ubuntu and I'm running a Windows 7 and Ubuntu 10.04 LTS release on a laptop from a local distributor here in the Philippines.  The laptop is a NEO ELAN L2280 N.  Everything on the laptop works fine with Lucid except the built in webcam.  The cam works on Windows using BisonCam NB Pro (driver came along with the unit upon purchase).

I did an lsusb and here are the results.

```
idemiloon@flatbox:~$ lsusb
Bus 003 Device 002: ID 046d:c052 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0241 Acer, Inc 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Seems my webcam is on Bus 001 Device 003: ID 5986:0241 Acer, Inc

I did some research and ended up at [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/) and found that my built in webcam is listed as a supported device.

I tried installing luvcview to test if the cam would work as suggested from the Community Documentation.

```
sudo apt-get install luvcview
```

But running *luvcview* gave the results below.

```
idemiloon@flatbox:~$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory
```

The built in webcam can not be detected by Skype.

Any help and solutions would be greatly appreciated.  Thanks!  =]

---

### Post by mörgæs on 2010-07-11
Maybe this will help:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

If you install Cheese, do you get a picture?

---

### Post by Tuna Caserole on 2010-07-12
> **mörgæs said:**
> Maybe this will help:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

If you install Cheese, do you get a picture?
Thanks for the reply **mörgæs** I already did.  I get a prompt on Cheese saying "No device detected."

---

### Post by Tuna Caserole on 2010-08-02
I finally managed to get the built in webcam on my laptop work.  Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=1481557").

Again I'm using a NEO ELAN L2280 N laptop.  The laptop is manufactured by CLEVO a Taiwanese OEM, and is distributed under NEO Manufacturing in the Philippines.

I'm posting the details of what I did in case someone might need it for reference.

I didn't do anything special.  I only followed what was posted on [this particular post]("http://ubuntuforums.org/showpost.php?p=9301136&postcount=30").

Though this laptop has a different webcam, it works perfectly fine with the same process.

First I turned off Skype and Empathy just to be sure.

I manually went to /home/.Skype/username and looked for a file named 'config.xml' and opened it on gedit.

I looked for these lines of codes (it was near the bottom of the file)
```
<TransferWindow>
  <Height>240</Height>
  <NoCancelConfirmation>0</NoCancelConfirmation>
  <Width>480</Width>
  <X>3</X>
  <Y>647</Y>
</TransferWindow>
```

I removed those entries and replaced it with:
```
<Video>
  <CaptureHeight>480</CaptureHeight>
  <CaptureWidth>640</CaptureWidth>
</Video>
```

Clicked on 'Save' and closed the file.

Then I opened a terminal (Applications  > Accessories > Terminal) and typed in the following commands one at a time.  (It is important that you wait until a command is finished before executing the next command).
```
cd /tmp
wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2
tar xvfj tip.tar.bz2
cd v4l*
make
```

*Both *wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)* and *tar xvfj tip.tar.bz2* will take some time before you can finish these set of commands.  As it will be downloading and extracting the files within the current directory you're working in.

It will finish and prompt you that it encountered 1 or 2 errors but its just fine.

Once finished typed in this command in the terminal:
```
gksudo gedit /tmp/v4l*/v4l/.config
```

It will open gedit with the content of the file.

I searched for this line in the xml file:
```
CONFIG_DVB_FIREDTV=m
```

And replaced it with:
```
CONFIG_DVB_FIREDTV=n
```

Afterwards, I just clicked on 'Save' and closed the file.

The next thing to do would be to run these commands one after the other.  Again it is important to wait until these commands finish.
```
make
sudo make install
```

*I made a mistake on this part and accidentally ran the sudo command first and got several error prompts.  Not sure if it made any impact on my system but I just repeated the commands in the correct order just to be sure.

When everything finished, I just restarted my system and the webcam now works on Skype for video calls.

I also installed Cheese and the the webcam now works with no issues.

Video resolution runs well at 640 x 480 with 18 FPS.  Higher resolutions result to stuttering frame rate.

That's all I did.  =]

---

### Post by laure_f_o on 2010-08-03
hello, I have the same problem, but however, I can see my webcam in lsusb after trying several things from other forums/posts. my laptop is an ahtec.
Could it be possible that my webcam is switched off by a combination of keys from my keyboard?
 
thanks, when I get to see my webcam in lsusb again I will try your procedure.
 
thanks again.

---

### Post by Tuna Caserole on 2010-08-04
Sorry I didn't get what you meant there.  Are you saying you CAN or CAN'T see your webcam in lsusb?

Would you mind posting the results you get the results from your laptop after typing these commands in your Terminal?
```
lsusb
```

And
```
lsmod | grep videodev
```

---

### Post by laure_f_o on 2010-08-04
hello, 
 
Sorry I meant CAN'T,, but now I can, I do not know why but my webcam was disabled. I enabled again FN+F10. But I still the same problem, I cannot see the webcam in any application.

---

### Post by laure_f_o on 2010-08-04
xxx@ahtec:~$ lsusb
Bus 002 Device 003: ID 5986:0241 Acer, Inc 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xxx@ahtec:~$ lsmod|grep video
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
video                  20623  1 i915
output                  2503  1 video

I am not able to work the web cam, this is my lsusb ans lsmod. my ubuntu is 64 bits.

---

### Post by Tuna Caserole on 2010-08-12
Hi.  Seems you also have the same internal webcam as I do.  =]

If you're not running Skype, you only need to do the part on my post from this line:
*Then I opened a terminal (Applications > Accessories > Terminal) and typed in the following commands one at a time. (It is important that you wait until a command is finished before executing the next command).*

You should be able to make your webcam work from there.  =]

---

### Post by laure_f_o on 2010-08-12
hello,

Sorry, where are the commands? 

and, my cam does not appear in /dev/video or whatever....

---

### Post by Tuna Caserole on 2010-08-13
> **Tuna Caserole said:**
> Then I opened a terminal (Applications  > Accessories > Terminal) and typed in the following commands one at a time.  (It is important that you wait until a command is finished before executing the next command).
```
cd /tmp
wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2
tar xvfj tip.tar.bz2
cd v4l*
make
```

*Both *wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)* and *tar xvfj tip.tar.bz2* will take some time before you can finish these set of commands.  As it will be downloading and extracting the files within the current directory you're working in.

It will finish and prompt you that it encountered 1 or 2 errors but its just fine.

Once finished typed in this command in the terminal:
```
gksudo gedit /tmp/v4l*/v4l/.config
```

It will open gedit with the content of the file.

I searched for this line in the xml file:
```
CONFIG_DVB_FIREDTV=m
```

And replaced it with:
```
CONFIG_DVB_FIREDTV=n
```

Afterwards, I just clicked on 'Save' and closed the file.

The next thing to do would be to run these commands one after the other.  Again it is important to wait until these commands finish.
```
make
sudo make install
```

Just restart after you've finished all of this.  =]

---

### Post by laure_f_o on 2010-08-13
Hello, I have already done all this but no improvement. One thing is I do not have the /dev/video* link file, I suppose that this is because I do not have the driver installed, but in UVC website is said that my cam is supported.

I saw the errors you mentioned when I do make, but you said it is normal.

Any ideas? Thanks.

---

### Post by Tuna Caserole on 2010-08-13
I just tried opening Cheese again and my problem's back again.  LOL

Apparently the last kernel update made the existing v4l files obsolete.

I'll let you know as soon as I find a fix for this.  =]

-----

Flagged thread as 'unsolved'.  Previous documentation no longer works for latest kernel update.

---

### Post by laure_f_o on 2010-08-13
I finally get my webcam works, BIEN!!!!!!

It was for the kernel, here you have a post,

[http://ubuntuforums.org/showthread.php?t=1536460](http://ubuntuforums.org/showthread.php?t=1536460)

[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

I hope this help you,

but I have a new problem, after reboot my wifi does not work....

---

### Post by Tuna Caserole on 2010-08-17
Wow thanks!  I'll try this then.  Hope it does work.  =]

---

### Post by Tuna Caserole on 2010-08-19
Unfortunately this still doesn't fix my webcam problem.  LOL!

Still searching for solutions.

---

### Post by cherryredz on 2010-09-14
The kernal update at  [http://www.ramoonus.nl/2010/05/linux...u-linux-10-04/](http://www.ramoonus.nl/2010/05/linux...u-linux-10-04/)

also fixed my webcam but as with laure_f_o after reboot my wifi does not work....

any one know a nice easy fix??

---

