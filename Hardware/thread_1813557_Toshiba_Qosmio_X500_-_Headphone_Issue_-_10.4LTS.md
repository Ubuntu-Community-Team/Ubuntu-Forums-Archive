---
title: "Toshiba Qosmio X500 - Headphone Issue - 10.4LTS"
date: 2011-07-27
forum: Hardware
---

### Post by fl00ky on 2011-07-27
Hey all. So I downloaded and installed Ubuntu 10.4 LTS last night. 

Generally everything is working just fine except for the headphone jack.

I have searched the wonderful world that is Google and found many users with similar issues and certain solutions. The most recommended one involved adding a line to a certain conf file. Yet, after trying a few things and playing around with the sound preferences, the following are my issues:

1) Sound output is only working through the laptop's built-in speakers. 
2) Headphone jack doesn't seem to pick up anything.
3) Headphone jack is functional in Windows 7 which is on a separate HDD.

I've spent a couple hours on this already and it's really doing my head in. I am a beginner to Linux, but not computers. 

My aslamixer does not show a control bar for headphones.

---

### Post by mikewhatever on 2011-07-27
1. That doesn't seem to be a problem, unless you want the speakers silent.
2. So you've tried adding options to /etc/modprobe.d/alsa-base.conf? Can you be more specific? Have you identified the sound device?
3. Hm... Why is that a problem?

---

### Post by fl00ky on 2011-07-27
> **mikewhatever said:**
> 1. That doesn't seem to be a problem, unless you want the speakers silent.
2. So you've tried adding options to /etc/modprobe.d/alsa-base.conf? Can you be more specific? Have you identified the sound device?
3. Hm... Why is that a problem?

Looks like trial and error paid off in the end. I do have it working. 

For others who may be looking for information, the issue:

Built-in speakers worked fine. On inserting my headphones the speakers didn't mute and I couldn't hear anything in the headphones. 

What I did: 

Typed the following into Terminal to gain access to the configuration file:

> sudo gedit /etc/modprobe.d/alsa-base.confI made the following addition to the bottom of the file. The issue was just finding the right model name, I guess.

> options snd-hda-intel model=ideapad
I'm not sure whether the thread should be deleted or marked solved (Have to figure that one out). The issue is solved though.

Edit: The Windows 7 addition was just an additional test to ensure that the jack was not faulty.

---

### Post by mikewhatever on 2011-07-28
It would greatly help those reading this with a similar problem if you identify your sound card. The machine brand only is a very vague identification, as the same laptops can have different components.

---

### Post by fl00ky on 2011-07-28
> **mikewhatever said:**
> It would greatly help those reading this with a similar problem if you identify your sound card. The machine brand only is a very vague identification, as the same laptops can have different components.

I apologize.

The sound card is:

HDA Intel: Conexant Analog. 

Codec: Conexant CX20583 (Pebble HSF) 


Sorry for the delay. 

PS: Please let me know if anymore information from my end will be useful to others, or if the above information is the right stuff you were looking for. 

Thanks

---

### Post by mikewhatever on 2011-07-28
Perfect, thanks!

---

