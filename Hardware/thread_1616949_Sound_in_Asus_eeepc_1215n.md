---
title: "Sound in Asus eeepc 1215n"
date: 2010-11-08
forum: Hardware
---

### Post by blink0 on 2010-11-08
Hey guys,

I just got myself a brand new 1215n eeepc and, since it comes with windows 7, installed linux via wubi (I plan to upgrade to a real linux soon enough).

Anyway, after getting wired and wireless networking running, I am now trying to get the sound to work. I followed the steps under [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) , produced the info file (for your viewing pleasure under [http://www.alsa-project.org/db/?f=049030e5237a4db4abc0fc1f6a8c76cf47f3f3f4](http://www.alsa-project.org/db/?f=049030e5237a4db4abc0fc1f6a8c76cf47f3f3f4)) and everything seems to be working fine, still no sound!

Oh yeah, none of sound sliders is muted :)

Any ideas?

Thanks in advance!

ps: the microphone seems to be working, by the way, since the little slider in Sound Options moves when I make a sound.

---

### Post by blink0 on 2010-11-09
So, after following the aforementioned sound troubleshooting guide, I ended up adding the "options snd-hda-intel model=auto" line to /etc/modprobe.d/alsa-base.conf . With this in place, I can now:

- Hear music etc, as long as I plug in a headphone to the output jack (the internal speakers do not work).
- Use the internal microphone (the plug-in mic jack doesnt work).

I also installed the pulse audio volume control (pavucontrol) and I see that if I play a sound, even if I do not hear anything (without a headphone plugged in), the Playback slider moves (ie. it detects that a sound is being played). 

Any ideas?

---

### Post by samuelalexdev on 2010-11-09
Hi there,
which version of alsa do you have?
cat /proc/asound/version
make sure it's the latest 1.0.23
if it's not the is an updater script for the alsa drivers 
here you find the procedure it's quite simple
[http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810")
Let me know what happened :)

---

### Post by sunset on 2010-11-09
Hey I'm very interested in the 1215N and will look forward to any reports you can offer as to how things go.  Specs for this thing look really nice.

Sound/mic issues (mainly for Skype) are important to me.  Did you have to do anything special for networking, video etc.?  Good luck, and keep us posted!

---

### Post by blink0 on 2010-11-09
OK so after updating linux with the latest packages kernel etc, the sound stopped working... Following samuelalexdev's tip (thanks!), I updated to alsa 1.0.23 and now the headphone sound (through the jack) is working, as well as the microphone (both the internal one and with an externally connected one). All that it's left not working are the internal speakers!

By the way, I didnt mention my pc stats (ubuntu version, alsa version, etc) because every necessary piece of information appears in the link I gave ( [http://www.alsa-project.org/db/?f=049030e5237a4db4abc0fc1f6a8c76cf47f3f3f4](http://www.alsa-project.org/db/?f=049030e5237a4db4abc0fc1f6a8c76cf47f3f3f4) ).

To finish, all works but the internal speakers. The only thing I see in the dmesg log worth mentioning is (I think) the line: 

ALSA hda_codec.c:337: hda_codec: connection list not available for 0x24

Any ideas here?

@sunset:
yeah, when I finished installing linux, there was no wired or wireless connection. Googling around, I realized that you must install the wired interface's driver manually. You can find it here: [http://www.opendrivers.com/driver/2117587/atheros-ar8152-ethernet-driver-1.0.1.9-linux-free-download.html](http://www.opendrivers.com/driver/2117587/atheros-ar8152-ethernet-driver-1.0.1.9-linux-free-download.html) . After that, Ubuntu offers to install a proprietary "Broadcom STA Wireless Driver".

When it comes to video, I read in many places you can't activate the NVIDIA drivers or else you'll get a permanent black screen when booting. You can deactivate this card all together with [https://github.com/peberlein/acpi_call](https://github.com/peberlein/acpi_call) to save up 30% of energy (according to the comments, I haven't measured myself).

As for Skype, after getting the sound to work, it seems to work fine, although I only made some calls to the sexy british accented "Skype Call Testing Service" girl.

---

### Post by blink0 on 2010-11-09
OK skype suddenly stopped working, as in, it doesnt make any sound anymore...

I get this in syslog:

Nov  9 16:11:50 ubuntu pulseaudio[1324]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

---

### Post by sunset on 2010-11-09
So you're on 10.04?  First thing I'd do is install Maverick (perhaps Netbook Edition).

---

### Post by IcarusR on 2010-11-09
Did you try adding

```
options snd-hda-intel model=your_model
```

to /etc/modprobe.d/alsa-base.conf as documented in the SoundTroubleshooting page you linked ? 
This seems to resolve a few intel sound issues.

---

### Post by blink0 on 2010-11-09
@sunset: upgrading as we speak, I'll get back soon

@IcarusR: yeah, I tried all that guide said, so I have "options snd-hda-intel model=auto" (since I couldn't find the proper model for this laptop and the ALC259 codec).

---

### Post by samuelalexdev on 2010-11-10
From my expirience at this point just remove what you previously added to alsa-base.conf and it should work :) try commenting # snd-hda-intel model="auto"
and see if it works

---

### Post by blink0 on 2010-11-10
Yeah, I should've guessed that the upgrade would screw the system up lol... Get a very weird error with the latest kernel and can't get X with the 2nd latest...

Anyway, I'll start over again, install a brand new Ubuntu 10.10, see how it goes and if necessary, follow the steps I did before (luckily I wrote everything down). I'll get back later to you guys!

Thanks for all the help, by the way ;)

---

### Post by blink0 on 2010-11-10
OK, good news: with a brand new Maverick install, everything works OOTB!

Well, kinda. The Wired card was working, so I used it to update the OS and get the wireless card driver (a proprietary Broadcom one).

The sound works fine, but the microphone is muted by default. So I installed pavucontrol, unmuted it and now all is fine! (including skype).

The "shutdown nvidia script" also works fine, and the power consumption went from around 14W to around 11W! Now I just need to figure out how to set the module to load at boot-time, any ideas? I read that u need to put it in /etc/modules, but where shall I put the .ko file then? And should I then run the script (to call the module and turn off the card) with a normal init script?

---

### Post by sunset on 2010-11-10
Nice! =D>

Whatever commands you used to load the module and run the script, I guess you could add those to /etc/rc.local.

Oh and how's the graphics performance?

---

### Post by 5hark on 2010-11-13
I also have Asus 1215n and Ubuntu 10.10 with latest updates and sound work sometimes and sometimes it does not without any reason

---

### Post by Tryfon on 2010-11-15
Hello, I just installed Ubuntu 10.10 on my new Asus 1215n and after all the updates I get no sound output at all. I can't see anything muted by default, everything seems to be configured fine, but no sound.

Anybody has the same problem?

---

### Post by Tryfon on 2010-11-16
Well, this time I have sound. It seems that it is behaving randomly. Same like 5hark.

Any help appreciated.

---

### Post by shendai on 2010-12-12
Has anyone heard of any improvement on this issue?  I've been using Ubuntu since ver 8.04, and I've not encountered such an aggravating intermittent issue yet.  Sound sometimes works, sometimes not.  Log files aren't providing anything useful.  It's bizarre and should be fixed.  I'm booting more into Win7 because of this as I just want things to work, and it's just sad to have to do that.  Also - Ubuntu 10.04 does not support ethernet on this netbook out of the box.  Manually adding the driver is not difficult but every time a kernel update happens the driver needs to be recompiled.  Again, irritating.  New Linux users are not likely to be patient with this behavior.

---

### Post by LtPitt on 2011-01-15
I have absolutely the same problem and same netbook...

I have 10.04 updated to latest kernel, installed manually wi fi lan...
Everything was perfect until, after a reboot, sound stopped working.

As the friend a few posts above mic is perfectly working and audio card is working ONLY from earphones but I get no sound from internal speaker.
Tried all the listed solutions in this tread without having success... :(

Any hints?

---

### Post by LtPitt on 2011-01-16
You guys will not believe it but the solution's here:

[http://ubuntuforums.org/showthread.php?t=1633284](http://ubuntuforums.org/showthread.php?t=1633284)

---

### Post by LtPitt on 2011-01-22
Definitely NOT fixed :/ sometimes when I boot the audio cripples and pc hangs on... I have to turn it off elettrically :/

---

### Post by LtPitt on 2011-02-02
Anybody has my same problem? :(

---

### Post by ikeluiz on 2011-03-19
I have the same problem, i have ubuntu 10.10 on my asus 1215n but i have sound after configure /etc/modprobe.d/alsa-base.conf with option snd-hda-intel , but the sound is very sux, and the microfone and speakers don't work, just home teather works if i put the headphone the sound has a hiss, so if a configure like option snd-hda-inte model=basic this model in theory this configuration should work.

But now the speakers work but the microphone and audio output does not work without mentioning that the sound is distorted with a junk certain types of beats.

I have a theory that the hdmi video card is interfering with the sound in some way because if I fit the vga cable or hdmi, a low hiss that ends well.

I tried compiling the driver directly from the website realteck could compile but no sound I was after that, I really do not know what else to do, the video accelerator does not work is one thing but the sound does not work there's no way, I was disappointed with this netbook.

Please someone help me make the sound work if not I'll sell it and buy a netbook compatible with the gnu / linux. :(

---

### Post by charstring on 2011-07-29
Got sound to work ok on Ubuntu 11 by installing the proper alsa drivers:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

