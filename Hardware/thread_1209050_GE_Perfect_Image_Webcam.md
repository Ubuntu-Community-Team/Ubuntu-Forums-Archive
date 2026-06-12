---
title: "GE Perfect Image Webcam"
date: 2009-07-09
forum: Hardware
---

### Post by addimonk on 2009-07-09
I have a GE Perfect Image webcam and I am having problems with it. Whenever I use it half of it is green and there are all of these little lines. I can't find a driver for it anywhere. I'm a newb so please don't get to complex. When I do lsusb I get:

Bus 002 Device 002: ID 0c45:62e0 Microdia 

I have heard of lots of people having problems with "Microdia" Can anybody help me?

---

### Post by nowin4me on 2009-07-22
I have the exact same webcam and I am in the same boat as you :(.
Well I am going to do a bit more googling and see if I can find something for us.

---

### Post by rodspi on 2009-09-25
The webcam does work with Jaunty with certain programs.

Out of the box programs, guvcview and luvcview (with the maximum resolutions setting [1280x1024]).  guvcview is the most functional of the two programs.

Skype works when you edit the config.xml file to use the maximum and good framerate.  However, I have only tested skype on a gateway to acer netbook.  The video caused skype to crash after about a minute use. My googling revealed that for high resolution webcam and skype you 
need a fast dual-core processor and bandwith for high resoultion webcams.  They define high resolution as 640x480 or higher.

Haven't figured out how to get it to work with ekiga

The "cheese" application crash a lot.  If you can get the program to open and set the resolution to 1280x1024 before it crashes then it works.  However, the program will crash once you remove the webcam and reboot.  If you are using a netbook/notebook you will have find all cheese config file and maunuall delete them.  Then remove and reinstall program for the "cheese" program to work with built-in webcam.

Haven't figured out how to get it to work with VLC ans mplayer.

I'm hoping the lower resolutions issues are fixed in ubuntu 9.10/mint linux 9.10 currently running two netbook with mint linux and one desktop with ubuntu 8.10

---

