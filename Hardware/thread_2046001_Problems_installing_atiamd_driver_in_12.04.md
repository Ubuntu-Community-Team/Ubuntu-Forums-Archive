---
title: "Problems installing ati/amd driver in 12.04"
date: 2012-08-22
forum: Hardware
---

### Post by geirmash on 2012-08-22
Hi there! The ati graphics-card i have installet in my laptop is HD 5470.
I have installed the drivers both from the repositories AND from System Settings -> Additional Drivers -> ATI/AMD proprietary FGLRX graphics driver. I can locate the Catalyst Control Center, but i cannot open it. I get an error saying:

"There was a problem initializing Catalyst Control Center Linux edition.
It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not
functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig."

I have tried to re-install the drivers several times, and still the same error occurs.
If i try to run "fglrxinfo", i just get:
"geirmash@ubuntu:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12"

I have tried everything people have suggested in this thread: "http://ubuntuforums.org/showthread.php?t=515573&highlight=install+ati+drivers", but obviously none of the methods work.

So if anyone have a solution for installing the drivers and make them work, please reply! I do not want to go back to Windows just because of this :P

I only use my laptop for development and therefore do not need to run heavy graphics.
I first needed the drivers when i tried to run an android project in eclipse and the graphics could not run because the driver for the graphics card was not installed.


Other guides and solutions i have tried:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[http://www.techlw.com/2012/04/install-ati-catalyst-123-drivers-on.html](http://www.techlw.com/2012/04/install-ati-catalyst-123-drivers-on.html)


If specific information(about errors etc) is needed, it will be posted.

---

### Post by Sergey V Smb on 2012-09-06
I think these two posts can help you sort your problem out: [the first]("http://gumz-ex-press.com/2012/ubuntu-12-04-working-hybrid-graphic-ati-radeon-hd6470m-installation/") and [the second]("http://askubuntu.com/a/98851").

They both describe the same problem and equivalent solution and helped me to re-install the driver on my x64 Ubuntu 12.04 machine (ProBook 4530s). 

I hope it helps you.

---

### Post by QIII on 2012-09-06
Which method did you use from the binary how-to wiki.

The first of the resources suggested by sergey will be of little use if you don't have hybrid graphics and the Askubuntu link is for an older driver.

Could you give me a little more information about your machine?

By the way, the message you are getting is most often caused by failing to initialize xorg.conf.

---

