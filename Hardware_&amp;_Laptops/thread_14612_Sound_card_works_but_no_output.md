---
title: "Sound card works but no output"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by Deusiah on 2005-02-08
Sorry for the rather vague title, allow me to clarify. My sound card works I know this becuase I have a head phone output located on my sound card (pins not 3.5mm jack) which I connected to a 3.5 mm jack on the front of my PC some time ago. When I discovered no sound was coming out of my speaker I discovered that this output still works which proves my sound card is in working order.

I am currently running Ubuntu Hoary 64-bit version, my sound card is an Audigy 2 ZS. This sound card was working in the past but I come to start it up one day and no sound. For some reason the three output levels, LFE, Center and Surrond must now be set to silent which would explain the headphone socket still working.

My problem is how to turn up the volume on the three speaker output channels. I have loaded up just about every setting in Gnome Volume Manager and turned them up but to no avail and now I have simply ran out of paths to go down.

Any ideas how to resolve this issue?

Thank you,
Deusiah

---

### Post by Deusiah on 2005-02-09
Over 20 views and not a single reply must mean no one knows how to fix it which isn't good. I have searched for an answer on Google to but I can't find anyone with a problem like mine :(

Even if you don't know the answer I'd like to hear any ideas for anything I can try, I have run out of things to mess about with.

---

### Post by Deusiah on 2005-02-10
[QUOTE=Deusiah]Over 20 views and not a single reply must mean no one knows how to fix it which isn't good. I have searched for an answer on Google to but I can't find anyone with a problem like mine :(

Even if you don't know the answer I'd like to hear any ideas for anything I can try, I have run out of things to mess about with.[/QUOTE]


Never Mind, fixed it myself. Solution was to open alsamixer from a terminal, find "Audigy Analog/Digital Output Jack" and unmute it (m). This toggles between digital/analogue. Gnome Volume Control does not provide an option for this however as it crashes for me when I try to enable it.

---

### Post by r00 on 2005-02-28
that's awesome! wish i could do that with my usb extigy..
got the ac97 onboard working with no surround.. i've tried every configuration in the mixer and still only came out of two speakers..

and with the usb extigy, i played with alsamixer forever and not a sound came out of either the front headphone jack or any of the channels in the back.. 

i might just have to trade my usb extigy in ..but i'll wait a little while longer til in hopes i can find an answer..

---

### Post by Deusiah on 2005-03-01
I'd just like to add that an older version of Gnome Volume Manager seems to support the digital/analogue switch. I was using Hoary before but now I'm back with Warty and I see the switch without using Alsa Mixer.

As for the surround make sure front and front PCM etc are turned up. Apart from that there's nothing more I can suggest.

---

### Post by kelean on 2005-03-01
[QUOTE=Deusiah]I'd just like to add that an older version of Gnome Volume Manager seems to support the digital/analogue switch. I was using Hoary before but now I'm back with Warty and I see the switch without using Alsa Mixer.

As for the surround make sure front and front PCM etc are turned up. Apart from that there's nothing more I can suggest.[/QUOTE]
 I know how you feel Deusiah.  I have a post up for several days now and im the only person to reply to it.  Ubuntu has a problem with sound and not much if you have an odd cound card.

---

### Post by Deusiah on 2005-03-02
I wouldn't say Ubuntu has a problem with sound Kelean. I think it's more accurate to say that the support Linux has for some sound cards is not as good as one would like it to be.

As for the lack of people answering your posts I have also had the same problem. This post was up for a good few days before recieving any answer. I think the best thing to do is, if possible, find a thread already discussing your problem and post in there. I didn't do this becuase my problem seemed to be nothing like any problem I could find on the forums.

Other that that you could always try asking for help in general Linux forums as I very much doubt your problem is Ubuntu specific. You could also try asking for help in IRC chat too. If your like me however and your the type of person who would rather not trouble someone else asking for help then the best thing you can do is search on Google and keep messing about with your card, and don't give up till it's fixed. That's what I had to do in the end, then I post my answer here hoping it might be of some use to someone else.

---

### Post by r00 on 2005-03-06
oddly enough..
i re-installed ubuntu after doing some random testing and screwing many things up..
installed all 200+ updates hahha.. and rebooted.. amazingly..the sound was working on the extigy after some minor raising of volume and messing with the switches.. still no surround..but at least the extigy works now :P

---

