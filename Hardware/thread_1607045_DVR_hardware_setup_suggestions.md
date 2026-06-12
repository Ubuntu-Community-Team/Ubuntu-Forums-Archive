---
title: "DVR hardware setup suggestions"
date: 2010-10-27
forum: Hardware
---

### Post by claven123 on 2010-10-27
I'm thinking of setting up a linux box to use as a DVR in the basement.  I have old computers lying around and could use the case and maybe the HD.  Anyone suggest a set up for doing this.  I was thinking of just building a cheap machine to do this.  I've read about some of the issues with mythTV and some of the other programs.  It seems they need a bit of tinkering to get them to work.  However, for this one and only application I think it's worth it.  (does this work with comcast cable?)

---

### Post by blackswamper on 2010-10-31
Comcast Cable TV is exclusive to their tuners because their signals are encrypted with a proprietary encryption. They are only obliged to deliver a hand-full of "open" channels that you would not need to decrypt. You will not find a tuner card that can decrypt and tune Comcast Cable TV unless it is provided by them (their own branded "receivers"), which they "supposedly" have been developing but have never released or sold (as far as tuner/capture cards). Just getting their DVR tuner (which runs Linux with a HDD, as does DirecTV's DVR, lol) only runs a couple more dollars a month (I know, it's already highway robbery as it is WITHOUT an HD package),but once the signal is beyond the tuner it is decrypted. At that point any Linux compatible tuner/capture card should be able to display and record the signal (given that the hardware can handle the duties). I have the standard def reciever output through RCA to my Pinnacle HD Pro's RCA input. TVTime in Maverick Meerkat (10.10) displays fine without any configuration. I have yet to setup MythTV, but I would bet that it wouldn't be hard to deploy in my configuration and would probably be the best and easiest solution for any DVR setup. Hopefully my older PC (Athlon XP 2500+, 1GB DDR) can handle the encoding. Mot sure about that yet.

---

### Post by claven123 on 2010-10-31
Been looking around for some how to's but I keep getting windows systems.  I do have a reciever/decoder in the basement, but it isn't in HD nor is it a recorder.  Might be easier to get another one that is a recorder :).  Can't be that much more, but I have this urge to see if I can do it myself with ubuntu.
 
I'll have to look at some cards.  (now just need to find one that works well with ubuntu 10.10).

---

