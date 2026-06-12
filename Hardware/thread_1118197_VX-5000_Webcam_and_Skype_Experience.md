---
title: "VX-5000 Webcam and Skype Experience"
date: 2009-04-06
forum: Hardware
---

### Post by LIB53 on 2009-04-06
I recently bought a VX-5000 webcam and it worked perfect right out of the box. When I installed Skype, i had to open the options and set a couple video and audio settings to use the VX-5000, but after that it worked perfect. This a great webcam, but it is not listed here:[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams). Is there anyway that i can add this webcam to the list?

Note: I'm on Jaunty, so i don't know how it works in previous versions, but a bit of googling found the same results in Intrepid.

---

### Post by axmukher on 2009-04-25
Try this mantra:

First make sure "Skype" and "v4l1compat" are installed ...

Then -

System > Control Centre > Personal > Startup Applications

(Previously till Hardy it was System > Preference > Session)

If Skype exists in the list of Startup Applications, then select Skype, click on "Edit" button and change the "Command" line to the following: 

sudo LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

If Skype does not exist in list of startup applications, click on the "+Add" button and add one with the above "Command" line.

Pray now to the great Lord Shiva and your webcam will work.

---

