---
title: "Biostar a77oe3 Motherboard driver issues"
date: 2011-03-14
forum: Hardware
---

### Post by Crxss on 2011-03-14
I'm using this mobo in my rig running ubuntu 10.10. I saw it as compatible hardware in the sticky, but despite that there's no sound at all. I tried running the driver install on WINE but it told me there was no card supported. I really need some help.

---

### Post by Crxss on 2011-03-14
I juat went through 2 hours of troubleshooting using that comprehensive sound guide on the forums, and with no luck at all. Anyone have an idea of what's wrong? I feel like I've tried everything at this point.

---

### Post by Yellow Pasque on 2011-03-14
See if latest alsa helps: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
If not, use the alsa-info script in that link to post your info.

Oh, and installing windows drivers through wine won't work. Sorry, but I LOL'd at that one.

---

### Post by Crxss on 2011-03-14
I don't know what I'm supposed to do with those scripts, I'm not linux savvy. I set them to be allowed to be used as executable programs, but they just open the terminal and crash.

yes I know windows drivers don't work on linux, but maybe that was the day they magically could've worked lol.

---

### Post by Crxss on 2011-03-14
I used lspci -v to get my audio info if it helps:

Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Biostar Microtech Int'l Corp Device 821f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by Crxss on 2011-03-15
I'm using this page now:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I couldn't figure out what model I have since my computer is built from scratch and isn't a laptop. I have the ALC662 codec which seems to only be used in laptops. I just set model to auto, then restarted alsa, and I got this error a few times before I heard the loud bang noise coming from my speakers as it always does when I turn my pc on or off now; meaning sound still doesn't work..


```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/asa/.gvfs
      Output information may be incomplete.
Terminating processes: 1441
```

---

### Post by Crxss on 2011-03-16
sorry for bumping, but I really need some help here..

---

### Post by Yellow Pasque on 2011-03-16
> **Crxss said:**
> I don't know what I'm supposed to do with those scripts, I'm not linux savvy. I set them to be allowed to be used as executable programs, but they just open the terminal and crash.

Can't really tell you why it's crashing without a log. Even if you don't want to upgrade alsa, at least run the alsa-info script from that thread and post the link to its output. Until then, it's like groping around in the dark (and even with full info, it's sometimes not clear what's wrong).

Oh, and please don't bump more than once a day (that's the staff's rule for this site).

---

### Post by Crxss on 2011-03-16
> **Temüjin said:**
> Can't really tell you why it's crashing without a log. Even if you don't want to upgrade alsa, at least run the alsa-info script from that thread and post the link to its output. Until then, it's like groping around in the dark (and even with full info, it's sometimes not clear what's wrong).

Oh, and please don't bump more than once a day (that's the staff's rule for this site).

It uploaded my info to the alsa site but I don't know where I'm supposed to find my log there. Also, I would upgrade alsa if I knew how to run the upgrade script :/ I'm very new to linux. I set it's permission to run as an executable but all it does is close right after opening.

---

### Post by Crxss on 2011-03-17
figured out how tun run the alsa-info script, here's my link:

[http://www.alsa-project.org/db/?f=fbadc06b34a2670965d56925cfb507da6453c57d](http://www.alsa-project.org/db/?f=fbadc06b34a2670965d56925cfb507da6453c57d)

---

### Post by Crxss on 2011-03-18
anyone think they know what's wrong? I hate having to keep bumping this thread.

---

### Post by Crxss on 2011-03-28
Been a week and still haven't been able to get sound. Any input?

---

