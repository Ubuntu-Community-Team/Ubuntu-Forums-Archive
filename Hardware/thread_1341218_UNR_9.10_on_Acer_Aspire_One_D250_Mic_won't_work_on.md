---
title: "UNR 9.10 on Acer Aspire One D250 Mic won't work only with skype"
date: 2009-11-29
forum: Hardware
---

### Post by gian unr on 2009-11-29
Hi there, 

I installed UNR 9.10 on an Acer Aspire One D250, everything works perfectly, only the mic won't work with skype.

- I tried all the imput setting on skype (I cannot change any of them)
- downloaded skype from medibuntu "vers. 2.1 beta"
- already tried skype vers 2.0 - doesn't work at all
- mic works for recording.

can someone please help me out with this??? please!!!

Thanks
Gian

P.S. I'&#7743; not an expert...go easy!:D

---

### Post by devinb999 on 2009-11-29
I came across this when I had the same problem with my girlfriends Aspire One. I'm trying it now and I'll see if it works.

AspireOne D250 Microphone Issue

Microphone doesn't work out of the box. Download alsa-driver-1.0.20 from [www.alsa-project.org](www.alsa-project.org) and compile it with ./configure --with-cards=all (initially microphone in the mixer is muted!) In mixer settings input source should be set to "Mic" (default), not "Front Mic".

Entire article found on this page
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by gian unr on 2009-11-30
I'm not really sure about that...how am I supposed to "compile"??? sounds still a little over my level of expertise

thanks
Gian

---

### Post by Aearenda on 2009-11-30
I am not certain but the D250 may have the same problem as my A150 with Skype. See posts 16 and 18 on [this thread]("http://ubuntuforums.org/showthread.php?t=1313137"), which describe how I made mine work.

BTW, Karmic (9.10) already has Alsa 1.0.20 installed. That article is for Jaunty (9.04).

---

### Post by gian unr on 2009-11-30
Thanks a lot...it worked!!!!

You made my day!!!

It was actually very simple and yet so hard to figure out!!!

amazing!!!

---

### Post by necro351 on 2010-06-07
Thanks, post 16/18 also worked perfectly for me.  Its a complete hack though, they need a way to make this work out of the box without complicating the system.  Thanks!

---

### Post by crjackson on 2010-07-28
> **Aearenda said:**
> I am not certain but the D250 may have the same problem as my A150 with Skype. See posts 16 and 18 on [this thread]("http://ubuntuforums.org/showthread.php?t=1313137"), which describe how I made mine work.

BTW, Karmic (9.10) already has Alsa 1.0.20 installed. That article is for Jaunty (9.04).

Thanks for the like, it just solved my skype mic problems on Lucid UNE with my wife's new Gateway netbook.  I used the alsa mixer and it works fine provided you turn OFF the option for Skype to automatically adjust your mixer settings.

Do you know of anyway to make the setting permanent so that skype can set a dead channel or starting any app. with mixer adjustments won't show or alter the dead channel?  This bug REALLY sucks.

---

