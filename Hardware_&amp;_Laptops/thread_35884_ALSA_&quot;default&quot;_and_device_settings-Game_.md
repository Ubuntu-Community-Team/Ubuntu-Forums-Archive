---
title: "ALSA &quot;default&quot; and device settings-Game theater xp"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by Dittohead on 2005-05-20
This is a bit complicated so bear with me ;)

I just moved from Gentoo so some conventions used in ubuntu (and I guess debian too) are a bit foriegn to me, I've only used debian for a few hours before this, and ubuntu never. I'd heard a lot of good things about ubuntu so I decided to give it a try for a while to find out. I'm quite impressed.

My sound card is the Game Theater XP, based on the cs46xx series of chips. It's worked quite well under other other distros, or at least to a degree (LFE/surround worked but I had to make the app out put to either surround, LFE or front, not all at the same time).

I've only got two sound cards installed in this system, one is the onboard nForce stuff and the other is the Game Theater XP:

```
$ lspci | grep audio
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)
0000:02:08.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
```

Before I knew there were problems with audio I went ahead and made sure things were unmuted. They were but I first realized I was going to have problems when I noticed the device we had detected was "Realtek ALC655 rev 0 (OSS Mixer)" As I mentioned, I don't have a Realtek card, just the nVidia (which I don't use) and the GTXP. I went to file->change device... and was a little irked to find 4 devices:

Realtek ALC655 rev 0 (OSS Mixer)
Cirrus Logic CS4294 rev5,Cirru (OSS Mixer)
NVidia CK8 (Alsa Mixer)
CS46xx (Alsa Mixer)

I changed the device to CS46xx (Alsa Mixer) and unmuted all the apporiate channels and turned them up to 50%.

In the "System->Prefs->Sound" dialog and in the Sound Events tab hitting play failed to warrent a response in my speakers.

I then went to System->Prefs->Multimedia Systems Selector and noticed that ESD was picked for both Audio output and input. (either that or it was OSS...I can't remember).

If I hit "test" with OSS or Alsa I get this error message (replace XXX with either OSS or ALSA):

*Failed to construct test pipeline for 'XXX'*

If I select ESD it claims to be testing, however I don't get any sound.

I installed BeepMediaPlayer and started playing an OGG file after I set it to run through Alsa for output and made sure it was outputting to the CS46xx (hw:1,0). It worked!! However the "default" listed in the audio device combo box wouldn't play.

I once again set Multimedia Systems Selector output and input to alsa and launched rhythmbox...I then added my sample mp3 and gave it a try:

*ALSA device "default" is already in use by another program.*

Hmm, it seems that the "default" doesn't work. Hence my problems earlier, for some reason "default" isn't mapped to a functioning device, thus it craps out when trying to create a pipe to it. Or so that's my understanding.

I guess what I need to know is how to remove or edit alsa devices. I'm also wondering how I can get it to output to the subwoofer (LFE) as well...I was able to get it working by making the alsa output plugin in BMP (If at all possible I'd like to use rhythmbox from now on) to output to hw:1,3, which was the LFE.

Thanks for taking the time to read this and help me out, it's really the only thing left before this desktop is working 100%!

---

### Post by Dittohead on 2005-05-21
OK, I fixed it...sort of.

I created /etc/asound.conf with the following:

```
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

```

Though I still can't output to my LFE/surround speakers...

I disabled it in BIOS as well, then changed default to say "card 0".

I got my sound working over all the speakers via pcm.ch51dup and pcm.duplicate (in /etc/asound.conf so it's a global setting) that I found in the (alsa) wiki, and set gstreamer-properties to device=pcm.ch51dup (or duplicate). The sound is very crackly and when the CPU is in use it's even worse! The problem occurs in XMMS/BMP as well, though not as bad. When it outputs to stereo on "default" it works just fine. Any ideas why and how to fix it?

---

