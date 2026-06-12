---
title: "Philips spc230nc webcam in Jaunty"
date: 2009-07-11
forum: Hardware
---

### Post by matrixblue on 2009-07-11
I can't seem to get this webcam (Philips spc 230NC) working under Jaunty but it worked fine in Intrepid.

I installed (with some difficulty using a patch) the gspca modules but nothing changed. Easycam doesn't work in this version either.

lsusb show the cam listed as:

Bus 002 Device 003: ID 093a:262c Pixart Imaging, Inc.

Can anyone point me in the right direction?

---

### Post by palimmo on 2009-07-19
> **matrixblue said:**
> I can't seem to get this webcam (Philips spc 230NC) working under Jaunty but it worked fine in Intrepid.

I installed (with some difficulty using a patch) the gspca modules but nothing changed. Easycam doesn't work in this version either.

lsusb show the cam listed as:

Bus 002 Device 003: ID 093a:262c Pixart Imaging, Inc.

Can anyone point me in the right direction?

Same problem! :(

---

### Post by matrixblue on 2009-07-19
I solved this problem with some instructions I found on the Kubuntu Forums:

Download [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) and save it to your Desktop
Open Terminal
cd /tmp
sudo mkdir gspca
cd gspca
sudo cp ~/Desktop/gspca-b9f77fa3c506.tar.bz2 .
Note 1:  you can use the Tab key to complete the name of a file after entering the first few letters (paying attention to case)
Note 2:  there is a period after a single space in the command -- that tells the "copy" command (cp) to copy the file to the current directory.
sudo tar -xvf gspca-b9f77fa3c506.tar.bz2
cd gspca-b9f77fa3c506/
sudo make
sudo make install
Now the package should be compiled and installed.
Now you install the libv4l-0 package with
sudo apt-get install libv4l-0
And let's install camorama while we're at it, for testing purposes:
sudo apt-get install camorama
So, you are now finished compiling and installing.  You want to see if you camera works?  Assuming your webcam is connected:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
If camorama pops up and you see yourself, you win!   Wink
The little script that I made can be copied into kate and then you can save it in your home directory as "webcam" or something like that.  Before you run it the first time, you have to make it executable with
chmod +x webcam

Note: Use LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype to run skype with video

Hope this helps!!!

---

### Post by palimmo on 2009-07-20
> **matrixblue said:**
> I solved this problem with some instructions I found on the Kubuntu Forums:

Download [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) and save it to your Desktop
Open Terminal
cd /tmp
sudo mkdir gspca
cd gspca
sudo cp ~/Desktop/gspca-b9f77fa3c506.tar.bz2 .
Note 1:  you can use the Tab key to complete the name of a file after entering the first few letters (paying attention to case)
Note 2:  there is a period after a single space in the command -- that tells the "copy" command (cp) to copy the file to the current directory.
sudo tar -xvf gspca-b9f77fa3c506.tar.bz2
cd gspca-b9f77fa3c506/
sudo make
sudo make install
Now the package should be compiled and installed.
Now you install the libv4l-0 package with
sudo apt-get install libv4l-0
And let's install camorama while we're at it, for testing purposes:
sudo apt-get install camorama
So, you are now finished compiling and installing.  You want to see if you camera works?  Assuming your webcam is connected:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
If camorama pops up and you see yourself, you win!   Wink
The little script that I made can be copied into kate and then you can save it in your home directory as "webcam" or something like that.  Before you run it the first time, you have to make it executable with
chmod +x webcam

Note: Use LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype to run skype with video

Hope this helps!!!

And what about colours?

---

### Post by matrixblue on 2009-07-20
Colors?

---

### Post by physeetcosmo on 2009-07-23
All,

Can I assume that the Philips SPC611NC will have similar problems in 9.04?

---

### Post by matrixblue on 2009-07-23
I don't know

---

### Post by widebluecraig on 2009-09-02
Did this work for anyone?

---

### Post by physeetcosmo on 2009-09-02
I never bought the cam, after not hearing a response for over a month. No results to give. Sorry!

---

### Post by matrixblue on 2009-09-02
> **widebluecraig said:**
> Did this work for anyone?

Yeah, it worked for me

---

### Post by scpetand on 2009-10-13
It works but:
-The frame rate is about 4 sec/pic, (yes it takes a picture every 4 second)
-No color, just blue
-The resolution is crap

---

### Post by no2498 on 2010-01-24
i hope you get this in an email
get cheese and wxcam programs
to see the cams that this  did not help

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
after it comes on you have something to work with

---

