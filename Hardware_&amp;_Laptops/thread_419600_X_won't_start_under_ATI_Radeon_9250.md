---
title: "X won't start under ATI Radeon 9250"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ~SkyBlue~ on 2007-04-23
I have ATI Radeon 9250 and tried various drivers. So far I only got away with vesa driver, but I don't like it since it doesn't have any hardware accel. support.

I have tried the normal xserver ATI driver, the screen goes pitch black right after ubuntu loading screen, and system freezes

Also tried fglx 8.28.8 from ati.com (this is the relevant version for Radeon 9250), reconfigured xserver, and this time after a little flickering, an error msg pop-up saying it can't start X.

Here is link to my lspci, dmesg and Xorg.0.log :
[http://www.cse.unsw.edu.au/~gtan/errmsg/lspci](http://www.cse.unsw.edu.au/~gtan/errmsg/lspci)
[http://www.cse.unsw.edu.au/~gtan/errmsg/dmesg](http://www.cse.unsw.edu.au/~gtan/errmsg/dmesg)
[http://www.cse.unsw.edu.au/~gtan/errmsg/Xorg.0.log](http://www.cse.unsw.edu.au/~gtan/errmsg/Xorg.0.log)

Any help will be greatly appreciated

---

### Post by dorkobobsk8r on 2007-04-23
hmmm... looks like X is looking for /dev/input/wacom... try commenting out all sections relating to /dev/input/wacom in your /etc/X11/xorg.conf, then reboot...

---

### Post by ~SkyBlue~ on 2007-04-23
Apoligies, it seems I have posted irrelevant logs, here is the correct one

This error occured when I'm trying to start X using newest fglrx
[http://www.cse.unsw.edu.au/~gtan/errmsg/fglrx/xorg.conf.txt](http://www.cse.unsw.edu.au/~gtan/errmsg/fglrx/xorg.conf.txt) (the xorg.conf used)
[http://www.cse.unsw.edu.au/~gtan/errmsg/fglrx/Xorg.0.log.txt](http://www.cse.unsw.edu.au/~gtan/errmsg/fglrx/Xorg.0.log.txt) (the error log)

And thankyou for you suggestion above, but I don't think wacom is the problem. It's just an input driver for tablet PC. I had it working with vesa driver.

---

### Post by SquirrelHavoc on 2007-06-07
I am having the same exact problem with my PCI RADEON 9250, I get X initializing, then an error I can't decypher (new to linux, but used it before), then I get a black screen and system lockup. A while back I was looking into this and someone said to edit the xorg.conf file to do this and that to it, but I didn't know how from a shell prompt without emacs. Not really looking for someone to hold my hand through this, but I would like to get it running again, so since this thread just stopped, and the links to config/log files are now 404s, has this been rectified? If so, how?

PS Sorry for the run on sentences and poor english, I'm actually American, just a slow one :p

---

### Post by snama on 2007-06-11
dont use the newest fglrx driver for the radeon 9250 and earlier. support for these cards was dropped after the 8.28 release (correct me if iam wrong). i use a radeon 9250 and the open-source radeon driver works fine for me in feisty

---

### Post by Kubunteando on 2007-06-12
Snama is absolutely right.
For ATI Radeon card not supported after the 8.28 ATI proprietary drivers the Open Source drivers are the most stable ones plus allow you to run applications like Beryl, Google Earth for Linux, games like Regnum Online...

The most stable Open Source drivers with HW acceleration are the MESA 6.5.3, unfortunately not included in Feisty. Maybe someone should ask Ubuntu to include those...
For those you can check [www.mesa3d.org](www.mesa3d.org)

---

### Post by soul_motor on 2007-06-15
How do you get the files onto your computer?  I'm really new at Linux and haven't got a clue.  Thanks in advance.

---

