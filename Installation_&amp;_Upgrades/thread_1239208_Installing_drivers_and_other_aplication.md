---
title: "Installing drivers and other aplication"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by chuxije on 2009-08-13
Hello,

I apologize in advance for asking for something that has probably been asked for 100000 times but there is 1000+ pages of topics and I not able to find the exact information that I need, so here it is.

I am new to Ubuntu. I have been using Linux for some time, but everything was mostly set up for me and I used only basic functions (such as, go to Internet, use terminal for something simple etc).

I need help in following. I have that famous Linux unsupported lap top Fujitsu Siemens Esprimo V 5535 which has that stupid Grafic card SIS Mirage 3+ (V670 or smth like that).

I wanted to know the following. If I ever find the driver for this card or accelerator (because now everything is showing up very slow, in resolution 1024x768 , not in the right resolution - i need wide screen resolution, and it is bad so I use windows for now ) how do I install it. What are the ways to do it (because I haven't seen or couldn't find hardware management  where I can add a driver) , and how are they supposed to look like (some source code, some installation package or a file to copy and where in Linux are located the drivers) . 

Also , what are basic ways to install software in Linux. I know that some are supposed to be compiled, some to just double clicked and so on, so what are the ways to do this  in Linux, and particularly Ubuntu.

And the last. Before few years, I had a music player (very simple one) XMMS. I know that it is basically a copy of Winamp, but I like it because it is simple and it does 2 basic and only functions that I want. First is to play music (in a good quality), without asking me a lot, and second is easy jumping to songs and making cues. Now, on this version it is not working for me, so does anybody has any version of it that works correctly, or something very simple to XMMS and how do I install it.

Thank you in advance!

---

### Post by chuxije on 2009-08-13
Hello :) 

Well I have found a very good solution for my problem with graphic card. I have downloaded this driver (in attachment) which was made by some Linux user (thank him for this a lot). As I understood it has just 2D and no 3D acceleration what ever that it means, but the thing is , I finally have my correct resolution and the image is now fine (it is not slow etc..)

Also you have to configure your xorg.conf the device section to this : 

Section "Device" 
Identifier "Device0" 
Driver "sis671" 
EndSection

and it works fine. Just double click the driver .deb package and it is ok.

Still I would really like if somebody gave me a little introduction on how to install/uninstall things in Ubuntu, all of the methods that there are , and what is the solution for XMMS.

Thank you !

---

### Post by chuxije on 2009-08-13
Well , for all those who want to use XMMS or similar to that, I have found this web site : [http://tuxarena.blogspot.com/2009/04/how-to-compile-and-install-xmms-in.html](http://tuxarena.blogspot.com/2009/04/how-to-compile-and-install-xmms-in.html)

Enjoy :)

---

### Post by Mark Phelps on 2009-08-14
Looks like you lucked out with the .deb file.  Those are self-installers, serving much the same function as the MS Windows .msi files.

As to XMMS, I use that also but stumbled across Audacious.  It is not nearly as complex as some of the other Linux audio apps but it also supports XMMS skins. You should Google for it and try it.

---

### Post by chuxije on 2009-08-16
Hi :) 

Thanks for the reply ! Audiocast is perfect for me, because it is simple, and I do not like to bother much while I enjoy music.

Although I do have one question. Bearing in mind that I am completely new in this, what is the software for editing audio and video. For example is GIMP as good as photoshop, or how to convert audio fails, grab a CD or just cut some part of the song.. ? Do you have any suggestions where should I look for this ? 

Thanks!

---

