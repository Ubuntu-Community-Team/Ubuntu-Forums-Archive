---
title: "Trouble with m50vm-a1 laptop, Im new to Ubuntu"
date: 2008-12-05
forum: Hardware
---

### Post by SmoothCorn on 2008-12-05
Hello,

I have m50vm-a1 laptop, and just installed Ubuntu 8.10 on it. There are two problems: no sound, no wireless.

I am completely new to ubuntu, so I dont know where to start looking. I went to the ubuntu documentation site, and searched the forums, but the amount of information is overwhelming.

I see that some people also experienced similar problems on this laptop, but I couldnt really understand how they solved the problems, since Im so new to this. Is there a page with a list of guides of how to install ubuntu on different laptops?

I would really appreciate it if you offered me some assistance.

Thanks in advance :)

---

### Post by utnubuuser on 2008-12-05
Hi -- Here's a thread:
> [http://ph.ubuntuforums.com/showthread.php?t=87257](http://ph.ubuntuforums.com/showthread.php?t=87257)
apparently same problems solved using this open sound documentation:
> [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by SmoothCorn on 2008-12-05
Many guides tell me to go System > Administration > Networking

I do not have Networking there. Instead I have network tools, what could be the problem?

Thanks

---

### Post by Gilles.t on 2008-12-05
hi!

I have also an asus M50VM
for sound problem you should follow instructions on this post:

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

if it seems to complex to you post the output of this command
cat /proc/asound/card0/codec\#* | grep Codec
I may provide you a partial fix

The wifi works for me "out of the box"
Can you post the result of lspci command?

Gilles

---

### Post by utnubuuser on 2008-12-05
You might also check System>>Administration>>Hardware Drivers

Anyway, sounds like Gilles' got your back

---

### Post by SmoothCorn on 2008-12-10
Hello, thanks for your replies.

My internet is now working, but I still cant get sound to work.

When I type in aplay -l heres what I get:

device_list:215: no soundcards found...

When I type in lspci -v heres what I get:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1893
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

Is this normal, Is that really my sound card?

I tried installing the alsa drivers, and reinstalling the drivers like it says in the comprehensive sound problems solutions guide on this forum and no result.

Also, when I type in the command that you suggested "cat /proc/asound/card0/codec\#* | grep Codec", here's what I get:
cat: /proc/asound/card0/codec#*: No such file or directory

Thanks for your help. :)

---

### Post by SketchyClown on 2009-02-01
SmoothCorn,

Just wrote this for someone else, now I'll offer it to you too.

I have the M50VM-A1 as well.

Mine has the Intel HDA soundcard.

lspci gives me:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Now, my sound didn't work either out of the box. I left the sound preferences all at default. If you right click the sound icon in the panel and open the volume controls I made sure they were all checked and maxxed out for starters, then I found this:

[http://www.linlap.com/wiki/Asus+M50VM](http://www.linlap.com/wiki/Asus+M50VM)

"Sound works in ALSA with “options snd-hda-intel model=3stack-dig” to the file /etc/modprobe.d/alsa-base."

I added that line to the alsa-base and presto, sound works flawlessly.

Hope this may help you.

---

