---
title: "Dell Inspiron 1525 laptop webcam installation"
date: 2009-10-30
forum: Hardware
---

### Post by stoneseal on 2009-10-30
My Dell Inspiron 1525 laptop have embedded Creative Live Avatar webcam. Please help to find driver and software to make using this webcam. It was the problem for ubuntu 9.04 also. Thanks for solutions.

---

### Post by emergingtechnologies on 2010-01-24
> **stoneseal said:**
> My Dell Inspiron 1525 laptop have embedded Creative Live Avatar webcam. Please help to find driver and software to make using this webcam. It was the problem for ubuntu 9.04 also. Thanks for solutions.

I'm a total noob but I just entered the following code and got the web cam on my 1525 working.  Hope it works for you:


Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo



Try it.

---

### Post by achadweh on 2011-05-08
> **emergingtechnologies said:**
> I'm a total noob but I just entered the following code and got the web cam on my 1525 working.  Hope it works for you:


Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo



Try it.

thanks,,, it worked for me too on Ubuntu 11.04

---

### Post by nazarete on 2011-08-01
my web cam is not working any more what I can do?
 even the blue LED light also not working, any help please, I'm using vista copy but I installed the crack and it's looks like original, but my problem I guess becouse of windows ubdates,tell me please
 
 how to add and where to add
 
sudo modprobe uvcvideo
sudo rmmod uvcvideo

---

### Post by popper668 on 2011-10-05
> **emergingtechnologies said:**
> I'm a total noob but I just entered the following code and got the web cam on my 1525 working.  Hope it works for you:


Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo



Try it.


thank you. very effective.

---

### Post by Pynalysis on 2011-10-05
> **nazarete said:**
> my web cam is not working any more what I can do?
 even the blue LED light also not working, any help please, I'm using vista copy but I installed the crack and it's looks like original, but my problem I guess becouse of windows ubdates,tell me please
 
 how to add and where to add
 
sudo modprobe uvcvideo
sudo rmmod uvcvideo

Those commands can be executed in Ubuntu via the terminal window.

---

### Post by the_funtom on 2011-11-21
> **nazarete said:**
> my web cam is not working any more what I can do?
 even the blue LED light also not working, any help please, I'm using vista copy but I installed the crack and it's looks like original, but my problem I guess becouse of windows ubdates,tell me please
 
 how to add and where to add
 
sudo modprobe uvcvideo
sudo rmmod uvcvideo

Hi guys I had an issue with my webcam on my 1525, its resolved but the colors are all weird....and distorted. Can someone please help!

---

