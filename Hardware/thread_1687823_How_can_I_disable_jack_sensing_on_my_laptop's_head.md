---
title: "How can I disable jack sensing on my laptop's headphone jack?"
date: 2011-02-14
forum: Hardware
---

### Post by CasualObserver on 2011-02-14
The sensing "switch" in the headphone jack on my laptop is broken.

Under normal conditions, when you plug a set of headphones into the jack, the built-in speakers are disabled and sound only comes through the headphones. When you remove the headphones, sound then returns to the built-in  speakers. That doesn't happen anymore.

Now, whether or not headphones are plugged in, the onboard speakers never omit any sound.

I know for a fact that the speakers and the sound hardware are all fine. The headphones still work when plugged in, and I can still hear the fancy POST sound when I boot up.

After digging around on the internet, I came across a registry tweak for Windows 7 (I dual boot) that ignores the state of the sensing "switch" in the headphone jack. I just need to figure out how to do the same thing in Ubuntu.

Does anyone know how I can "disable" or ignore the sensing switch in the headphone jack? I'm currently running 10.04.

Any help will be greatly appreciated.

Thanks!

---

### Post by CasualObserver on 2011-02-24
I've been able to work-around my problem by using a different driver that allows muting of the speakers and the headphones independently. Here's what I did on Ubuntu 10.04 for my Asus G51JX-A1:

Find the name of your sound chipset

```
cat /proc/asound/card0/codec#* | grep Codec
```

mine returns:

```
Codec: Realtek ALC663
```

This is the name of your soundcard chipset. Lookup that chipset here:

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

You will hopefully get a list of options like I did:

```
ALC662/663/272
==============
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  asus-mode7	ASUS
  asus-mode8	ASUS
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)
```


Now edit your alsa config file:

```
sudo nano /etc/modprobe.d/alsa-base.conf
``` 

adding this line to the very bottom of the file.

```
options snd-hda-intel model=XXXX
```

Change XXXX to one of the values in your list, (like "auto" for example)

Save your changes and reload alsa:

```
sudo alsa force-reload
```

Now test your sound:

```
speaker-test -Dplug:surround51 -c6 -twav
```

Make sure you have the appropriate sound sources turned on in the mixer. Sometimes they'll all be muted by default.:

```
alsamixer
```

 If your sound still isn't working, then try a different value from your list for XXXX. Save. Reload. Test. You might have to try alot of different values before you find a value that works. There's no guarantee that any of them will work though, but hopefully one of them will.

Hopefully this will help someone else. It's taken me three weeks to find a solution to this problem.

Good luck!

Note: I pieced together my solution using these threads:

[http://ubuntuforums.org/showthread.php?t=1316880](http://ubuntuforums.org/showthread.php?t=1316880)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ellaivarios on 2011-06-20
> **CasualObserver said:**
> The sensing "switch" in the headphone jack on my laptop is broken.

Under normal conditions, when you plug a set of headphones into the jack, the built-in speakers are disabled and sound only comes through the headphones. When you remove the headphones, sound then returns to the built-in  speakers. That doesn't happen anymore.

Now, whether or not headphones are plugged in, the onboard speakers never omit any sound.

I know for a fact that the speakers and the sound hardware are all fine. The headphones still work when plugged in, and I can still hear the fancy POST sound when I boot up.

After digging around on the internet, I came across a registry tweak for Windows 7 (I dual boot) that ignores the state of the sensing "switch" in the headphone jack. I just need to figure out how to do the same thing in Ubuntu.

Does anyone know how I can "disable" or ignore the sensing switch in the headphone jack? I'm currently running 10.04.

Any help will be greatly appreciated.

Thanks!


[B]Hi,

I'm looking to do the same thing, but for an entirely different reason. I want to be able to have control over and switch on and off whether audio output comes out of my laptop speakers and the green headset jack simultaneously, because my laptop has a subwoofer and two speakers and with the two extra speakers from the headset (they are tiny and USB-powered, but powerful), I will have a neat little audio surround-like system while sitting in front of my screen, plus it will increase quality significantly and volume (almost double it) 

I'm interested in finding the tweak for Windows 7 you mention. Also, if you have found a simpler way to do this for Ubuntu Linux, I'd appreciate you pointing me in the right direction. I Will try your suggestion here and will let you know if it worked for me.

Thank you!
[/B]

---

### Post by gunshotdigital on 2011-07-04
Hi

Go in control panel and select Sound icon...

Disable the headphone  and click on built-in speaker to make sure that they are activated. That's it.

edit...it is a feature...You can even mute it..

---

