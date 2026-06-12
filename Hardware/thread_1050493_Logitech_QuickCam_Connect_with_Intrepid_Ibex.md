---
title: "Logitech QuickCam Connect with Intrepid Ibex"
date: 2009-01-25
forum: Hardware
---

### Post by ShaddamIV on 2009-01-25
After searching this forum and the Internet, reading many post and tutorials, I am still back to square one.

None of them are made for new users (from my point of view).
And most of the solution found applied to older version of Ubuntu.

I tried to compile the latest version of gspca by following a tutorial, then tried to repair the errors in the code with a patch from someone who wrote an article about it.

Still get plenty of errors while trying to compile it.
I am a c++ programmer but repairing this code is beyond my comprehension.

Is there an easier way? Like downloading a binary of the driver?

The problem is that it does not compile on Intrepid Ibex. Is it?

Is there a webcam that I can buy that would work automatically in Intrepid Ibex?

I bought this camera because some people wrote that it was compatible with Linux? Guess "compatible" has not the same meaning in the Linux world.

---

### Post by teaker1s on 2009-01-28
open up terminal 
```
lsusb
```

post output and I will look for you.

---

### Post by BentSlightly on 2009-01-28
I am in the exact same position as the original poster, minus being an a programmer. This is simply not making sense, even Ubuntu's Webcam Forum has a sad face when:( it mentions this issue. 

Gentlemen, anything you discover will be greatly appreciated. 

And thank you in advance. 

Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:0704 Hewlett-Packard DeskJet 825c
Bus 001 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
pat@pat-desktop:~$

---

### Post by teaker1s on 2009-01-29
is the webcam attached to a usb port as all I see is trackman wheel, which I'm guessing is a mouse

---

### Post by BentSlightly on 2009-01-29
You are correct, only the mouse is showing up.

---

### Post by teaker1s on 2009-01-29
From the keyboards and keycodes I have played with- no response generally means kernel cannot see it.

```
dmesg | tail
``` plug and unplug cam, any response?

I think you will need a kernel module to enable it if kernel doesn't respond.

as for question on cam that does work and cheap
[http://ubuntuforums.org/showthread.php?t=1024298](http://ubuntuforums.org/showthread.php?t=1024298)

---

### Post by alessandro57 on 2009-01-30
> **ShaddamIV said:**
> After searching this forum and the Internet, reading many post and tutorials, I am still back to square one.

None of them are made for new users (from my point of view).
And most of the solution found applied to older version of Ubuntu.

I tried to compile the latest version of gspca by following a tutorial, then tried to repair the errors in the code with a patch from someone who wrote an article about it.

Still get plenty of errors while trying to compile it.
I am a c++ programmer but repairing this code is beyond my comprehension.

Is there an easier way? Like downloading a binary of the driver?

The problem is that it does not compile on Intrepid Ibex. Is it?

Is there a webcam that I can buy that would work automatically in Intrepid Ibex?

I bought this camera because some people wrote that it was compatible with Linux? Guess "compatible" has not the same meaning in the Linux world.

Same problem, i couldn't solve it but i think to have understood the cause:
we cannot compile gspca because in the Intrepid, it is already in the kernel, and it would be good if it worked, but it doesnt!!!!! In Feisty it worked and in Intrepid it doesnt!!
If i have well understood we have to wait for 9.04.......
A lot of cams doesnt works even if they should. Check posts about cams and u can easily realize it.

---

### Post by BentSlightly on 2009-01-31
It's not as if people are not trying. it is the fact that the person who found the marked "solution" on Bug report, didn't bother to use any form of coherance in his explination. Big jumps in coding that did not tie together, not good.

---

### Post by BentSlightly on 2009-01-31
This blogspot allowed me enough info to successfully navigate the steps through the terminal for the "offical solution" offered by Bug Report. This seems to work for some people, so I felt that a bit of clarity would be helpful for some since this seems like a widespread problem. Alas, it did not work on my machine, but here you go.

link to blogspot: [http://ztatlock.blogspot.com/2008/11/logitech-quickcam-in-ubuntu-810.html](http://ztatlock.blogspot.com/2008/11/logitech-quickcam-in-ubuntu-810.html)


Enter all of these steps into your terminal that are in quotes:


> wget [http://people.atrpms.net/~hdegoede/libv4l-0.5.0.tar.gz](http://people.atrpms.net/~hdegoede/libv4l-0.5.0.tar.gz)
> tar xvzf libv4l-0.5.0.tar.gz
> cd libv4l-0.5.0
> make
> sudo make install
> export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so

Then according to the general info from various sources, test your webcam app of choice. (It didnt work for me in Ekiga, Skype, or Cheese).


 > echo export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so >> ~/.bashrc


If it works for you let me know, I'll have more info in a bit.

---

### Post by BentSlightly on 2009-01-31
pat@pat-desktop:~$ dmesg | tail
[   52.926634] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   63.508014] eth0: no IPv6 routers present
[  599.291660] UDF-fs: No VRS found
[  631.488457] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
[  667.275082] ppdev0: registered pardevice
[  667.320168] ppdev0: unregistered pardevice
[  668.465068] ppdev0: registered pardevice
[  668.512182] ppdev0: unregistered pardevice
[  669.540378] ppdev0: registered pardevice
[  669.588029] ppdev0: unregistered pardevice
pat@pat-desktop:~$

---

### Post by BentSlightly on 2009-02-01
I filed a bug report. 

[https://bugs.launchpad.net/ubuntu/+bug/324135](https://bugs.launchpad.net/ubuntu/+bug/324135)


Edit: Signing off, and heading for the tub!

---

### Post by BentSlightly on 2009-02-03
Fixed it!

I read on the Skype Forum that merely changing to a different USB port may solve the problem. That fixed it immediately. 

I feel like a putz for missing the easy fix, but I am definitely not regretting the journey. 

The apathy and overall lack of communication in here has been shocking yet fulfilling. Hopefully someone will find this thread and it will help them out. 

Signing off and heading for the tub, with a total boner. 

:popcorn:

---

