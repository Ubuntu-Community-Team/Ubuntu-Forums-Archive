---
title: "Weird mixing from line-out vs. headphone jacks"
date: 2014-02-25
forum: Hardware
---

### Post by Tinman131 on 2014-02-25
All - 

I have recently acquired a university research machine (upgraded version of a Dell Precision T3610, which obviously needed Linux) and I've recently found that sound from my speakers sounds horrible when plugged into the "line-out" jack in the back of the machine.  It sounds great, though, when plugged into the "headphones" jack in the front of my machine and equalized through the VLC equalizer.  Alsamixer shows that I can't raise the dedicated "Speaker" channel volume past 00 regardless of which jack it's plugged into, and auto-mute mode toggled to different settings doesn't produce any changes.  Adjustments in alsaequal (thought maybe I just needed a system-wide equalizer) don't change anything with sound quality on _either_ jack.  This problem didn't occur with an older Dell Optiplex 780, which I put ubuntu on a few weeks ago and has the same front headphone / rear line-out jack.

PulseAudio, my alsa packages, libasound, and everything else have been updated as well.  For reference, this is Mint 16.

Anyone have an idea what's causing this difference?  Thanks in advance.

---

### Post by tgalati4 on 2014-02-25
Who knows what abuse a university research machine has seen.  Take it apart and clean the motherboard.  Look for water/coke intrusion and leaky capacitors.  Also look for burn marks, paint, smoke, beer, bits of clothing, anything else that is commonly found in a university research lab.

The fact that you can't change the volume level is consistent with a shorted sound card.

---

### Post by Tinman131 on 2014-02-25
Well, sorry, I should have been more specific.  Recently acquired was meant to signify we just bought it, and it was delivered from Dell last Thursday.  I'm doing an initial setup of the machine.

The master channel in alsamixer allows volume level modification, but just not the "Speaker" channel (like I said, stuck at 00).

---

### Post by tgalati4 on 2014-02-25
If the machine was delivered from United Parcel Soccer, then you need to pull it apart, inspect everything and reconnect.  One loose cable will cause issues.  I mistakenly assumed this was pulled from an "Animal House" style laboratory.  Rest in Peace [Harold Ramis]("http://www.nytimes.com/2014/02/25/movies/harold-ramis-who-helped-redefine-what-makes-us-laugh-on-screen-dies-at-69.html?_r=0").

---

### Post by Omer_Rosenberg on 2014-03-11
I see that the thread is mark as SOLVED
How ???
I'm having the same problem
Thanks

---

### Post by Mugatu on 2015-01-05
> **Omer_Rosenberg said:**
> I see that the thread is mark as SOLVED
How ???
I'm having the same problem
Thanks

I had a similar problem with a Dell Optiplex 9020. My solution was to click the volume icon &#8594; *Sound Settings* &#8594; *Output Devices* and then change the value for *Port* until it sounds better. For me the value that worked best was *Headphones (unplugged)*.

I am using Xubuntu, so some of the specifics may be different.

Hope that helps.

---

