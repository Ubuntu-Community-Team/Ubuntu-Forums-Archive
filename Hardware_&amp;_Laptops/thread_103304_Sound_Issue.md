---
title: "Sound Issue"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Creeper on 2005-12-13
Okay first off I would like to say I'm still kind of new to Linux so sorry if I get confused.

Okay well recently I was trying to tweak my sound because it was a bit choppy. Well I went into Synaptic and found libsdl1.2debian-oss was selected. Well sense I was using ALSA for sound I figured I should change it. Well after I did My sound stopped wroking. so I changed to libsdl1.2debian-all but still no sound. I changed it back to OSS but I still don't have sound. 

Do any of you know what I did to mess it up? I don't get any sound at all. In totem I get the error "This is an audio-only file, and there is no audio output available."

Everything is plugged in and should be working fine. 

If it helps I have an Audigy Sound Blaster Live 24 bit. It was working fine before I changed the file.

Thanks in advance for the help.

---

### Post by kairu0 on 2005-12-13
Two questions:

1. Are you trying to fix choppy sound in games? (I just thought I'd ask because you mentioned sdl packages.)

2. Have you tried changing the Multimedia Selector in the Preferences menu (at the top of the screen on the Gnome panel)?

---

### Post by Creeper on 2005-12-13
[QUOTE=kairu0]Two questions:

1. Are you trying to fix choppy sound in games? (I just thought I'd ask because you mentioned sdl packages.)
[/QUOTE]
Well when I first was playing with them I was trying to fix choppy sounds in songs. But now I just want any sound.

[QUOTE=kairu0]
2. Have you tried changing the Multimedia Selector in the Preferences menu (at the top of the screen on the Gnome panel)?[/QUOTE]

Yes, I've tried all of the output devices in Sound Selector.

---

### Post by Creeper on 2005-12-19
Sorry for the double post but can anyone help me? Not to seem pushy but I would really like working sound.

---

### Post by ArmadaEnder on 2005-12-19
I'm having a somewhat similar problem. I just installed Ubuntu on on old tower of mine and I'm getting sound but only when the volume on my speakers are turned all the way up and yet it's only bearly hearable when I put my ear to the speaker. Just to clear this up, the volume in Ubuntu is all the way up and not on mute, that I made sure of. 

Does anyone know if I need to download a plugin for the volume to go up or know of a program that can assess the problem? Thank-you. 

This is on Breezy 5.10 btw. I did a search for sound problem and it brought me here.

---

### Post by Creeper on 2005-12-20
Well I get no sound what so ever on mine. 
I think you'll get better help if you make a new board on Breezy board.

---

### Post by Yoshimitsu8 on 2005-12-20
I have the exact same problem ArmadaEnder. I have all my stuff maxed out and all I hear is just a little bit of sound when I do something. It is really odd because this just happened one day out of the blue when I was running Hoary. Yesterday I upgrade to Breezy and now I'm still having the same problem. I completely reinstall it from scratch. I also know that my sound card and headphones work fine because I have a Office XP OS install on the same box and sound works fine for it. I have tried all sorts of different combinations in the open volume control and preferences for the little sound icon in the top right. I have also tried different combinations in the System>Preferences>multimedia system selector, still nothing.
HELP!!!

---

### Post by kairu0 on 2005-12-20
[QUOTE=ArmadaEnder]I'm getting sound but only when the volume on my speakers are turned all the way up and yet it's only bearly hearable when I put my ear to the speaker.[/QUOTE]

There are several volume settings that can affect your speaker output. Have you checked PCM? Have you tried raising Front, or even Headphone?

---

### Post by kairu0 on 2005-12-20
[QUOTE=Creeper]Well when I first was playing with them I was trying to fix choppy sounds in songs. But now I just want any sound.[/QUOTE]

Do you have the libesd-alsa0 package installed? Make sure it is there and then change the Multimedia Selector preference to use ESD.

Make sure that you have these other packages, too:

alsa-base, alsa-utils, gstreamer0.8-alsa.

---

### Post by Gandalf on 2005-12-20
can you please post the output of
dpkg -l |grep alsa

---

### Post by Yoshimitsu8 on 2005-12-20
Did of all that, still no luck. Any other thoughts?

---

### Post by Yoshimitsu8 on 2005-12-20
[QUOTE=Gandalf]can you please post the output of
dpkg -l |grep alsa[/QUOTE]

How do I do that?
<- = N00b

---

### Post by Gandalf on 2005-12-20
[QUOTE=Yoshimitsu8]How do I do that?
<- = N00b[/QUOTE]
Open Terminal (Applications -> Accessories -> Terminal) when it opens type
```

dpkg -l |grep alsa

```

note it's an l (like Laura) after the -

---

### Post by Yoshimitsu8 on 2005-12-20
ii  alsa-base                              1.0.9b-4 ALSA driver configuration files
ii  alsa-utils                             1.0.9a-4ubuntu5 ALSA utilities
ii  gstreamer0.8-alsa                      0.8.11-0ubuntu5 ALSA plugin for GStreamer
ii  libesd-alsa0                           0.2.36-1ubuntu5 Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                     1.8.7-1ubuntu1 Portable Windows Library Audio Plugin for th

---

### Post by Gandalf on 2005-12-20
alsa-oss is missing for you, go back to the same terminal and type
```
sudo apt-get install alsa-oss
```

try if sound is working now (you may need to reboot), if not then try to
```

sudo dpkg-reconfigure alsa-base alsa-utils gstreamer0.8-alsa libesd-alsa0 libpt-plugins-alsa alsa-oss
```

this should fix it

---

### Post by Yoshimitsu8 on 2005-12-20
Hmm tried both of those and still no luck. 

I was looking around at other forum and I'm wondering if I should have the file libao.conf (/etc) set to alsa rather then esd. I tried this but it didn't work, but I haven't tried it after I did the two commands you just put out.

Any other thoughts on why it doesn't work?

hmm esd is giving me this also (it gave me this before and after your commands)

king@King:~$ esd
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
king@King:~$

Here is some more information:

king@King:~$  lsof /dev/snd/*
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 7606 king   36u   CHR  116,0      6442 /dev/snd/controlC0
xmms      7635 king    8u   CHR  116,0      6442 /dev/snd/controlC0
king@King:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
king@King:~$

lol I hope you can figure this out because I have no clue. By the way, thanks a bunch for helping me!

---

### Post by Gandalf on 2005-12-20
yes because it is already running, hmm let's try
```

sudo apt-get install --reinstall alsa-base alsa-utils gstreamer0.8-alsa libesd-alsa0 libpt-plugins-alsa alsa-oss

```

---

### Post by Yoshimitsu8 on 2005-12-20
Trying right now...

---

### Post by Yoshimitsu8 on 2005-12-20
YES YES YES!!!! IT WORKS!
Wow thanks so much Gandalf you are my hero!

---

### Post by ArmadaEnder on 2005-12-21
My sound works now! But I still only have it through my left speaker but I found that that's because my mobo is crappy and I need to get a sound card. Thank you so much Gandalf!

---

### Post by anarchist_hippy on 2005-12-21
I think I have a problem with this... 

I can have sound from xmms (with alsa), but there is no sound from others... :( 
My sound card is ALC850 O/B, Mainborad is Asus K8N, CPU AMD 3000 64+... 

Any ideas?

---

### Post by Gandalf on 2005-12-21
You're welcome guys, i'm glad it worked for both of you...

[QUOTE=anarchist_hippy]I think I have a problem with this... 

I can have sound from xmms (with alsa), but there is no sound from others... :( 
My sound card is ALC850 O/B, Mainborad is Asus K8N, CPU AMD 3000 64+... 

Any ideas?[/QUOTE]
is esd running? what you mean by others? can you be more specific please?

---

### Post by DJStillman on 2005-12-21
Hey all:

Been following your thread very interestedly, as my Audigy 2 ZS is not giving me good sound.  If I use the sound mixer where it defaults, on Audigy 2 [Unknown] (Alsa Mixer), the only thing that will affect my sound is the master channel.  If I switch devices (Why is there more than one?), to SigmaTel STAC 9721,23 (Oss Mixer), I am able to change sound with Volume Channel (Mono??), and PCM.

Now, If I try to play a movie with Totem, the volume is crappy low, and I have to max out the sound everywhere, and have my speakers turned up.  If I have been playing XMMS and had it turned up, it is better, but still not great, and it seems that it has turned up PCM volume on the SigmaTel device.

I am using Breezy, have done all Gandalf recommended for reinstalling, and it made no difference.  Maybe it is just what I am used to with Windows, but changing the volume in an app only changes the volume there, and not on the sound board.  I see that there are several items to choose from on the Multimedia Panel, but have no idea what they do exactly.

So:

1. Why two devices with only one sound card?
2. Should XMMS be changing PCM on the Volume control?
3. What sink and source should I be using? 
[INDENT]**Sink -> ALSA, Artsd, ESD, OSS, Custom**[/INDENT]
[INDENT]**Source -> ALSA, ESD, OSS, Silence, Custom**[/INDENT]


Thank you for your help.

David

---

### Post by Yoshimitsu8 on 2005-12-22
Hmm my sound stopped working again...

I tried the reinstall of all the things again, but that didn't fix it. I'm sure if either the upgrade to the newest linux kernal (it was a critical update) or if rebooting caused sound to die again.

It is really odd as well because in Volume Control if I turn on the IEC958 2: thingy then I hear a bit of sound, but it is distorted, quiet, and staticy.

Any sugguestions?

---

### Post by Gandalf on 2005-12-22
That's kinda weird, are you sure you did install --reinstall to all alsa packages?

---

### Post by Yoshimitsu8 on 2005-12-22
This is what I ran:

king@King:~$ sudo apt-get install --reinstall alsa-base alsa-utils gstreamer0.8-alsa libesd-alsa0 libpt-plugins-alsa alsa-oss

Did I miss something?

---

### Post by Creeper on 2005-12-22
Sorry for not replying sooner. Holiday rush.

As for my dpkg -l |grep alsa output

```
ii  alsa-base      1.0.8-4ubuntu4 ALSA driver configuration files
ii  alsa-modules-2 1.0.8-4ubuntu4 ALSA driver modules
ii  alsa-oss       1.0.7-1        ALSA OSS-compatibility application wrapper
ii  alsa-source    1.0.8-4ubuntu4 ALSA driver sources
ii  alsa-utils     1.0.8-1ubuntu1 ALSA utilities
ii  libesd-alsa0   0.2.35-2ubuntu Enlightened Sound Daemon (ALSA) - Shared lib
ii  libwine-alsa   0.0.20050310-1 Windows Emulator (ALSA Sound Module)

```

---

### Post by Yoshimitsu8 on 2005-12-22
YES! works again, hopefully permentely this time.
I did the reconfigure thing and that fixed it.
THANKS!

---

### Post by Yoshimitsu8 on 2005-12-23
Stopped working AGAIN!
Ok this is really frustrating and it makes no sense. Currently I have multimedia system selector (audio) set as ALSA for both output and input (I tried other cobo's and nothing worked). I don't know if that matters at all.

I have tried the reinstall and reconfigure probably each 5 times now (different combinations of using the commands as well) and restarted about 10 times.

It is really odd to because when I right click on my sound icon (top right) and go to preferences my Ensoniq AudioPCI (Alsa Mixer) keeps on showing less and less things. It is down to showing only 3D Control - Center; 3D Control - Depth; Capture.

This I find rather strange and if I remember right each time my sound dies it looks like the "master" on this list goes aways. Before using the commands fixed it, but not any more, if anything the commands are making it worse!

Help!

---

### Post by Creeper on 2005-12-24
Hmm I took out my sound card and I have sound again. So either my sound card died or somehow became incompatible with my computer.

---

