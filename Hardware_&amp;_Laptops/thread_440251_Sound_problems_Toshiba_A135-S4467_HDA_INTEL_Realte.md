---
title: "Sound problems: Toshiba A135-S4467 HDA INTEL Realtek ALC861-VD"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by dsbeav on 2007-05-11
When I installed both Ubuntu and Kubuntu 7.04 I had no sound with:
Toshiba A135-S4467
Card HDA Intel
Chip: Realtek ALC861-VD

I googled the problem and the only solution I could find was adding the following line to my /etc/modprobe.d/alsabase file:

options snd-hda-intel position_fix=1 model=3stack

This made the sound work, but when I put headphones in my pc speakers still play.  I played around with KMIX and could not fix the problem.  Also, I can't get my microphone to work.

If anyone has an idea I'd appreciate it!

thanks

---

### Post by ekmandyn on 2007-05-12
Hi there,

I finally fixed my volume problem using your suggestion..Thanks!!!. In the beginning my headphone sound wasn't working either but in the volume control>switches I checked the headphone box and that fixed that problem,

Now my Toshiba A135-S4407 is totally functional (Sound, Video, wireless, etc) with ubuntu feitsy:) :) :) :) :)

---

### Post by Jad on 2007-05-13
Dude, 
I have new Toshiba Tecra A8-103 and I have same problem, would you please explain how did you solve your problem?

---

### Post by dsbeav on 2007-05-14
> **Jad said:**
> Dude, 
I have new Toshiba Tecra A8-103 and I have same problem, would you please explain how did you solve your problem?

Did you try editing: 

/etc/modprobe.d/alsa-base

by adding the following line at the end:

options snd-hda-intel position_fix=1 model=3stack

This got my sound up but my pc speakers still play when I have headphones in and I also cant get my microphone to work. 

I'm not exactly sure what that means.  I think it means that the priority of my sound card is changed from 2 to 1 and I think the seconds part changes the driver for the chipset.  I'm not sure though.

Also, go to the command line and type:

alsamixer

This will give you your sound card and your chipset. This will help troubleshoot your problem.

---

### Post by Jad on 2007-05-14
dsbeav, 
I already have that line in my alsa-base and already unmuted everything using alsamixer but it didn't work.

---

### Post by mostholy on 2007-05-14
I'm with Jad in the sense that I've added the line to alsabase and unmuted things in alsamixer but am still without sound.  I'm running Toshiba A135-S4527 which has the same sound hardware in question.  I'm jealous of ekmandyn as their system seems to be sound functional while mine is not.

---

### Post by mattmyers83 on 2007-05-15
I have a Toshiba A105-S171 with the same problem.  I have a AC97 Realtek chipset I believe.  From what i can see Alsa thinks my modem speaker is my sound card.  I have not found out how to fix this issue yet.

---

### Post by Jad on 2007-05-15
Sounds like we were choosed to feel with deaf people.

---

### Post by dsbeav on 2007-05-15
> **mattmyers83 said:**
> I have a Toshiba A105-S171 with the same problem.  I have a AC97 Realtek chipset I believe.  From what i can see Alsa thinks my modem speaker is my sound card.  I have not found out how to fix this issue yet.

That's probably a valid assessment.  That might explain why my sound plays through my headphones and also the mic doesn't work.

---

### Post by Jad on 2007-05-15
I really can't understand why we still have such silly problem in Linux

---

### Post by zanjabeel5 on 2007-05-15
I have the same soundcard this solved my problem.
just copy & paste the stuff

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

also look at the last comment here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107821](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107821)

---

### Post by Jad on 2007-05-17
I tried both mentioned solution and surprisingly it didn't work

---

### Post by dsbeav on 2007-05-17
> **Jad said:**
> I really can't understand why we still have such silly problem in Linux

When hardware providers start opening up their drivers little problems like these will diminish.

---

### Post by Jad on 2007-05-17
dsbeav, 
I understand this but as !developer I will always keep believing that there should be a way to overcome such issues.

---

### Post by hmjgriffon on 2007-05-17
> **dsbeav said:**
> When I installed both Ubuntu and Kubuntu 7.04 I had no sound with:
Toshiba A135-S4467
Card HDA Intel
Chip: Realtek ALC861-VD

I googled the problem and the only solution I could find was adding the following line to my /etc/modprobe.d/alsabase file:

