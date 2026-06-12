---
title: "Not all laptop speakers are working"
date: 2011-05-23
forum: Hardware
---

### Post by sharky44 on 2011-05-23
I have a Dell Inspiron E1705 laptop.  It has some nice integrated stereo speakers with a so-called integrated subwoofer (see [http://www.dell.com/content/topics/topic.aspx/global/products/inspn/topics/en/inspn_e1705_sp_spec?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/topic.aspx/global/products/inspn/topics/en/inspn_e1705_sp_spec?c=us&cs=19&l=en&s=dhs))

The problem is that sound is only coming from the 'subwoofer' on the bottom of the laptop, not from the stereo speakers near the front.  Therefore, the sound is very muffled.  Of course, with headphones, it sounds fine.

I've had Jaunty all the way through Natty and it's been the same issue, even with a reformat.  Any idea how I could enable *all* of my laptop speakers?

# lspci -v
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Thanks in advance for your help!

---

### Post by papibe on 2011-05-23
Maybe they are muted. Try  [alsamixer]("http://alsa.opensrc.org/Alsamixer"). Check [this]("http://www.patheticcockroach.com/mpam4/index.php?p=62").
Run it like this:
```
$ alsamixer
```
Unmute the speakers, test them. When you get the results you're going for, save the settings like this:
```
$ alsactl store
```
Regards.

---

### Post by sharky44 on 2011-05-23
Thanks for the ideas.  There is something weird happening.  When I turn the volume to full blast, it sounds normal (but very loud).  But as I turn the volume level down, the stereo speakers get quiet very quickly, but the 'subwoofer' stays loud, causing the sound to sound muffled.  The different speakers don't seem to be balanced well for some reason.

---

### Post by sharky44 on 2011-05-23
I finally stumbled across this thread which I'm hoping will solve my problem:

[http://ubuntuforums.org/showthread.php?t=1305889](http://ubuntuforums.org/showthread.php?t=1305889)

---

### Post by sharky44 on 2011-05-23
Success.  So there was an LFE channel in alsa-mixer that controls the subwoofer.  Previously, ubuntu would adjust the master, PCM, and LFE automatically when the volume was adjusted.  By following the instructions in the linked thread, the volume only adjusts the PCM and so I can keep my balance between the various speakers.

Solution: [http://ubuntuforums.org/showthread.php?t=1305889](http://ubuntuforums.org/showthread.php?t=1305889)

---

### Post by papibe on 2011-05-24
Good to know! Glad you solved it.
Regards.

---

