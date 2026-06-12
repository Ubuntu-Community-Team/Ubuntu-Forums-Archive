---
title: "Asus C90S touchpad and keyboard woes."
date: 2008-09-23
forum: Hardware
---

### Post by JMicahGrunert on 2008-09-23
Okay, I've pretty much exhausted all my possibilities for a couple of odd hardware problems.

First, I'm currently running Ubuntu 8.04.1 on my Asus C90S laptop. I was running 8.04, but decided to upgrade as 8.04.1 has the pre-compiled kernel modules for my Intel 4965 wireless chip which I couldn't get running under 8.04 for some odd reason.

However, my problem resolves around my Synaptics TouchPad and the GSynaptics utility I had installed for it. In 8.04, the scroll feature of the touchpad worked out of the box. But in 8.04.1, it doesn't.

I installed GSynaptics to give me some configuration options, but whenever I try to launch it GSynaptics pops up with the error...

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I have set the variable for SHMConfig to true and have tried on and yes, but I still get the same error message.

Additionally, Fn + F9 should turn the touchpad off, but it doesn't do a single thing.

I've tried to find KSynaptics, but it looks like that project is dead an buried. And from what I've glanced thus far, it seems to be a reported bug involving GSynaptics and Ubuntu 8.04.1 for some odd reason.

Perhaps I might have better luck with Xbuntu or another Debian variant.

Any suggestions anyone.

---

