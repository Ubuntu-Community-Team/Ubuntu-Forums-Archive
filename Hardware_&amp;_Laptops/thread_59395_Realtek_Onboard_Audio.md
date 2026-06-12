---
title: "Realtek Onboard Audio"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by Jvaldezjr on 2005-08-23
I have an EPOX 9NDA3J Motherboard that has an 8 channel Realtek ALC850 onboard device that uses AC'97 sound driver.  When I hook up my 5.1 speakers to all the correct inputs (Center, Front, Rear) my system plays sound back, but I'm not getting surroudn sound.  Instead Im getting only 2 channel audio, as if I have 2 speakers.  I've been researching the issue, but I have not been able to find a decent solution.  I've got Alsa working, but Ubuntu doesn't seem to know that I'm hooking up 5.1 speakers, and instead I'm only getting 2 channel sound.

I dont know if this is an ALSA issue and I need to recompile ALSA, or if this is a Realtek issue.  They have drivers on their site, but I can't get them to install correctly.  I'm not even sure if I have the right sound device.  Here's the info

```
modinfo soundcore
filename:       /lib/modules/2.6.10-5-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.10-5-386 preempt 386 gcc-3.3
depends:
srcversion:     4CCBC38AF44D1461882C573
```

```
lsmod | grep snd
snd_bt87x              12612  0
snd_intel8x0           29984  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  7 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_bt87x,snd_intel8x0,snd_pcm
```

Heres the code from lspci...A lot of NVidia devices are unknown...I don't know if it has anything to do with this issue, but maybe someone can help me understand the stuff I put in these code boxes.

```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f2 (rev a2)
0000:02:08.0 Multimedia audio controller: VLSI Technology Inc Thunderbird (rev 06)
0000:02:08.1 Input device controller: VLSI Technology Inc Thunderbird
0000:02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

Now I have an ATI TV tuner card attached, and I believe that is the snd_bt87x device, so the only conclusion I can think of is that the snd_intel8x0 is the device for my on board audio.

Any help would be greatly appreciated.

---

### Post by DancingSun on 2005-08-23
I have the Realtek ALC850 audio codec as well.  While I do have a 4.1 surround sound system, I can only get surround sound via a coaxial SPDIF connetion, which I have no idea how to enable in Ubuntu.

That being said, I did notice that by default, in the Volume Control applet, surround sound channels are muted in the ALSA sound device.  You'll need to select Edit --> Preference from the menu and check off the surround sound channels, then you can unmute them.

---

### Post by Jvaldezjr on 2005-08-24
Yea Ive done that, but no dice...its like the system doesnt know that the audio controller has 8 channels instead of 2.

---

### Post by Jvaldezjr on 2005-08-25
I'm still having trouble...why is this so much a pain in the ass?  I've installed the drivers from the Realtek website, and still nothing.  It still sounds like I have damn 2 channel audio.

---

### Post by benqbasic on 2005-08-31
Hey i also have the same onboard sound.
Did you guys come up with a solution?

Im just about to go out and buy a new sound card im sooo feed up ](*,)  with only having single channel.

---

### Post by DancingSun on 2005-08-31
While finding a way to enable my SPDIF output connection, I've stumbled across some tips on enabling sound.

Mute IEC958 related volume controls, and see if that helps.

Also, most audio streams only have 2 channels, were you testing with the proper audio streams?

---

### Post by Septor on 2005-08-31
If you are using mplayer, try:
```

mplayer -channels 6 dvd://

```

---

### Post by benqbasic on 2005-09-02
Hmmm,

I got my sound working. All 8 channels of it. :grin: 

I went in to "alsamixer" and enabled everything. (well not the mic and dat)

Hope this helps.


Ben

---

### Post by M7S on 2005-09-02
Getting 5.1 surround  to work was harder than I thought  ](*,), but I think I'm almost there now.  :) I just need a little help. 

As suggested on this forum, I've been fiddling around with alsamixer and gnome volume control, and I've been able to get my rear speakers to work. I still have some problems with my center speaker and subwoofer. Since my motherboard (Asus K8N-E deluxe with 8ch audio) doesn't use the mic jack as center/subwoofer jack, but has two different jacks. When I turn of "Mic as Center/Subwoofer" in alsamixer and test with ```
$ speaker-test -c6
``` I get sound out of center and subwoofer, but when I use ```
$ speaker-test -c6 -Dsurround51 
``` alsamixer automatically turns on "mic as center/subwoofer" and I won't get any sound out of my center speaker and subwoofer. Illogically enough, my rear speakers seem to work even if "line-in as surround" is on.

So, what should I do to stop "mic as center/subwoofer" from becoming activated every time I use the surround51 device?

Sorry if my english isn't as good as I would like it to be...

Regards,
M7S

---

### Post by M7S on 2005-09-03
Aah. I got it fixed on my own.

In /usr/share/alsa/cards I found NFORCE.conf. That file contained a section NFORCE.pcm.surround51.0 and in that section I found these lines:
```
					name "Mic As Center/LFE"
					preserve true
					value true
					lock true
					optional true
``` 
I changed it to:
```
					name "Mic As Center/LFE"
					preserve true
					value off
					lock true
					optional true
``` 

Then I restarted asla
 ```
sudo /etc/init.d/alsa restart
``` and then it worked!

I hope this could help someone with similar problems. Now I will watch some DVDs :D

Regards,
M7S

---

