---
title: "trying to access pictures on cellphone"
date: 2009-01-17
forum: Hardware
---

### Post by digitalramble on 2009-01-17
OK.  I have a motorola z6c and what I would really like to do is access the pictures and text messages on it.  I've actually been poking at this from a couple of angles, but not been successful.

*Ideally* I'd mount this sucker as a usb mass storage device and just grab the folder with the pictures and the folder with the text messages.  Of course, what we want and what we get can be two different things :)

Firstly, I set it up to recognize the motorola, but as usbserial.  I think this means I can NOT access it as a storage device, but only to connect like I'm going to call?

Basically, I used lsusb to see what I had, and created the file /etc/modprobe.d/motorola_ve.options with

alias usb:v22B8p2B24* usbserial
options usbserial vendor=0x22b8 product=0x2b24

in it.  At this point, kmobiletools seems to think it's there, and seems to correctly figure it's battery charge and signal strength.  However, try as I might, I can't get it to see any of the text messages (SMS) that are stored on the cellphone.  And there don't seem to be options to find the photos, anyway.

So my question is, how would I reconfigure this thing to NOT be a usbserial but to be a usb mass storage device?  Is that possible?  Failing that, is there a better/different program that would let me pull the photos and texts off the phone?  

It's really funny; the windows version (Motorola Phone Tools) is extremely lame (gives me the text messages with no timestamp on them...!) and doesn't seem to know anything about photos either ](*,)  But since the windows computer is my work computer, I'd prefer to do this on linux (my home computer).

Thanks for any tips, explanations (even if it's no you can't do that :(  ) and so on...

---

