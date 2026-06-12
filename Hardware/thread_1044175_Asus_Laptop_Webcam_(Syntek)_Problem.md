---
title: "Asus Laptop Webcam (Syntek) Problem"
date: 2009-01-19
forum: Hardware
---

### Post by Camelopardalis on 2009-01-19
Hi everyone,

My first post in these forums, hopefully all goes well!

This is obviously a common problem judging my the amount of threads here and elsewhere on the net.  Each one of those threads has helped me understand the problem more but none have got me over the finish line.  I apologise now if this has been addressed too many times already and I was unable to find the answer.

So... The webcam does not work.  

Some details to start with;

Asus F5Rseries Laptop
Ubuntu 8.10 dual boot with Vista
lsusb gives the following;

```
 lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 004: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I also followed this [guide]("http://ubuntuforums.org/showthread.php?p=3437115") successfully (by that I mean no errors) but still my webcam will not work.

I have also tried EasyCam2 to no avail.

I have the following installed and tried the cam with them all;
Cheese
Camorama
XawTV
VLC
aMSN

I will add more things I have tried as I remember, or try.

It's no the end of the world, I wouldn't use it much anyway, but I have always eventually found solutions to problems as I learn to use Linux.  In fact this is the first time I have asked a question in any Linux help forum (usually my questions are answered by reading others problems and subsequent solutions).  I am still very much an inexperienced Linux user when it comes to problems such as this, but have been using various distros for a couple of years.

Ok, sorry that was a bit long!  Thanks in advance.

Cheers.

---

### Post by sojyujai on 2009-01-27
Hi There's a known bug with the Syntek drivers in Intrepid - you can see the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123")

Down in the comments a fellow named Jim Lieb posted a link to some kernels he compiled containing the updated syntek drivers.  I gave the i386 kernel a try and it so far seems to have solved my problems - the webcam on my asus f3jp laptop seems to be working with cheese and skype.

You'll notice further down in the comments it's not working for everyone but it might be worth a try for you.

---

### Post by Camelopardalis on 2009-01-27
Thanks sojyujai, I will have a look and see how I go.

Cheers.

---

### Post by Camelopardalis on 2009-01-27
Didn't work for me, that is the first time I have done anything with the kernel, but I assume it installed correctly as I was able to select the new kernel when I rebooted.

Still, it appears that people are working on it and hopefully it won't be long before its easily sorted out.  Thanks again for the link and I will continue to monitor progress.

---

### Post by FreeMinded on 2009-04-28
Hello all,
has anyone been able to fix the web cam problem in Jaunty? 

Any help would be appreciated!

---

### Post by prezeus on 2009-05-25
I still searching for a solution in jaunty too

---

### Post by noobi_agocs on 2009-07-07
Hi everyone!


I had the same problem with my webcam. I googled around the web every evening after work to solve the problem. FINALLY it works for me...
:guitar:

I have an ASUS F5VL series laptop, and i'm using Ubuntu 9.04

1.
So, maybe the most important thing is, that you need to download the stk11xx Syntek driver, **BUT the 1.4.0 release**! This is very important! I had no chance to install the 2.0.0 release...

Here you can download it: [http://sourceforge.net/projects/syntekdriver/](http://sourceforge.net/projects/syntekdriver/)

2.
Then, I followed this HOWTO: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

This is a french HOWTO (i dont speak french), but it's excellent. I followed it step by step, EXCEPT that I didn't donwloaded the latest syntek driver using the svn command.

Later I found an english HOWTO: [http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html](http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html)

3.
After this i installed video4linux using the command:
$ sudo apt-get install v4l-conf

4.
The last step was to add my user nick to a group that is allowed to use the webcam. The command is:
$ sudo adduser USERNICK video

Then RESTART...


After this i've tried the webcam whit: Camorama, aMSN and Skype. All of them recognized whitout any problem the webcam.


I hope this helps you a little...
Have a nice day! Cheers!

noobi

----------------------------------------------------
ASUS F5VL Series, Intel Core2Duo T5250, ATI X2300

---