options snd-hda-intel position_fix=1 model=3stack

This made the sound work, but when I put headphones in my pc speakers still play.  I played around with KMIX and could not fix the problem.  Also, I can't get my microphone to work.

If anyone has an idea I'd appreciate it!

thanks

That totally fixed my sound!!!! You friggin rock man I was about to go back to the pain of edgy eft, man you couldn't have don't that fix in windows closed source crap haha! I get the same problem though sound coming out everywhere when I plug headphones in. There must be something else in this file that we can modify to make it work totally right.

---

### Post by ekmandyn on 2007-05-17
I really don't know why in my case the sound works only adding the line 

options snd-hda-intel position_fix=1 model=3stack 

to the etc/modprobe.d/alsabase file. 

First I tried many things though, maybe the combination of those finally work. The first thing I did was allowing to all the users use the sound. Then I reinstall the alsa drivers, I also got the gtstreamer with the codecs to watch DVDs.

Sorry that I'm not being very specific but I don't remember exactly how I did all that. However, I found all the information in this forum.

PD: I was wrong about my headphones, they are working but I got the sound by the speaker and headphones at the same time.

---

### Post by Serjudo on 2007-05-17
my solution:

1. Edit /boot/grub/menu.lst
2. Add this option to the adequate entry: acpi=ht
3. Reboot

My sound card is the alc861 vd and works ok!!

good luck!

---

### Post by dsbeav on 2007-05-18
> **ekmandyn said:**
> 
PD: I was wrong about my headphones, they are working but I got the sound by the speaker and headphones at the same time.

I have the same problem. Let me know if you find a solution.  I'll post one if I find one. 

Thanks!

---

### Post by dracflamloc on 2007-05-18
Adding that line worked for me on my A135-S4487

Thanks guys!!!

---

### Post by Jad on 2007-05-18
dracflamloc, 
you're lucky!

---

### Post by cmat on 2007-05-18
Compile the latest (like the RC version) ALSA drivers and utilities. I had the same problem with that hardware and it works great now. Make sure you compile it in the root console oppose to prefixing sudo. 

```
sudo -i
``` 

will give you the root console. make sure you have the required headers and dependencies.

```

cd /directory of extracted files/
./configure
make clean;make;make install

```

then restart your system. the sound is muted by default.

---

### Post by dsbeav on 2007-05-19
> **cmat said:**
> Compile the latest (like the RC version) ALSA drivers and utilities. I had the same problem with that hardware and it works great now. Make sure you compile it in the root console oppose to prefixing sudo. 

```
sudo -i
``` 

will give you the root console. make sure you have the required headers and dependencies.

```

cd /directory of extracted files/
./configure
make clean;make;make install

```

then restart your system. the sound is muted by default.

I recompiled my alsa-base, alsa-lib and alsa-utils using the Realtek patch.  (I don't remember the version, but it was upto date as of 2 days ago)  This made my sound work, except for the headphones play through the speakers and the only volume control that works through alsa mixer is front.  Did you have similar problems after you patched alsa-base?

Thanks!

---

### Post by mostholy on 2007-05-19
thanks so much zanjabeel5, the first link you provided to the LaptopTestingTeam did the trick for me: I now have sound and am very happy.  Ended up having to recompile alsa but the step-by-step was enough to walk me thru it.  Sound was muted by default and a quick adjust to that and reboot and I was greeted with the ubuntu startup sounds I've only heard described.  

Cheers

---

### Post by Beamo.fr on 2007-05-25
I had the same problem on Toshiba P200-157

adding the line : options snd-hda-intel model=3stack
got the sound working but putting headphones I also get sound on both (speakers and headphone)

Beamo

---

### Post by Jad on 2007-05-25
Same here it's working with headphones but I really hate listening to anything with headphones or at least I want my freedom back!

---

### Post by mostholy on 2007-05-27
okay, the sound works, now the details... The headphones get sound but so do the speakers, just started looking into this but would appreciate the obvious fix.  

My sympathies to jad as I've seen too many posts of frustration on the whole sound issue.

---

### Post by stuman on 2008-04-02
Because, new hardware drivers are engineered with Micro$oft during product development, since the hardware comes with M$ psys loaded.  Alternative OS's are deveoped after the hardware hits the market.

Newer is not necessarily better, but that doesn't seem to matter.

---

