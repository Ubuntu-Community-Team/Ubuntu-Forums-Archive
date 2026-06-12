---
title: "problem: Hp tx2"
date: 2010-08-09
forum: Hardware
---

### Post by piravi on 2010-08-09
Hi all! 
 I installed ubuntu on my tx2 hp and it works very well.
Now I want to use only the pen and disable the touch.... because I use my notebook to take freehand notes, using the pen.



How Can I do? 
Thanks.

---

### Post by clrg on 2010-08-09
Maybe you can disable the touchpad in the BIOS (I did it this way on my IBM).

---

### Post by piravi on 2010-08-09
In that case even the pen doesn't work.

---

### Post by Favux on 2010-08-09
Hi piravi,

With a default Lucid set up the stylus should be controlled by the linuxwacom driver and touch by the evdev driver.  You could check in Xorg.0.log in /var/log to be sure.

If so then to turn touch off you want b) evdev in 5) Turning touch on and off at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by piravi on 2010-08-10
Hi,
I have tried for days to resolve my problem, but without success!
So, I'm searching for someone helps me.

I installed ubuntu 10.04 on my  Hp tx2. It works well, but I have two problems:

1)Screen [I]rotation
2) I want to use only the stylus, because xjournal work bad if the Touch is on. I tried  to modify xsetwacom...without success. 


I can pay 100 euros  (130 $) for a perfect work.




[/I]

---

### Post by lisati on 2010-08-10
Threads merged. 
We're all volunteers here. We appreciate your offer: perhaps the person with the *perfect* solution hasn't seen your questions yet.

---

### Post by piravi on 2010-08-10
Okkey sorry:)

However I can pay who resolves my problems:) 
Thanks

---

### Post by Favux on 2010-08-10
Hi piravi,

The N-trig HOW TO I linked you to also has rotation scripts:  "4) Rotation to tablet".

You either follow the link to the Rotation HOW TO if you're using all wacom for your drivers and maybe use the Magick Rotation applet or you use the hybrid wacom/evdev scripts.  There's a new hybrid script in the last few pages of the thread if you don't like the recent one by Rafi.

---

### Post by piravi on 2010-08-10
No... it doesn't work..
I need a professional support...
What about canonical.com?

---

### Post by Favux on 2010-08-10
Never tried Canonical support.  Hear they are good.  Good luck.

---

### Post by piravi on 2010-08-11
They are good but slow:)
Favux, I renew to you the offer I did to you via private message. If you're interested...;)

---

### Post by piravi on 2010-08-12
Solved: It was easy: 
xinput float "N-Trig Touchscreen"
xinput reattach "N-Trig Touchscreen" "Virtual core pointer"


Now I'm trying to rotate the screen:
I tried some scripts but when I rotate  the screen, the  cursor isn't where the stylo is!

What Can I do?

---

### Post by piravi on 2010-08-13
Solved, but it isn't good: it seems windows vista. 

.... so: Windows7:) see you...

---

