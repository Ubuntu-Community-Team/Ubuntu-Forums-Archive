---
title: "Ubuntu amazes me... Read On"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by skwid on 2006-01-30
I usually don't post things like this but I recently built a new PC for gaming only and decided to put ubuntu on it.  I've been useing ubuntu on my laptop but I wanted to see how it would load up on some fancy hardware and how hard would it be to configure...

New PC Specs:

Asus P5N32-Sli  NForce 4 (Audio, Broadcomm Nic, Nvidia Nic)
P4 Extreme Edition 3.73Ghz
2 Gig Crucial Ballistix 667
2 x Asus 7800GTX Tops, in SLi Config.
1 74GB Raptor (On Nvidia Controller)
2 250GB Hitachi's (Also On Nvidia Controller)
Onboard Sound
Linksys WMP54g Wireless Card

Ok, I went through the standard ubuntu breezy 5.10 install with no troubles.  It detected the onboard nics and used them but didn't say anything about the wireless card...  I just kept going.   After the install was complete it booted to a perfect ubuntu login screen at my LCD's native res...  no trouble so far.   I then logged in and shocked me the onboard sound was working perfectly.  No Config...    I went into the networking Config and the wireless card was listed.  I checked the properties and clicked activate and it worked!   I couldn't beleive it...   Anyway the last thing I needed to do was load the latest Nvidia 8178's.  I installed build essential, gcc, gcc-3.4, linux headers,  and killed gdm.  I went to load them and the only hiccup I ran into is that it could not find gcc.  I simply fixed that with a export CC=/usr/bin/gcc-3.4, and re ran the installer and all it compiled with no problems.  The new Nvidia installer is great that it fixed the x config file for you...  I made a slight mod to setup my dual monitor setup and again it all worked no problem.

I am getting great frame rates in UT2004, Quake4, etc...

I just want to say excellent job to the Ubuntu Crew and these forums for making things VERY easy on everyone and what an excellent distro!

Sorry to blab...
Jeremy

---

### Post by hartnady on 2006-01-30
Yeah. It's kickass.

---

### Post by markcaetano@gmail.com on 2006-01-30
i totally disagree it dosent even support dialup

---

### Post by Sp@z on 2006-01-30
As I gamer I have to say I am impressed with how UT99 and UT2K4 run in ubuntu.....I get as good or better FPS in ubuntu as I do windows, the only thing I miss is on the fly sens switching with my copperhead.everything but that works......

---

### Post by djheadley on 2006-01-30
What do you mean, it doesn't support dialup?  I guess I'm using magic to connect to the internet.

djheadley

---

### Post by boomerian on 2006-02-01
What version of the LinkSys WMP54G are you using?
I cannot get version 2 (Broadcomm chipset) working for the life of me...
VERY frustrating, and no help (some suggestions, interest then wanes, and here I am) on the forums...

---

### Post by Lord Illidan on 2006-02-01
[quote=markcaetano@gmail.com]i totally disagree it dosent even support dialup[/quote]

Take a look at this, then : [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

To OP : Your specs have me salivating...
I wonder... how much is your fps rate in glxgears?

```
glxgears -printfps
```

---

### Post by skwid on 2006-02-01
[QUOTE=boomerian]What version of the LinkSys WMP54G are you using?
I cannot get version 2 (Broadcomm chipset) working for the life of me...
VERY frustrating, and no help (some suggestions, interest then wanes, and here I am) on the forums...[/QUOTE]

Sorry for the late reply.. I am using version 4.

@Lord Illidan... I was wondering how to do that... I didn't let it run too long but here is the numbers.   What does it all mean?  I can only relate to 3dMARK scores. 

```
skwid@hizouse:~$ glxgears -printfps
63750 frames in 5.0 seconds = 12749.983 FPS
67610 frames in 5.0 seconds = 13521.892 FPS
67714 frames in 5.0 seconds = 13542.732 FPS
67379 frames in 5.0 seconds = 13473.451 FPS
67773 frames in 5.0 seconds = 13554.578 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
skwid@hizouse:~$

```

---

### Post by FX on 2006-02-01
> I simply fixed that with a export CC=/usr/bin/gcc-3.4, and re ran the installer and all it compiled with no problems. 

Only problem with that is though what person that is new to linux coming from windows it gonna do that????

Not trying to be a jerk or nothing but lets face it. Linux has a ways to go yet before it gets as easy as MS. Only reason I know what I know is because I sat and took the time to learn. Most people that would like to break from MS are not going to do that.

---

### Post by skwid on 2006-02-01
[QUOTE=FX]Only problem with that is though what person that is new to linux coming from windows it gonna do that????

Not trying to be a jerk or nothing but lets face it. Linux has a ways to go yet before it gets as easy as MS. Only reason I know what I know is because I sat and took the time to learn. Most people that would like to break from MS are not going to do that.[/QUOTE]


Same here dude...  I've been using it for a couple of years and it's just basically setting down and Sticking to it.  And ALOT of reading.

---

