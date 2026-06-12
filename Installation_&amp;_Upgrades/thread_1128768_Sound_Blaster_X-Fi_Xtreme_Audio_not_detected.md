---
title: "Sound Blaster X-Fi Xtreme Audio not detected"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Chew N Tobacca on 2009-04-17
I have installed Ubuntu Studio 8.10 64-bit on a friend's computer. So far, we have no sound. Other than that, things are great. I've been around the forums & other linux forums, and nobody seems to be having the same issue.

It seems as though the card is not really being detected by the operating system. It shows up if I run "lspci":

```
04:00.0 PCI bridge: Creative Labs Device 7006
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>
	Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs Device 0018
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at fdafc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```
Obviously the card is being recognized. Plus, we have a dual-boot with Windows XP, and it works great there. But when I run "aplay -l" in a terminal, I get this:

```
fifelon@arenus:~$ aplay -l
aplay: device_list:215: no soundcards found...
fifelon@arenus:~$ 

```

And when I run "asoundconf list", I get nothing at all:

```
fifelon@arenus:~$ asoundconf list
fifelon@arenus:~$ 

```
In addition, PulseAudio does not find the sound card at all. If I open the PulseAudio manager, there are no options for anything there. It simply tells me that there are no devices available.

I have been getting mixed feedback from the web amongst my research. Some people say that the chipset itself is not an X-Fi Xtreme at all, but rather it is an Audigy chipset. This is somewhat confusing also.

Has anyone else had this problem? I appreciate any input or suggestions anyone has for me.

---

### Post by Chew N Tobacca on 2009-04-19
Mostly a quick nudge in hope to get a solution.

However, I have heard that by default Intrepid does not support this family of Creative Labs soundcards; Hardy, according to rumor, should just fine. I am downloading Hardy as we speak, so I will find out...

---

### Post by Bowl of rice on 2009-07-22
I have a Creative Sound Blaster X-Fi external USB sound card. It works fine with Windows Vista, but my house is primary Mac so I prefer an Ubuntu box. The driver I found on the Creative website says it supports the Sound Blaster. Looking deeper it list every other version of the sound blaster but the X-Fi. Does anyone know if this was left out of the text or if it is not supported. When I just ran it from the Ubuntu Live CD the sound would not work. 

To the person above, what where you findings? Have any advice?

---

### Post by eternalsword on 2009-07-22
My guess is hardy will not work.  You may need to upgrade to latest alsa release.  Depending on what type of x-fi card you have, you may even need to get bleeding edge from git.  There are various scripts around that can help you upgrade, or if you're fortunate you can find a ppa.

---

### Post by Bowl of rice on 2009-07-22
Is there a way to find out if it is being worked on? Pardon my ignorance, how could I find out?

---

### Post by eternalsword on 2009-07-22
you should ask on alsa-user list (details at [http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)) or on the #alsa channel at irc.freenode.net on irc.  If you don't know what irc is, see [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat) for some irc clients.  You'll need to read docs on that particular client on how to connect to servers and join channels.  One client that's not mentioned there is ChatZilla ([https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16)), which is a firefox extension.

---

