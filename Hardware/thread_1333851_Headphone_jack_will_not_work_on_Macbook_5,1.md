---
title: "Headphone jack will not work on Macbook 5,1"
date: 2009-11-21
forum: Hardware
---

### Post by rashhashan on 2009-11-21
I installed 9.10 on my Macbook 5,1 and my headphone jack doesn't transmit sound to my speakers. The internal laptop speakers work fine but my headphone jack does not. I have read many forums and tutorials on how to install all drivers and get all hardware working for 9.10 on a mac but i cant figure this one out. plz respond

---

### Post by BaroqueBloke on 2009-12-06
I have the same problem with my 1,1 macbook.  Im running 9.10 and cant find a work around.  Any help is much appreciated.  

Cheers!

---

### Post by ahorriblemess on 2009-12-08
I have a Macbook 1,1 running Karmic as well. The instructions are easily found on google: 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I chose the closest thing to what I have. 

But anyway, I installed alsa with the terminal:

sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

sudo dpkg-reconfigure alsa-source   (on this one I just went with the dafault choices)

sudo module-assistant a-i alsa-source


After all that was finished (takes a while) I used Ubuntu Software Center from the menu, searched for and installed Gnome Alsa Mixer, and noticed "Speaker" was muted, so I unmuted it. Everything worked after that.

---

### Post by theTailor on 2010-02-02
I had the same problem on my macbook2,1. After reead what ahorriblemess wrote I just tried installing the Gnome ALSA mixer and unmuted the speaker that was muted and everything was fine. I didn't have to install or configure any other packages. (I just have the out-of-the-box install of 9.10.)

---

