---
title: "sound in ubuntu warty"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by xinelo on 2005-08-09
I've installed Ubuntu online from a Warty 4.10 CD. Everything looks fine, but nothing sounds fine :( When I insert a CD, the CD player works fine, but I hear no sound.

When I try to play an mp3 in Rhythmbox 0.8.5, the message is "Error: There is not connector installed to manage an mp3 file". The radio does not work either, the error message is: "Could not open vfs file [http://whatever:8008/](http://whatever:8008/) for reading" and "Error: Playing could not be paused". Weird.

I searched the tutorials and howtos on the ubuntu site and I found a
HOWTO about this, at http://www.ubuntuforums.org/showthread.php?t=26567&highlight=mixer+device+found$but it couldn't help me. I'll show what I did:

The command

$ lsof /dev/snd/*
$

outputs nothing, so i should assume that no program is using ALSA??

So I decided to follow on and edit the esd.config file, which i did
exactly as the howto says. I restarted my session, but the problem
remains and there is no sound.

I then tried to check the sound volume, but when clicing on Applications
> Multimedia > Volume Control I got an error message roughly like:

"Error: no mixing device and/or element has been found"

I remember the same or a similar thing happening in a previous distro I had (LinEx, Debian-based). I think I never succeeded then.

My sound driver is Sigmatel AC97, but I don't know if this is the model
of my sound card... If not and if this information is necessary, could
you tell me how I can find it out?

The output of "lsmod|grep snd" is

# lsmod|grep snd
snd_intel8x0m          18632  0
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_intel8x0m          18632  0
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  10
snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_$
soundcore               9824  1 snd

I've also checked the option "enable the start of the sound server" in
Sound Preferences.

By the way, I don't know whether this is related, but totem doesn't play
any video file, it says "Totem could not play "file:///media/cdrom0/file". Failed to open: reason unknown".

Neither do I know whether this is related, but I noticed some error messages when booting, about pciehp, shpchp and hw_ramdom...

Btw, my PC is a Dell Inspiron 8500.

Has anyone run into the same problem? Does anyone can help? Many thanks for any potential help :)

xinelo

---

### Post by SKLP on 2005-08-09
Why would you install an old version of ubuntu?

---

### Post by xinelo on 2005-08-10
Because the ubuntu-5.04-install-i386 iso that I downloaded and burnt to a cd and tried to use to install ubuntu would never work. So I had to use the orange install cd that I had been sent before april. I thought I wouldn't matter much because you can always upgrade later (which I'll do when I get to that point in the guide I'm reading... ;) 

Is this related to my problem?

---

### Post by xinelo on 2005-08-10
Problem solved. I downloaded again the Hoary version and this time it got installed! The sound works now :))) 

Take care, xinelo

---

