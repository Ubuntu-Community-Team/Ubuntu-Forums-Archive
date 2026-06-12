---
title: "Any experience with a Gateway MT3421 or similar models?"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by Fujimitsu on 2007-07-24
I am planning on picking up a cheap gateway at office depot this week for $500 AR, the model # is MT3421.  The laptop is a retail-only model so i couldnt find much information at all about it online other than the office depot page and this [http://www.gateway.com/retail/mt3421.php](http://www.gateway.com/retail/mt3421.php).

It s a cheap laptop that i just plan on using for work and school, but since its relatively weak im really not looking forward to Vista on it... thats where you guys come in.  

I've installed Ubuntu on a couple of desktops without a hitch so i know my way around relatively well but i wouldn't say I'm an "advanced user".  I'm looking at installing Ubuntu in a dual-boot with Vista or XP depending on how vista performs.  

My question is has anyone had any experience with this or similar laptops? There are a whole slew of similar retail-only laptops from gateway, each with just a slightly different configuration.  I can't seem to find any really detailed information on them (hardware models etc.) so i cant just search for specific parts.  I just need to know whether i will be able to get this working or if i should look somewhere else (possibly a vostro).  I am willing to do a decent amount of work to get this up and running as long as its possible, if anyone has any experience or even just details about the hardware in this thing i can do the research on my own.

Anything you can offer is appreciated, I'm just a little worried because i can find so little about this machine anywhere although it seemed alright in the store.

---

### Post by Fujimitsu on 2007-07-25
*bump*
anyone have ANY information on what hardware is in this? or if it works? im gonna just buy it today and see how it goes i guess

---

### Post by Fujimitsu on 2007-07-26
Bought it yesterday, I got ubuntu installed and working very quickly.  Wireless networking works with ndiswrapper, 3d works fine (or as well as a 6100go can), only problem is no sound yet :/ illl try and post again if i get it working.

---

### Post by 311005901 on 2007-08-24
I just bought one of these yesterday. 
I can't get the sound to work or the desktop effects.

I'm dual booting with Vista and Fiesty.

---

### Post by aggieml on 2007-09-20
I bought one a few weeks ago and have been dual-booting with Vista and PCLinuxOS.  Everything works fine except:
1.. you have to use ndiswrapper for the wireless card to work
2.. I HAVE NOT BEEN ABLE TO GET THE SOUND TO WORK.  The current version of ALSA does not support it.  It tries to use module snd-hda-intel and appears to set up correctly and appears to work except nothing comes out of the speakers or headphone jack.  The sound card is an NVidia MCP51 High Definition Audio (SigmaTel 9200).  From what I've read, some people have gotten this sound card to work on other laptops using OSS, but I have read no one that got it to work on a Gateway MT series laptop.  I went out and bought a $40 usb sound card from Turtle Beach for linux.  
3.. the left button of the touchpad kinda broke on me within 2 weeks of buying it.  I pressed it one time and I heard a snap.  It still works, but it's just barely resting on the sensor and there's no click noise anymore.  It's not too big of a deal, but it annoys me.

Hope I've been helpful to some out there.

---

### Post by james9876 on 2007-09-26
I managed to get the sound working very well on mine.  Funny, it worked very well at first though, but then disappeared when I updated to feisty, and it took a lot of work to get back again.  Unfortunately I cannot remember what I did now :(.

An additional note, I use USB speakers, so that might have something to do with it.

---

### Post by Fujimitsu on 2007-09-28
I never did get the sound to work, but yes NDISWRAPPER is required for wireless.

Screen just broke on it... yay! you guys know what model of screen I would need to replace it?

---

