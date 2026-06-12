---
title: "[SOLVED] New HP laptop, not much works, help!"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by FuturePilot on 2007-08-16
I just got a new HP dv6500 laptop (Intel Core 2 Duo, Nvidia 8400 GS 2GB RAM) and I'm having tons of trouble getting Feisty to work. I try to boot the CD and the first thing I see is```
PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
```
Then after a while it dumps me into Busybox with ```
Cannot access tty: job control turned off
```
I got it to boot with the instruction from another thread with adding break=top to the kernel and then doing modprobe piix in Busybox. Then after I install I mounted the system and added piix to /etc/initramfs-tools/modules and updated the initramfs but it wouldn't boot afterwards.

I also got it to boot with the all_generic_ide kernel parameter but I still see that PCI error.

I also have no sound. I think it's a Realtek HD audio device. But no sound at all.

Any help? This is depressing.:(

---

### Post by jnorthr on 2007-08-16
Have you tried just running the live cd before installing ubuntu just to see if everything is to your liking ? Would have expected many of these problems to be declared there, just sounds like you are doing a lot of work as ubuntu should run out -of-the-box on a new(recent) machine.

---

### Post by charles.g.moore on 2007-08-16
I used this thread and it helped immensely albeit for Dapper but many things should at least help.

You may not be that far along in your install but eventually the post may help.

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)

---

### Post by charles.g.moore on 2007-08-16
On my dv6000t the sound came from the alsa driver installation, nothing b4 then.

I also get the PCI error, have had trouble hunting down exactly what it has to do with but my sys. runs fine.

I run the 32 bit version with the 686 kernel ( ithink that is what it is)

---

### Post by FuturePilot on 2007-08-16
Well. I've pretty much got everything working except the sound. I had to install the Nvidia driver with Envy but it works. I'm still getting that PCI error but I'll worry about that later since it's at least booting right now. But I still have no sound. I've compiled the latest alsa driver and I've tried everything but still no sound.:( I'm not sure if I have an Intel sound card or a Realtek card.

---

### Post by cmat on 2007-08-16
> **FuturePilot said:**
> Well. I've pretty much got everything working except the sound. I had to install the Nvidia driver with Envy but it works. I'm still getting that PCI error but I'll worry about that later since it's at least booting right now. But I still have no sound. I've compiled the latest alsa driver and I've tried everything but still no sound.:( I'm not sure if I have an Intel sound card or a Realtek card.

Compile the latest ALSA driver and utilities (I'm talking about release candidates) and obtain all the dependencies before hand. Usually fixes all sound problems with Intel cards and Realtek. There are no packages I know of and it would be best to do a tarball compile.

---

### Post by FuturePilot on 2007-08-16
I've compiled 1.0.14. I can't find any release candidates.:confused:

---

### Post by FuturePilot on 2007-08-16
Ok. After hours and hours of searching and trying different things, I have sound!!!
Thanks to this post here
[http://ubuntuforums.org/showthread.php?t=489603&page=2]("http://ubuntuforums.org/showthread.php?t=489603&page=2")
Post#15
and these instructions
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
Now everything seems to be working fine, except I still see that PCI error at boot up and I need to boot with the all_generic_ide kernel parameter, but it seems to be working fine and I have sound!!!\\:D/\\:D/\\:D/

---

### Post by satvanton on 2007-08-18
Hi Guys, 
Same here, got my new hp 6500 dv special edition- vista 64 bit- 4 g ram-200 mem and nivida 8400 graphic card, but i am really upset with the voulme output , can some help me out with i am still in the 15 day period, is there anything can be done or should i need return this laptop back...
regards.
sat

---

### Post by FuturePilot on 2007-08-18
What's the problem exactly? Do you have sound at all? Or is it just too quiet?

---

### Post by satvanton on 2007-08-18
Thank you for your prompt reply. When i play any dvd the voice is not loud enough barely we can able to hear any dialog. 

Regards,
Satvanton

---

### Post by kirios on 2007-08-18
[COLOR="DarkRed"]Hmmm... I'm supposed to get an HP 520 (Core Duo T2050) tomorrow and this thread doesn't sound encouraging. Has anyone used Feisty on an HP 520?[/COLOR]

[http://h10010.www1.hp.com/wwpc/hk/en/sm/WF05a/1090709-1124051-1124051-1124051-12434656-80330282.html]("http://h10010.www1.hp.com/wwpc/hk/en/sm/WF05a/1090709-1124051-1124051-1124051-12434656-80330282.html")

---

### Post by FuturePilot on 2007-08-19
> **satvanton said:**
> Thank you for your prompt reply. When i play any dvd the voice is not loud enough barely we can able to hear any dialog. 

Regards,
Satvanton
Have you compiled the latest alsa drivers?

> **kirios said:**
> [COLOR="DarkRed"]Hmmm... I'm supposed to get an HP 520 (Core Duo T2050) tomorrow and this thread doesn't sound encouraging. Has anyone used Feisty on an HP 520?[/COLOR]

[http://h10010.www1.hp.com/wwpc/hk/en/sm/WF05a/1090709-1124051-1124051-1124051-12434656-80330282.html]("http://h10010.www1.hp.com/wwpc/hk/en/sm/WF05a/1090709-1124051-1124051-1124051-12434656-80330282.html")
Actually I've got it working quite well now. It just took a little more effort than I was expecting. That laptop seems like it should be fine.

---

### Post by satvanton on 2007-08-19
Hi, 
I took three year full coverage , so when i complained this to hp they made me to do lot of things almost like i spent 6 hrs with them and their super was supposed to call me today but never did. I am not sure that i did not do what u mentioned.
sat

---

### Post by popch on 2007-08-19
This sounds a bit silly, but I had to use the volume control in*** two different places*** in order to hear the sound track of my DVDs:

(1) the volume control in the DVD player program
(2) the master volume control in Gnome's top panel (or the hardware keys associated with that function).

I advice not to wear the headphones while doing so the first time.

---

### Post by EXCiD3 on 2007-08-19
> **popch said:**
> This sounds a bit silly, but I had to use the volume control in*** two different places*** in order to hear the sound track of my DVDs:

(1) the volume control in the DVD player program
(2) the master volume control in Gnome's top panel (or the hardware keys associated with that function).

I advice not to wear the headphones while doing so the first time.


Something I was using actually had volume control in 3 places, and this could be why people are experiencing low volumes. One of the locations must have a lower volume set and this would definitely limit maximum output.

---

