---
title: "Thinkpad T43 Shuts Down Randomly and then....."
date: 2009-04-07
forum: Hardware
---

### Post by slinkeey on 2009-04-07
Hello,

My Thinkpad T43 Shuts Down Randomly (Maybe it is not random, but i can not find any pattern) and then it can be a real pain to get going again..

I usually have to take the battery or power out and keep reapplying and removing power until I see the amber battery led blink.  When I get the machine running again, It may run for .5 seconds or 5 days..  It all depends on how it feels :)

So for some reason if I remove the power completely over and over it comes back to life.  (Removing and Reinserting the battery over and over with the power unplugged...  Or I will out the battery and plug and unplug the power cord over and over)..

I have tried running it on just battery.. I have also tried just running it on AC.. Same thing..

I have asked in Thinkpad groups, but did not have any luck..

I am a ubuntu user and I know the ubuntu community is top notch so I figured it wouldn't hurt to ask for advice here.

Thanks,
Jeff

---

### Post by wirepuller134 on 2009-04-07
This is my experience, we use exclusively IBM equipment for laptops.  Don't laugh, but my primary laptop is an old old old model 2611.  It still does the job and I need the serial port to log into older Allen Bradley processors.  It got to where it would not boot up at times, removing the battery and power supply, then reinserting the battery, then powering it on, then plugging in the power supply would allow it to boot normally.  From looking at the way it is built, it actually runs from the battery on boot up. I needed to replace the battery pack, it was a pain to do, since they don't make them anymore.  So we bought the batteries separately from one of our suppliers and rebuilt the pack.  The old system is still plugging along.  This fixed ours, hard to say what could be doing it to yours.  Hope this helps.

---

### Post by slinkeey on 2009-04-07
Allen Bradley Processors.. Hmmmm PLCs?

Anyways thanks for responding and thanks to whoever moved this. I put it in the cafe because it was not Ubuntu related...

I don't think the battery boots this notebook..  Besides, I have the same problem with the battery unplugged and running on just AC...  Sometimes I have luck and sometimes not..

Thanks for your advice!! :)

Jeff

---

### Post by wirepuller134 on 2009-04-08
Mine will not boot without the battery in it.  But it is an antique.  Heat issue?  Are all of the fans operating?  It might be worth it to lift the keyboard out and see how dirty the cpu fan is.
  Off topic:
  Yes they are PLCs, the older ones like the slc 500's and several Mitsubishi's and omron touch screens prefer a real serial port rather than a usb converter.   The 1746-PIC will only work with a real serial port.  Thus I keep the old boat anchor, I get laughed at by our employees when I bring it out, but it is a heck of a conversation piece.

---

### Post by eldragon on 2009-04-08
i dont want to be the one saying this but since noone pointed it out: its almost definately the mainboard on its way out.

ive seen this happen on several lenovo. first the battery goes, then the mainboard.

---

### Post by slinkeey on 2009-04-08
Ubuntu reports that I might have a broken battery.  It says that it is working at 45% capacity.  This appeared to happen at around the same time this problem started.  That is one of the reason why I have been seeing if running it on just AC would solve the problem.  You might be onto something.

Off Topic:
PLC are pretty cool.. I remember when my dad use to program PLCs using ladder logic.  If I remember right, he mostly dealt with Modicon.  I did remember some AB PLCs  in some of the machinery that he built.

---

### Post by slinkeey on 2009-04-08
The fan is working good.

I have already removed the keyboard.. The inside was pretty clean but I dusted it out..

---

### Post by wirepuller134 on 2009-04-08
Just to see I broke out the boat anchor and no it will not boot without the battery in it.  The newer ones will.  So we could only think of a few things.  A heat issue caused by the fans not running fast enough, bad connection between the cpu and the heat sink.  Dust or debris in the power switch not allowing it to make contact properly when pressed, or conductive debris causing the switch to make contact constantly or a failed power switch on the motherboard. Last but not least as mentioned above, hardware failure of the motherboard.  I hope its not the last one, and is an easy fix, but if it is hardware failure, look at it this way.....it makes a cool paper weight.

---

### Post by slinkeey on 2009-04-08
Well.. I will have to see if the power switch is a culprit..

I checked the heatsink and it is seated well.  as far as I can tell.

It is so wild how for example recently it has been running for a few days now without a problem..

Funny PLCs came up in this conversation because I was going to say that I just got rid of a Canon Innova (Made by Acer) recently from probably 1991/1992 386sx.  That was used for PLCs and a Mitsubishi Wire EDM.  Been in a shop enviroment for years and never missed a beat.  I wish I could say the same for this IBM and I am a big fan of the IBM iSeries (AS400).

---

### Post by RJARRRPCGP on 2010-02-28
> **wirepuller134 said:**
>  From looking at the way it is built, it actually runs from the battery on boot up. 

That reminds me of my Belkin UPS. LOL. 

With the UPS battery dead, the UPS won't even power up with AC power. :(

---

### Post by tgalati4 on 2010-02-28
If you have a shorted cell in a battery, then the power-limiting circuitry will cut out when you exceed a certain current level.  It's possible that your battery is drawing too much current during charge that either your power supply or on-board current limiter is causing a safety shutdown.

Time to get a new battery.  Or borrow one from a similar T4x machine to test.

Don't delay, because running at high current can burn out your power supply and/or destroy the main board.

Batteries are only good for 3 years or 300 cycles, whichever is most inconvenient.

---

### Post by yaklly on 2012-03-06
Hello,

My Thinkpad T43 Shuts Down Randomly (Maybe it is not random, but i can  not find any pattern) and then it can be a real pain to get going  again..

I usually have to take the battery or power out and keep reapplying and  removing power until I see the amber battery led blink.  When I get the  machine running again, It may run for .5 seconds or 5 days..  It all  depends on how it feels :smile:

So for some reason if I remove the power completely over and over it  comes back to life.  (Removing and Reinserting the battery over and over  with the power unplugged...  Or I will out the battery and plug and  unplug the power cord over and over)..

I have tried running it on just battery.. I have also tried just running it on AC.. Same thing..

---

