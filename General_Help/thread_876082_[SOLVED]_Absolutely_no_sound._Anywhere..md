---
title: "[SOLVED] Absolutely no sound. Anywhere."
date: 2008-07-31
forum: General Help
---

### Post by Saul Hudson on 2008-07-31
I've recently installed Hardy Heron onto my PC, my first Linux :P

Since the install I have been unable to get my computer to produce any sound. I have run through the comprehensive sound guide, and tried many other 'half-solutions' that I've found. I've managed to tie myself into so many knots I don't know whether I'm coming or going. I have completely reinstalled Linux, as I felt that I'd messed with too many settings without knowing what I was doing.

I wanted to avoid posting on the forums as it is such a vague request that I feel stupid for asking, but here I am anyway, eventually.

Any help would be greatly appreciated. If you ask for information about my hardware, please tell me how to obtain that information as well.

Thanks.

---

### Post by hessiess on 2008-07-31
please post
```

lspci
```

---

### Post by loboc on 2008-07-31
> **hessiess said:**
> please post
```

lspci
```

and 
```

lsmod | grep snd

```

---

### Post by Saul Hudson on 2008-07-31
```

~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:09.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

```

$ lsmod | grep snd
snd_hda_intel         344728  2 
snd_hwdep              10500  1 snd_hda_intel
snd_mpu401              9448  0 
snd_seq_dummy           4868  0 
snd_mpu401_uart         9728  1 snd_mpu401
snd_ca0106             36192  2 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            25760  3 snd_mpu401_uart,snd_ca0106,snd_seq_midi
snd_ac97_codec        101028  1 snd_ca0106
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                78596  4 snd_hda_intel,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24836  2 snd_seq,snd_pcm
ac97_bus                3072  1 snd_ac97_codec
snd_page_alloc         11400  3 snd_hda_intel,snd_ca0106,snd_pcm
snd                    56996  23 snd_hda_intel,snd_hwdep,snd_mpu401,snd_seq_dummy,snd_mpu401_uart,snd_ca0106,snd_seq_oss,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd

```

---

### Post by loboc on 2008-08-01
Looks like you have two sound cards and only the onboard intel one is getting its drivers loaded, 

1
```
 aplay -L 
``` will list the devices alsa knows about, if your soundblaster card is not there try finding out which module should be loading at alsa-project.org look for the supported soundcard matrix link.  

2
Do you have pulseaudio installed it might not be communicating with alsa right?

3
```
 alsamixer 
``` will let you unmute the cards.  Sometimes with a fresh install all the cards are muted by default

---

### Post by Saul Hudson on 2008-08-02
```
aplay -L
``` did indeed show two cards, one of them was an NVidia, so I'm assuming the other is my Creative Labs one. It was referred to as CA0106 in the terminal and after searching on alsa-project.org, I found that CA0106 seemed to be the drivers for a similar card, the Audigy SE, and there was a different chipset for the LS. In spite of this, both links went to the same page and the instructions there also failed to help me, so I guess that's irrelevant.

I don't know if this is just me being picky but my card was described as an SB Audigy LS by Ubuntu, and I could only find an SB LS on the alsa-project lists... is it possible my card isn't actually that one, and does that mean it isn't supported by alsa?...

Pulseaudio is installed, although I haven't touched it, so if there is a way of playing with the settings in there, I haven't tried that (version 0.9.10-1ubuntu1, if that's helpful).

And I've unmuted everything it'll let me unmute inside alsamixer, still to no avail.

Thanks for your reply.

---

### Post by loboc on 2008-08-03
pulseaudio havs a couple of utilites that are all acessiable from an applet that you can get using synaptic or apt-get 

padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pavucontrol - PulseAudio Volume Control
pavumeter - PulseAudio Volume Meter

Open a terminal 

Install those and run the padevchooser by 

```
 padevchooser& 
```

a little headphone jack icon should show up in your tray 

Click on it and open the manager. You should see the screen shot below  

If pulse isn't running you'll see a message about being unable to connect to the server

For whatever reason my pulse did this and did not start automatically from the boot scripts, so in the terminal window I had to type 
```
pulseaudio&
```

then in the manager window click connect


If that works for you add /usr/bin/pulseaudio to your start up programs as a fix to whatever is keeping it from being started when the computer boots.

---

### Post by jocko on 2008-08-04
> **Saul Hudson said:**
> ```
aplay -L
``` did indeed show two cards...

Three things to try (I assume you want to use the soundblaster card, not the integrated nvidia):
1. Look at the output of:```
asoundconf list
```You should see both of your soundcards listed. In which order are they listed?
If the nvidia card is listed first, it will be used instead of your soundblaster.
To fix that:
```
asoundconf set-default-card *[COLOR=Blue]name_of_card[/COLOR]*
```Where *[COLOR=Blue]name_of_card[/COLOR]* is the name of your soundblaster as it was written in the output of asoundconf list.
This fix will only work for the user that runs the command (as the settings are stored in the /home folder).
You may need to log out and in again to see if this works.

2. Set modprobe to prevent the nvidia card from being set as first card:
```
gksudo gedit /etc/modprobe.d/alsa-base
```Add this line to the end of the file:
```
options snd-hda-intel index=-2
```You'll need to reboot for this to have any effect.

3. Prevent the driver for the nvidia card from ever being loaded (if you don't need it):
```
gksudo gedit /etc/modprobe.d/blacklist
```Add this line to the end of the file:
```
blacklist snd-hda-intel
```You need to reboot to see if this worked.

---

### Post by Jack-Frost on 2008-08-04
I've had this happen on my other linux computer. You may just be missing FLASH on your firefox, or desktop. Try to see if you can get it from ADD/REMOVE PROGRAMS. If that doesn't work, try

Sudo apt-get install flash

It worked for me. 

Or it may just be that you may have to update your linux when some components come out. That worked for me as well.

---

### Post by Saul Hudson on 2008-08-05
loboc,

I tried to install all those packages and I already had all of them installed apart from the Device Chooser. I checked the manager and there was no error messages, it was connected to the server, so I assume that it's working correctly.

jocko,

I'm just desperate to get any sound out of my computer, so I'm quite happy to use any soundcard available to me, it just seemed that using the Creative Labs one would be most convenient. It turned out that the Creative Labs one was set to default anyway, so I tried what you mentioned but changing it to the NVidia instead of the other way around. And this didn't help either.

Jack-Frost,

Flash is installed and working (just silent obviously!), and I hope waiting for new components isn't the answer, as my system is completely up to date at the moment.

Thanks for all your responses.

---

### Post by Saul Hudson on 2008-08-05
Also... 

I just put a radio station on and checked the PulseAudio Volume Meter, and it shows a fluctuating volume, so it thinks it's working.



Hardware fault. Bought, and installed, new soundcard and everything worked instantly.

---

