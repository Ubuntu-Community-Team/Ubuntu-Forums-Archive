---
title: "Dell Studio 1558 with I5 Processer"
date: 2010-03-23
forum: Hardware
---

### Post by Si2100 on 2010-03-23
Can Linux Ubunut run on Dell Studio 1558 with 64bt Processor?

i tryed before and found that the sound driver failed any ideas?

---

### Post by Glenn Louttit on 2010-03-26
Hi. 
I have a dell 1558 i5 also.  Currently running Lucid lynx 10.04 reasonably successfully. Sound is working, wireless works. however, do not touch the volume controls on the key board as this seems to lock the whole panel tool bar. Because this is still an alpha version, it is still being developed, but at least some things that did not work in 9.10 work in 10.04.
Hope this is helpful

---

### Post by openxs on 2010-04-20
> **Glenn Louttit said:**
> Hi. 
I have a dell 1558 i5 also.  Currently running Lucid lynx 10.04 reasonably successfully. Sound is working, wireless works. however, do not touch the volume controls on the key board as this seems to lock the whole panel tool bar. Because this is still an alpha version, it is still being developed, but at least some things that did not work in 9.10 work in 10.04.
Hope this is helpful

I did find a recent post that solved the volume control problem, the guy who posted this said it worked for him, I've yet to get around to trying it, here's the link: [http://ubuntuforums.org/showthread.php?t=974723&page=6]("http://ubuntuforums.org/showthread.php?t=974723&page=6") Good luck

---

### Post by Si2100 on 2010-04-29
Hi Guys,
i've just reload ubuntu and got no audio...

whats is the driver for the IDT Audio? for linux....

---

### Post by Zorrothustra on 2010-05-06
Confirmed, sound buttons work fine on the official 10.4 release.

---

### Post by openxs on 2010-05-13
> **Si2100 said:**
> Hi Guys,
i've just reload ubuntu and got no audio...

whats is the driver for the IDT Audio? for linux....

Hi, only just seen your post. My audio worked out of the box, this is the output from lspci -k:

2:00.1 Audio device: ATI Technologies Inc RV710/730
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Hope you have it working by now.

---

### Post by Glenn Louttit on 2010-06-02
Hi. My Dell 1558 seems to be working fine now, audio controls work, even have sound in a virtual box running windows 7 (only because I have a program that only runs on windows).
I do have one new problem. It seems that my wireless internet, after having worked fine for all this time does not now want to connect. It recognises that there is a network there, the password and evertyhting are correct, but after trying to connect it keeps on coming up saying that it is unable to connect.
Any suggestions?
Thanks

---

