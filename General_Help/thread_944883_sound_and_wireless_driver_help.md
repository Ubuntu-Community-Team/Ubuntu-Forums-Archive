---
title: "sound and wireless driver help"
date: 2008-10-11
forum: General Help
---

### Post by a_weasel on 2008-10-11
I just switched over from vista. I'm having 2 problems currently:

1. Sound: I'm getting sound, but it's weak and thin compared to how it was on vista, so i think there must be some sort of driver problem.

This is all the relevant information I know to give...I'm sure there's more; tell me what to type!!
```
daren@daren-laptop:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```


2. Wireless: I believe my card is detected, but I can't connect to any wireless networks. (I'm getting internet access, but i have to be plugged in.)

This comes from lspci as well:
```
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

I'm pretty lost/overwhelmed right now, and just a little worried that I might have made a rash choice in switching...thanks in advance for any help.

---

### Post by zachthejones on 2008-10-11
check under System -> Adiministration -> Hardware Drivers. Is it showing a restricted Broadcom driver? If not, just try rebooting with the computer hooked up via ethernet and see if you get a dialogue notifying you of the option to install the driver. Hopefully it'll detect your card and do all the hard work for you. That's how I got mine installed.

If not, there's a way to make it detect the card and install it, but I can't remember it offhand...

Congrats on the switch, though. Wireless is always a little touchy at first, but I'm sure you're going to have a tone of fun with Ubuntu!

---

### Post by a_weasel on 2008-10-11
Heh, actually, between the time I wrote that i was worried switching was a rash choice and now i've become increasingly enamored of the opensource philosophy in general...all of the IDE's i used in windows were already supported and all i had to do was click "add-this"...pretty cool! Getting java up and running was a snap as well (btw, when did version 6 get released?...i thought 5 was still relatively new...).

anyway, I dunno what happened because the Broadcom stuff wasn't there before (I'd tried exactly what you said) but now it showed up, so I'm good on that front.

Still a little confused about sound, but maybe it's a non-issue, because I intend to install XP as a secondary OS so that i can still run music applications and games.

Thanks for the help!

---

### Post by zachthejones on 2008-10-11
first thing to check with the sound is to pop open the terminal and type in "alsamixer" (I believe that's it) and check all those levels. That's what I found to be wrong with my first install. I don't know how it determines some of those settings, but sometimes they're a little off...

And yeah, I was pretty much the same way. Just enjoy the ride. Linux (and Ubuntu in particular) are a different animal than Windows. Sooooo much better in my mind, but you've got to be willing to spend a little time sometimes...but it's always been worth it in my experience.

---

### Post by Bucky Ball on 2008-10-11
Double click your speaker icon, make sure you have the correct device selected and volumes are up, nothing muted. Experiment with that window and find the right combination for your requirements.

---

