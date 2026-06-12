---
title: "Just Installed Ubuntu...Having a Few Problems Though"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by mrxtambourineman on 2008-01-11
I have just installed Ubuntu 7.1 for the AMD 64. I have a few problems however. When I was installing I got the error: "failed to connect to socket /tmp/dbus-AxuiW4v9eR". I have no idea what this means or if it's related to my problems. I'm using a Toshiba A215 laptop for the install if this helps. 

The main problems I'm having are:

1. I have a Radeon x1200 and the drivers are restricted, but it won't let me enable them. When I try to enable them it tells me that "xorge-driver-fglrx is not enabled." I'm not sure how to do this.

2. My sound is not working at all. I have a Realtek High Definition Audio integrated with my motherboard.

3. My wireless card is not working/not recognized. I am using a Atheros AR5007EG. When I go to the network icon next to the date and time it does not allow me to choose wireless as an option.

My final question is are these problems unique to ubuntu 7.1 for the AMD 64 architecture. Would I be better off installing the 32 bit version instead. It wouldn't be a big loss because I just installed ubuntu about 30 mins ago. Thank you for your time. I look forward to feedback.

Eric

---

### Post by Scheater5 on 2008-01-11
All I have is an answer to your last question.  There was once a big deficiency in the number of packages available for the 64 bit version, but that is no longer the case.  I have not had any problems with the 64 bit version, and would recommend it.  However, do note that, in general, everyday use will not make much use of the 64 bit version, and you're not likely to see much of a performance increase unless you do process-intensive activities.

---

### Post by limbourg31 on 2008-01-11
Generally, the 32-bit install is less prone to many errors. For the wireless card I recomment you check if it is supported in the guide at the ubuntu site, and if not, install ndiswrapper. If it isn't supported in ndiswrapper either, you really can't install it unless you want to write your own drivers. Sound ought to work with Realtek, but again check that it is supported. ATI has recently released drivers for linux, so head over to their site and try and use it ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)). See if that works

---

### Post by mrxtambourineman on 2008-01-11
I'm a linux newb so I really don't understand the installation instructions for ndiswrapper. Its way over my head.

Eric

---

### Post by Yellow Pasque on 2008-01-11
Those are all hardware driver problems and would exist in the 32-bit version as well. Definitely keep the 64-bit version if your processor is capable of it. The 64-bit version boots a bit faster, builds software faster, does multimedia tasks MUCH faster and just has more punch in general. 

1. For the X1200, I would suggest downloading the latest drivers from ATI instead of using the old Ubuntu ones. Follow Method2 in this helpful HowTo: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Here is a good page for those other problems you encountered:
[http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10](http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10)

---

### Post by carandraug on 2008-01-13
> **mrxtambourineman said:**
> 1. I have a Radeon x1200 and the drivers are restricted, but it won't let me enable them. When I try to enable them it tells me that "xorge-driver-fglrx is not enabled." I'm not sure how to do this.

2. My sound is not working at all. I have a Realtek High Definition Audio integrated with my motherboard.


About the sound, you probably do have sound but it's just not getting to the columns. First download the linux drivers for your sound card from the realtek website and install them. After that, open the terminal and insert

> sudo gedit /etc/modprobe.d/alsa-base

it will open a document. Add a line at the end with

> options snd-hda-intel model=z71v position_fix=1 

Save and exit. Restart and next time you go to control the sound try changing the headphones. Worked for me.


If you want to use the restricted drivers you have to first go to System > Administration > Software souces. In the first tab (Ubuntu software) there's a lot of check boxes. Put a check on the first four "Canonical-supported....", "Community-maintained.....", "Proprietary drivers...." and "Software restricted by....". Next time you probably won't get the "xorge-driver-fglrx is not enabled" error.

---

