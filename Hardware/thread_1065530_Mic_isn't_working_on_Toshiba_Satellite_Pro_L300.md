---
title: "Mic isn't working on Toshiba Satellite Pro L300"
date: 2009-02-10
forum: Hardware
---

### Post by HistoryMac on 2009-02-10
Mic isn't working on Toshiba Satellite Pro L300!!! Aaaaaaah!!!!!

When I try to record sound using the mic that's built into my TOSHIBA Satellite Pro L300, it doesn't work. Skype 2 can make calls, but the person on the other end can't here me :confused: (I'd imagine it's a driver issue)

I'm pretty new to Ubuntu so explain things as simply as possible :) 


Running Ubuntu 8.10 (Intrepid Ibex) on
TOSHIBA Satellite Pro L300
2GB RAM
120GB HDD
2.0Ghz Intel Pentium Dual Processor

Thanks!

---

### Post by HistoryMac on 2009-02-11
bump. Please help!! :( Pleeeeaaaase!!!!!!!!!!!!

---

### Post by HistoryMac on 2009-02-13
Bumpity bump.

---

### Post by michilen on 2009-06-19
Ya, the same thing is happening to me with a Toshiba satellite L35.  I've tried different microphone but it doesn't work.  SOMEONE PLEASE HELP!  OH, by the way i love Ubuntu it's so great.  :-)

---

### Post by gradinaruvasile on 2009-06-19
> **HistoryMac said:**
> Mic isn't working on Toshiba Satellite Pro L300!!! Aaaaaaah!!!!!

When I try to record sound using the mic that's built into my TOSHIBA Satellite Pro L300, it doesn't work. Skype 2 can make calls, but the person on the other end can't here me :confused: (I'd imagine it's a driver issue)

I'm pretty new to Ubuntu so explain things as simply as possible :) 


Running Ubuntu 8.10 (Intrepid Ibex) on
TOSHIBA Satellite Pro L300
2GB RAM
120GB HDD
2.0Ghz Intel Pentium Dual Processor

Thanks!

Try Skype test Call. Does that work?

Check the capture volume on your system. For that i would recommend using Alsamixer from the terminal. Just open the terminal and type
```
alsamixer
```

Press tab to go to the capture view. Check the Capture item by selecting it (with the left/right arrow keys) and pressing space so that u have a red "CAPTUR" written under it. Check also the Input source item too - using up/down keys see if u have more than 1 input sources (mic, front mic etc).

[COLOR="Red"]And one more thing: UNCHECK "Allow Skype to automatically adjust my sound levels"
[/COLOR]Because that option will lower the capture volume and leave it that way. Dunno why it is there....

---

### Post by Alias1407 on 2009-06-19
Ubuntu doesn't work to well with the front mike inputs on laptops,

I would suggest that you go out and buy a USB Microphone.


Trust me, I had the same problem

---

### Post by gradinaruvasile on 2009-06-19
I have a Dell D630 and it doesnt switch automatically mics when i plug in an external one. I had to select it manually from alsamixer.

---

### Post by technoboi on 2009-06-23
My brother has just ordered an L300. It is his first computer so it would be a steep learning curve, for him, to have to cope with Vista and all the spyware, viruses and resulting slow operation due to anti-spyware programs etc. that goes with Windows.
So, I want to put Ubuntu on it. I have an Eee PC 901 running 8.04 and everything works OK on it. My suggestion, for your L300, is to make a live CD, with another version of Ubuntu, say Jaunty, or even 8.04, and see  if things work better. On my AMD64 machine my Philips webcam worked OK on 8.1 but it doesn't on Jaunty. So, it is a case of finding the best distro and then scouring the web to find solutions for those things that don't work. There is also the new Netbook version of Ubuntu that might be worth trying, but I haven't checked it out yet so I don't know if it would be any use for the L300.
If I come up with any answers I'll report back.

---

### Post by obirenokenobi on 2009-07-27
I have that laptop and works very well with Ubuntu. I encountered the same problem and this is what I did:

1) Open alsamixer
2) Move to "View" -> "Capture", in my case I used tab to get there (ubuntu 8.10), in other versions you may need left and right arrows.
3) With up and down keys, move the volume to 100
4) Move to "View" -> "All", check that Master and Capture are both at 100
5) Press Esc to exit
6) In Skype, preferences, sound devices, put the following:
Input: HDA Intel (hw:Intel,0)
Output: pulse
Calling: pulse
7) UNCHECK "Allow Skype to automatically adjust my sound levels"
8) Voilá!

Hope this helps!

---

