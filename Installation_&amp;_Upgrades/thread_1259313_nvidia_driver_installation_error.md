---
title: "nvidia driver installation error"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by vikramk.ibs on 2009-09-06
I have ASUS M2N68-AM motherboard running on Athlon64x2 (7750) & With Ge-Force7 series on board. I have Ubuntu 9.04, but unable to install the N-Vidia Driver.

I tried to activate it in "System=> Administration=> Hardware Drivers" but its not detecting any hardware (note - this is after Fresh Installation, before running any system update)

I downloaded linux drivers from n-vidia website with the file named **NVIDIA-Linux-x86-185.18.36-pkg1.run** 

I tried to install this file with command
> sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run

The error appears like this
[IMG]http://i32.tinypic.com/29xx4d2.jpg[/IMG]

:confused:
Can anyone please help me out???

---

### Post by pedja_portugalac on 2009-09-06
Read my post here [http://ubuntuforums.org/showthread.php?t=1253906](http://ubuntuforums.org/showthread.php?t=1253906)

You should download driver for 64 bit processors, it's on my post.

---

### Post by vikramk.ibs on 2009-09-06
> **pedja_portugalac said:**
> Read my post here [http://ubuntuforums.org/showthread.php?t=1253906](http://ubuntuforums.org/showthread.php?t=1253906)

You should download driver for 64 bit processors, it's on my post.

Thanks a lot buddy..

I'm downloading it.. will put the result afterwards...
:)

---

### Post by realzippy on 2009-09-06
Log out.Hit alt+ctrl+F3
A terminal opens.Log in there with username/password.
then stop xserver by:

[B]sudo /etc/init.d/gdm stop
[/B]
Then go to your nvidiadriver;assuming it is on your desktop,type:

**cd Desktop**

Then:

[B]sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
[/B]
Answer all questions with "yes".

**sudo reboot**

"You should download driver for 64 bit processors"   **??????**
**64 bit driver is only needed when running 64bit ubuntu!**Do you?
I am shure you do **not**,otherwise the 32 bit nvidia installer would have complained about "wrong architecture" !!!

---

### Post by vikramk.ibs on 2009-09-06
> **pedja_portugalac said:**
> Read my post here [http://ubuntuforums.org/showthread.php?t=1253906](http://ubuntuforums.org/showthread.php?t=1253906)

You should download driver for 64 bit processors, it's on my post.

I tried the installation u've given (64 bit)
the error is
[IMG]http://i27.tinypic.com/292pq87.png[/IMG]


:confused:

---

### Post by realzippy on 2009-09-06
Yes,as I mentioned before,you are running 32 bit!
Please test what I suggested,and delete that 64bit driver...and do not chmod 744 anything here...

---

### Post by vikramk.ibs on 2009-09-06
> **realzippy said:**
> Log out.Hit alt+ctrl+F3
A terminal opens.Log in there with username/password.
then stop xserver by:

[B]sudo /etc/init.d/gdm stop
[/B]
Then go to your nvidiadriver;assuming it is on your desktop,type:

**cd Desktop**

Then:

[B]sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
[/B]
Answer all questions with "yes".

**sudo reboot**

I will try it..

> **realzippy said:**
> "You should download driver for 64 bit processors"   **??????**
**64 bit driver is only needed when running 64bit ubuntu!**Do you?
I am shure you do **not**,otherwise the 32 bit nvidia installer would have complained about "wrong architecture" !!!


You are right that thing is not working

---

### Post by realzippy on 2009-09-06
...have a date in real life now...will be back in 2 hours.
Good luck!

---

### Post by vikramk.ibs on 2009-09-06
> **realzippy said:**
> ...have a date in real life now...will be back in 2 hours.
Good luck!

I did the same process, during which it asked me to download config file online. As my net is thru phone, I cannot connect to internet during log-out mode. 

It has given error msg about non-availability of internet connection, later setup went well, after installation, it asked to incorporate some module in startup -I given yes. 

After reboot, there was an error saying


> UBUNTU is running in low graphics mode
(EE) NVIDIA - failed to load the NVIDIA kernel module.
Please check your system kernel log for additional error messages.

Failed to load module 'nvidia' (Module Specific Error,0)

No Drivers available


After selecting use backup drivers, it restarted again. and the screen is again the old one.

My GeForce 7 series is showing 800x600 screen resolution. :(

I agained tried to activate the drivers (System-> Administration-> Hardware Drivers) it was showing the list, sayin drivers un-activated.
I clicked on activate button. (internet was on, during this time), it shown the dialog box "Downloading and Installing drivers 0%" after few minutes the error msg was 
[IMG]http://i31.tinypic.com/116mlhs.jpg[/IMG]


This is really baaaaaaaaaaad

---

### Post by realzippy on 2009-09-06
There is alberto milones script "envy"...
(installs nvidia)
think meanwhile it works under xserver.
Type in terminal (not log out):

**sudo apt-get install envyng-qt**

Search your menue for entry "envy",do not know where it will be,and
check if envy could do the job.

if all this does not work,there must be a way to set up your phone internet connection from the terminal without xserver.But first test envy please...

---

### Post by vikramk.ibs on 2009-09-06
> **realzippy said:**
> There is alberto milones script "envy"...
(installs nvidia)
think meanwhile it works under xserver.
Type in terminal (not log out):

**sudo apt-get install envyng-qt**

Search your menue for entry "envy",do not know where it will be,and
check if envy could do the job.

if all this does not work,there must be a way to set up your phone internet connection from the terminal without xserver.But first test envy please...

I will check it out....

Your are genius buddy.
I will try the envy and post my results..

Thanks a lot for your quick reply..

---

### Post by realzippy on 2009-09-06
If no luck with envy,have a look at:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/350776](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/350776)

They also had "jockey backend crash",some could fix it by disabling
the ubuntu CDROM as repository source in synaptic...
Try it.BTW,is your system updated meanwhile?

---

### Post by vikramk.ibs on 2009-10-06
> **realzippy said:**
> There is alberto milones script "envy"...
(installs nvidia)
think meanwhile it works under xserver.
Type in terminal (not log out):

**sudo apt-get install envyng-qt**

Search your menue for entry "envy",do not know where it will be,and
check if envy could do the job.

if all this does not work,there must be a way to set up your phone internet connection from the terminal without xserver.But first test envy please...

Envy loaded, now its improved with the resolution (1152 x 768)

Yet to try compiz, will put the results after that...

Thanks for envy idea...

HATS off to you buddy

---

### Post by vikramk.ibs on 2009-10-06
Envy resolved almost all the issues
now my Hardware driver is also showing the **activated** status

but still unable to save my nvidia settings, it says unable to create file xconf.backup file.

And Desktop effects and even compiz is not working

:(

can solution for this?

---

