---
title: "Low sound volume with Intel card"
date: 2009-05-19
forum: Hardware
---

### Post by tdjb on 2009-05-19
I've been searching the forums but haven't found a solution to my problem yet. I have a Dell Inspiron 1545 with an Intel sound card running Ubuntu 9.04. For whatever reason the volume is super low even when I have it all the way up in the mixer. I've set the "front" and "pcm" levels to 100%, but that still doesn't solve the problem.
Any ideas on what might be the problem? In the process of trying to figure out what's wrong I ran the alsa information script and the results are posted here: [http://www.alsa-project.org/db/?f=693fd4fe0d93c75e5a0eb10e589825b678db5b5d](http://www.alsa-project.org/db/?f=693fd4fe0d93c75e5a0eb10e589825b678db5b5d)

Here is the output of lspci:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 02aa
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

The only option I have added to alsa-base.conf is:
"options snd-hda-intel model=3stack"

Thanks in advance.

---

### Post by benerivo on 2009-05-22
I don't know what the problem might be with alsa, but i also found the volume slightly low on my laptop. I installed oss as a replacement for alsa, and the top volume was significantly louder. See [this page]("https://help.ubuntu.com/community/OpenSound").

---

### Post by brianfactors on 2009-05-28
I have the same laptop, and I also have a problem with sound. Two problems, in fact:

1) Sound volume. dito. Compared to the volume I get in Vista, Ubuntu's volume is VERY low. I have gotten it so that it's high ENOUGH, though. I'd just rather have the option of cranking it higher.

2) Playing multiple items. For some reason, certain items such as totem and Rhythmbox can play at the same time, but other software such as VLC, Adobe Flash, or Skype block other programs out or get blocked from the sound. So, for example, I'm playing my music on Rhythmbox and I get a call on Skype. Skype can't access my sound. I shut down everything using sound, just restart Skype, and it works. Wierd...

I've only been using Ubuntu for about a year and a half, and I just got this laptop, so I'll let you guys look at lspci.

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
Seems I have the same sound card.

I reinstalled ALSA from source. Didn't do very much for me.

I found this. Didn't help me much, though: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Oh, I'm using the 64 bit version. Does that make a difference?

---

### Post by brianfactors on 2009-06-02
I solved the second problem using this:
[http://www.linuxtent.com/?p=236](http://www.linuxtent.com/?p=236)

Just get rid of PulseAudio. ALSA and OSS is apparently good enough by itself.

Oh tdjb,

I have gotten a high enough volume for it to be worth it. Unfortunately, not as high as in Vista, but still high enough to be worth it.

I don't know if you've done this or not, but you could install Gnome ALSA Mixer, which gives you more things to turn up. :-)

```
sudo apt-get install gnome-alsamixer
```I sure hope this helps somebody.

---

### Post by LCDolph on 2009-08-01
I got rid of pulse audio and ALSA and installed OSS.  The osstest works and when I play a video or sound file bars appear in the mixer but no sound comes through my speakers.  Any ideas? osstest sounds quite loud, so if I could only figure out how to get everything else playing.  I'm a total linux newbie too

---

### Post by thychamp on 2009-08-02
I have this laptop as well.  I used this site which got my sound to work.  [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

While all applications that play sound work, I pretty much have to have the volume to the max all the time, because it is relatively low.  Once the volume shows about half volume you can't hear anything.

---

### Post by Tosh78 on 2009-08-30
I have exactly the same problem. I have volume but the volume is too low. Does anybody have a clue on how to solve this?

---

### Post by brhad56 on 2009-09-02
I uninstalled pulseaudio as several posts I've read suggested, but this did not work and i reinstalled it. I fixed this problem by using kmix alone.  Apparently, in addition the the default channels, Front, Surround, Center, LDE, PCM, etc...  There are OTHERS that are hidden.  So In KMix, I clicked on Settings->Channels and then put a checkbox by Master Front and clicked OK.   Slid the bar on the new visible Master Front volume and sound got louder.  Hope this helps someone else.

---

### Post by agrobanko on 2009-09-25
a tip here, many programs can amplify the audio, for example in mplayer try:
mplayer some_audio_or_video_file -softvol -softvol-max 600

---

### Post by Tosh78 on 2009-09-26
Try installing Kmix. I did that and it works fine now.

---

### Post by brianfactors on 2009-10-17
I tried out Kmix, (actually already had it installed) but I don't know why you would do that unless you're using kde. It didn't really have any more sliders than the gnome alsamixer.

---

### Post by brianfactors on 2009-11-08
Hey everyone, BTW, I have just downloaded Karmac and volume seems to be just great. Thanks for the great update, guys! The multitasking with flash/gnome seems to be fixed too. Perhaps there's still a problem with Skype... haven't tested.

At any rate, thanks for the great update, guys!

---

### Post by arunerd on 2010-02-15
thanks very much...my sound has improved a lot.

---

### Post by TracyO on 2010-02-28
Same problem.  Specifically, I recently installed 9.04 and noticed the sound issue.  I have a Dell Inspiron 1525.

I was having trouble hearing sound (music, podcasts, radio) from my kitchen 15 feet away from the speakers with all the volume adjustments to the max.

Installed Kmix, and turned my PCM up all the way, and that's helped immensely.  Thanks all!

---

### Post by Tosh78 on 2010-02-28
Hi All. I upgraded to 9.10 and all my sound issues dissapeared. Keep that in mind.

---

### Post by laupsavid on 2010-03-22
Going to rant a bit here. Sorry.

I did a ridiculous amount of searching to find the answer for my computer (Asus M3N78-VM motherboard), and I wished I had read this thread first. Mine was fixed by installing alsa-mixer to adjust the volume as an early poster said.

Don't know why that isn't in the install by default. Seeing literally hundreds of posts of sound being too quiet for the last several iterations of Ubuntu, you'd think the tools that fix this would be added to the default package.

I got apparently expert advice on how everything in Ubuntu is now PulseAudio and that's what you have to control. And how in 9.10 it "just works." No, it didn't "just work" and so that was no help.

I read several blogs and posts on this site also which said "adjust PCM" which was meaningless to me. Also, stuff about "equalization" which never mentioned what software does this. Lots of people pulling on controls and fixing the problem by right-clicking and selecting things that just didn't exist in my brand-new, default 9.10 install.

If you look "PCM" up, you get a lot of incomprehensible stuff to read, and scary warnings about how "only a sound engineer can modify this" and so forth.

Finding out that what many people were talking about was "alsa-mixer" consumed a lot of time. Why can't people just say what they used to fix things instead of being so vague?

Also don't know why the Ubuntu comprehensive sound problem post is four years out of date. But all I can do is complain, not being expert enough to help rewrite it at all.

Okay, enough, and thanks much to the person who finally came out and said "alsa mixer" clearly and in public so that people could know what it was called so they could use it.

---

