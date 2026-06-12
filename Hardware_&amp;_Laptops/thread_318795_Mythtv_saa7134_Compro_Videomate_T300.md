---
title: "Mythtv saa7134 Compro Videomate T300"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by b3n87 on 2006-12-14
Hello, im getting desperate now, hopefully someone can help me.

I cant get my Compro videomate T300 DVB tv tuner to work with myth tv or anyway else for that matter.

amsn's webcam extension can sometimes that i have the card in the PCI slot, because it correctly names it, other times its called "unknown" instead. which makes me think that it could what driver is being loaded?

Basicly i was just wondering if anyone has got it working yet, and if so can they PLEASE PLEASE help

im really stuck on this one, thanks in advance

Ben

---

### Post by superm1 on 2006-12-15
> **b3n87 said:**
> Hello, im getting desperate now, hopefully someone can help me.

I cant get my Compro videomate T300 DVB tv tuner to work with myth tv or anyway else for that matter.

amsn's webcam extension can sometimes that i have the card in the PCI slot, because it correctly names it, other times its called "unknown" instead. which makes me think that it could what driver is being loaded?

Basicly i was just wondering if anyone has got it working yet, and if so can they PLEASE PLEASE help

im really stuck on this one, thanks in advance

Ben
I haven't worked with your particular tuner, but a good place to start is to check dmesg for information about the drivers attempting to be loaded for the card.

---

### Post by ultima on 2006-12-27
I have this same card and have it running with Mythtv. Try putting saa7134-dvb in /etc/modules

This card is not the easiest card to setup with Mythtv but it can be done. I had alot of trouble scanning for channels. You will probably need to enter the frequencies for each channel. If you are running KDE I recommend you have a look in this directory ~/.kde/share/apps/kaffeine/dvb-t and open the file where you live, this will tell you the frequencies and other things you will need.

---

### Post by Tim Prosser on 2007-01-11
I managed to get one of these working OK, as mentioned you need to add the saa dvb driver using modprobe.  You might also need to tell modprobe what card type you are using:

modprobe saa7134 oss=1 card=70
modprobe saa7134-dvb 


There should be no trouble tuning the DVB-T with Kaffeine or Mythtv provided you start with a known channel frequency.

Analogue also works with TvTime if you can be bothered with that.

I also added Analogue+Composite in to Mythtv so I can copy videos to DVD - which works fine.

Haven't got the machine in front of me at the moment so can't check exactly what I did - but don't panic, its definitely not a dud.

PS Didn't get FM Radio working though - be interested if anyone has.

---

### Post by peterthewolf on 2007-01-27
I have a Compro Videomate DVB-T200 I got it working with Kaffeine without much trouble. I then tried Mythtv but had no success at all in finding any channels. To check that card was still installed properly I ran Kaffeine again all the channels had disappeared and I could not get them back until I had UNinstalled Mythtv.

---

### Post by peterthewolf on 2007-02-04
I have tried mythdora with the card, mythtv then scans channels ok albeit very slowly, but no TV display
I think it is something to do with mythtv loading an old module saa7146 which a google search says has been superseeded by saa7134. This would explain my experience with kaffeine and mythtv above.

Possibly the best that could happen would be for the mythtv people to look at kaffeine to see what they are doing wrong.

---

