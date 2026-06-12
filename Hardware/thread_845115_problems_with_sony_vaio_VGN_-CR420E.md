---
title: "problems with sony vaio VGN -CR420E"
date: 2008-06-30
forum: Hardware
---

### Post by amireee on 2008-06-30
hi guys
i purchaised a new sony vaio VGN-CR420E
i tried to install RedHat linux(ver 9 )

but my linux setup is not running so i want to know wether
ubuntu linux can be installed in my laptop and i want to know
wether it supports all the hardware componts like (sound card,webcam and wireless devices)

waiting for your replies
regards
amir

---

### Post by ukripper on 2008-06-30
> **amireee said:**
> hi guys
i purchaised a new sony vaio VGN-CR420E
i tried to install RedHat linux(ver 9 )

but my linux setup is not running so i want to know wether
ubuntu linux can be installed in my laptop and i want to know
wether it supports all the hardware componts like (sound card,webcam and wireless devices)

waiting for your replies
regards
amir

If you boot into Ubuntu live cd and at terminal type the below command then we can find out chipsets of each device your laptop is using and make suggestions:
```
lspci
```

post output here



Found some reviews on this laptop on amazon, someone is using ubuntu from here [http://www.amazon.com/Sony-VGN-CR420E-Laptop-Processor-Premium/dp/B0014HW4MA](http://www.amazon.com/Sony-VGN-CR420E-Laptop-Processor-Premium/dp/B0014HW4MA)
:


"    	
6 of 6 people found the following review helpful:
4.0 out of 5 stars A good work-at-home laptop, May 8, 2008
By 	D. R. Anderson "best daddy ever" (West Seattle, USA) - See all my reviews
(REAL NAME)   
I am running Ubuntu 8 on my CR420E. It works nice. Unfortunately the "Instant Mode" media playing relies on the Windows Vista partition. I would recommend carefully backing up the hard drive raw image and moving to a dual boot scenario to retain "Instant Mode" capability, at a cost of a chunk of drive space.

I've had no issues with the Linux driver support for the Intel chipset. I have not fully used the wireless, but 'iwlist scan' does pick up a list of the neighbors' private networks. So it appears to probably all work. The video, sound, USB, keyboard, trackpad, and SD card reader all work great.

I am not sure how to poll the battery life, but I run mine off the outlet at home so I don't care.

A few quick points on a pretty nice, but arguably not as nice as it is pricy laptop:

Pro: Nice keyboard action, and most of the "function" modified keys are laid out intuitively (home and end = left and right for example). I used similar CR-320Es at local retailers before ordering this, and the comfy keyboard action was really a big attraction to me for writing and coding.

Pro: Plenty of RAM (3GB) right out of the box.

Pro: Fast. I'm no connoisseur but it handles GIMP filter operations like a seasoned blackjack dealer deals a hand. Nice and fast really. I'm at the Ubuntu 8 logon screen about as fast as any Windows XP I've ever had.

Pro: That built in SD card reader! It's so cool to not have to fumble with a cable and card reader.. it is just like a tiny little floppy drive. Just pop the SD out of the camera and right into the computer.

Con: Glossy screen.. unfortunately this is becoming quite common issue.. If I wasn't using this at home, in low light conditions, this sad surprise would have been a return or re-sell worthy issue. Matte is where it's at, as far as I'm concerned.

Con: The speaker just doesn't put out loud enough. External speakers or headphones are necessary for movie-watching without absolute silence and concentration. It's one of many reasons I would only recommend this as a home laptop.

So-so: Battery life is just so-so, I usually get about 3 hours. A "high capacity" battery may be ordered separately. Again I would only recommend this for home use, so run it off the wall and this is a non-issue."

---

### Post by amireee on 2008-07-01
**I would recommend carefully backing up the hard drive raw image and moving to a dual boot scenario to retain "Instant Mode" capability, at a cost of a chunk of drive space.**

i have formated my hard disk totally .is the above mentioned is mandatory and also please tell me what is Instant Mode

---

### Post by ukripper on 2008-07-01
> **amireee said:**
> **I would recommend carefully backing up the hard drive raw image and moving to a dual boot scenario to retain "Instant Mode" capability, at a cost of a chunk of drive space.**

i have formated my hard disk totally .is the above mentioned is mandatory and also please tell me what is Instant Mode

I am not used to Vista so not really sure about it. 

And to your question it is not necessary it is just precautions he is taking as a fallback position.

All you have to care about is your important data which you require and is good to backup regularly and you can do that by using sbackup in ubuntu which is there by default.

---

