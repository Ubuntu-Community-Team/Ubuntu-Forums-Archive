---
title: "Cannot install Wacom Bamboo Pen CTL-460 on Ubuntu 9.10"
date: 2010-04-08
forum: Hardware
---

### Post by opensource-for-all on 2010-04-08
Hello all Ubuntu users out there.  As many of you know, installing Wacom tablets into Linux is a complicated process.  I have been trying to get mine working, but I can't even get the mouse to move.  They say Wacom tablets are supposed to work out of the box on Ubuntu, but mine doesn't work at all. I've tried to install according to the instruction on the Linux Wacom Project page, but I'm always stuck in the middle because my computer couldn't find the file wacom.ko in this step: [http://linuxwacom.sourceforge.net/index.php/howto/testwacom](http://linuxwacom.sourceforge.net/index.php/howto/testwacom)

I'm still a new linux user, so I'm still pretty unfamiliar with using terminals and command codes.  Any help would be appreciate it :)

I'm using Ubuntu 9.10

---

### Post by tnaia on 2010-04-08
I have been having a similar problem.

I tried some different approaches suggested on the forums and other pages... but not being myself an experienced user, ended up just learning - the hard way - that is it is important to document what I do. (I ended up with a broken user account, fixed recently, due probably to the wrong mixing of suggestions.)

I'm planning on trying again this weekend. As soon as I have any results I'll report to the forums.

---

### Post by Ayuthia on 2010-04-08
You might try this [post]("http://ubuntuforums.org/showpost.php?p=9091755&postcount=1008").  Your device is still pretty new so the current stable driver does not support it yet.  However, the ones that are currently in development does recognize your device.  There is still work being done for it, but it seems to be working pretty well for the pen devices.

---

### Post by Jem Masters on 2010-04-08
Hi, I bought today Wacom Bamboo pen & touch, but I was following the link that Ayuthia posted but theres a broken link (page cannot be found)


> We are going to test out the 0.8.5-10 version that now contains ob1kenobi's patches.
Option A
For now I have archived this version because of a recent release so you can download it here.
Unpack the source:

any idea where I can find a working link or something similar to make work the Bamboo?

---

### Post by Ayuthia on 2010-04-09
Please try [0.8.5-12]("http://downloads.sourceforge.net/project/linuxwacom/linuxwacom-dev/0.8.5-12/linuxwacom-0.8.5-12.tar.bz2?use_mirror=superb-sea2").  You will need to replace 0.8.5-10 in the first post with 0.8.5-12.  Please let me know if that works.  If it does, I will update the thread so that it points to the newer release.

The linuxwacom site will replace the development versions whenever they create a new one.  The older one disappears.

---

### Post by opensource-for-all on 2010-04-09
Oh my goodness, thank you Ayuthia! My tablet is working now! 

Right-clicking works, but no grabbing with the first button.  Also no pressure sensitivity...

Any advice on how to get the pressure on?

---

### Post by Jem Masters on 2010-04-09
Compile and install:
Code:
> make clean
make distclean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.27/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/
sudo depmod -a

Theres no wacom.ko in 2.6.27 in 'src' for linuxwacom-0.8.5-12, any idea where i can get it? or someone that can post it?

---

### Post by Ayuthia on 2010-04-10
> **opensource-for-all said:**
> Oh my goodness, thank you Ayuthia! My tablet is working now! 

Right-clicking works, but no grabbing with the first button.  Also no pressure sensitivity...

Any advice on how to get the pressure on?

For GIMP, you can try going into Edit->Preferences->Input Devices and enable the stylus through that portion.  Otherwise, I am not for sure of other applications that have pressure sensitivity.

---

### Post by Ayuthia on 2010-04-10
> **Jem Masters said:**
> Compile and install:
Code:


Theres no wacom.ko in 2.6.27 in 'src' for linuxwacom-0.8.5-12, any idea where i can get it? or someone that can post it?

I have not checked out 8.5-12 yet, but I thought that I saw that it can be found in the 2.6.30 folder.  Does that folder exist?

EDIT:  You might check out 0.8.6.  It looks like there is now a Production release.  It also seems to have a 2.6.30 folder out there.

---

### Post by Jem Masters on 2010-04-10
This what inside the 2.6.27 in both 8.5.12 & 8.6 


Makefile.in
wacom.h
wacom_sys.c
wacom_wac.c
wacom_wac.h

theres no wacom.ko or do I need to substitute .ko with another of this? I have no idea on what I'm doing wrong, I'm just copying and pasting.

---

### Post by Ayuthia on 2010-04-11
> **Jem Masters said:**
> This what inside the 2.6.27 in both 8.5.12 & 8.6 


Makefile.in
wacom.h
wacom_sys.c
wacom_wac.c
wacom_wac.h

theres no wacom.ko or do I need to substitute .ko with another of this? I have no idea on what I'm doing wrong, I'm just copying and pasting.

Is there a 2.6.30 directory?  I think that is where the wacom.ko file will end up.

---

