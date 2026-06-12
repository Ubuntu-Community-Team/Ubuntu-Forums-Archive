---
title: "Blank screen after AMD64 Ubuntu install"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Wolvenreign on 2009-06-17
Hey everyone!

Well, I recently freed up about 8 gigs of space on my laptop so I can play all my good Steam stuff on Linux. I had also recently learned that I installed the wrong version of Ubuntu the first time around, as it seems my good ol' lappy has AMD64 architecture.

So, I ran the Ubuntu AMD 64 live Cd, and overwrote my previous partition as well as the newly freed space. However, when I restarted the computer, (and after logging in, with the log in screen displaying perfectly), I was greeted with a screen that was completely black, save for the lone mouse cursor.

Anyway to fix this to make it display the ordinary Ubuntu screen?

Help greatly appreciated!

---

### Post by Wolvenreign on 2009-06-17
It seems like this is something that needs to be solved in shell prompt in recovery mode (if I have the terminology correct).

Is this right, and if so, what commands do I use? From what it seems, installing the proper Nvidia drivers should solve the problem, bit I can't get past the black screen to get the internet working.

Mind you, I HAD installed Ubuntu once before on this very same computer. It was 32-bit, which I realized was a mistake. At the same time, however, I didn't have to go through this the last time.

Once again, help much appreciated.

---

### Post by Wolvenreign on 2009-06-17
Well, after uninstalling GNOME and instead installing KDE as one google result said to do, I tried to log in to Kubuntu (still AMD64) and I was no longer greeted by a blank screen with a mouse pointer. Instead, I am greeted by a series of process notes, such as "Starting network connection manager NetworkManager" and so on. 

     However, it seems to freeze after a pair of twin messages that say "Advanced Power Management level to 0xfe (254). The only difference between the two is that the first says "sda" and the other says "sdb" above their respective messages.

     Oh! This is new. After about 10 minutes hanging there, the computer switches display to two orange stars, both on the upper left corner of the screen, though one orange asterisk sits about five RETURNs under the other, still sticking closely to the left side of the screen.

So, what now, folks? I'm in desperate need of some help, and I truly hope there's some mighty Linux user out there up for the challenge.

---

### Post by Wolvenreign on 2009-06-18
Well...I've posted just about everywhere else...

Does anyone know if this would be a problem if I switched to, say...Gentoo?

---

### Post by merlinus on 2009-06-18
Have you searched for the drivers for your video card, which btw you did not mention?

---

### Post by Wolvenreign on 2009-06-18
Well, I'm not sure how to search for the drivers. I'm guessing that's what this other guy told me to do, but there's a special character I'm not sure how to input. (pc104 keyboard layout)

```
sudo lspci ***_|_*** grep -i vga
```

Is that how you search for the video card drivers? I can at least tell you it was an Nvidia card, and when I ran 32 bit Ubuntu, the driver said that it was in Beta.

Edit: Silly me, it was Shift+backslash. Anyway, the video card is nVidia GeForce 7150M (rev a2)

---

