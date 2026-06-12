---
title: "No sound, nVidia onboard soundcard"
date: 2005-11-09
forum: General Help
---

### Post by hamil on 2005-11-09
Just having some minor troubles with my soundcard I think.....

Every second bootup, my sound does not work, and today when I got back from school, the sound had stopped working while I was at school.
To get the sound to work again, I have to restart the computer, and the sound works perfect again..

I used Arnieboys "Automatix" to get all the progz and codecs needed, don't know if it has anything to do with that...

Anyway, if i do lsmod | grep snd, I get this result:
```

snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  1
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  3 snd

```

lspci | grep -i audio, gives my this output:
```

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)

```

Both outputs is from when I do not have any working sound on my machine.

Hope that someone is able to help me solve this issue?

Lasse

---

### Post by Teroedni on 2005-11-09
could you give us some more information on what hardware you are using
Hardware and such?

---

### Post by hamil on 2005-11-09
Yes.

The machine is an AMD64 Athlon 3200, running on an Ubuntu 5.10 i386.
The mainboard is an MSI Platinum K8N Neo, in the spesifications it states that it is: AC'97 2.3 compliance.
Further down on the spesification page it says:
Audio: Realtek ALC850 7.1-channel audio codec

In another topic regarding a sound issue, I found that the command: /etc/init.d/alsa force-reload might help me. It stated that all programs using the soundcard would restart.
When I issued the command, my Mozilla-Firefox retarted, and the sound came back on..
But still the issue is not resolved, since the sound goes on and of... And I now have to restart alsa every time the sound goes down..

---

### Post by Teroedni on 2005-11-09
could you try a reinstall,too see if the problem persist?

---

### Post by hamil on 2005-11-09
A reinstallation, is not an option at this point...

---

### Post by Arktis on 2005-11-09
> 
lspci | grep -i audio, gives my this output:

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)

It appears to be onboard nvidia sound, so I assume that means nforce.  Do you have the nforce drivers installed?  That may help.  My onboard sound wasn't even usable until I installed them.  [Here](http://www.nvidia.com/object/linux_nforce_1.0-0306.html) is a link to latest x86 nforce driver installer.  Installation is suprisingly easy.  After that, reboot.  Then be sure to select your sound device from the volume control preferences.  I hope this helps... it might not.  I'm not sure since you appear to already have partially working sound.

---

### Post by hamil on 2005-11-10
Arktis:
It did not turn out just the way I wanted yet....
When i run the nforce.run file, I get to accept the license and everything, but then the installer starts to complain. 
It does not seem like you have a precompiled kernel interface to match your kernel. Make sure you have the kernel source files.

When i enter synaptic, and search for kernel, I find this one:
"Linux kernel source for version 2.6.11 with Debian patches"
But it is not marked with the Ubuntu symbol. Is it safe to install this one, and is that all the nforce depends on? Is there anything else to do?

Thanx!

---

### Post by Arktis on 2005-11-10
Don't get that package.  It's not even the same kernel version that breezy ships with anyways.  ;) You need to have the linux-headers package installed for the kernel you are using.  For example, if you are using the default 386 kernel, you need linux-headers-2.6.12-9-386.  Also, you need build-essential, gcc-3.4, gcc-3.4-base, and cpp-3.4.  Then before you run the installer, you need to change compilers like this:
```
export CC=gcc-3.4
```

---

### Post by Teroedni on 2005-11-11
Hmm i wonder i i actually got the same problem myself
When i starting xmms in My Turion machine(which have  ac850 codec just as you i get an message once or twice which states it cant find my soundcard
but the third time i click on it it goes ok:P

But i get it only in xmms not in xine or cdplayerfrontend.hmm


Could you check if you can activate sound via xmms by cliking on play 2-3 times
?  Anyone else have the same problem?

snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
snd_rawmidi            25056  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
snd_intel8x0           33344  0
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm

---

### Post by hamil on 2005-11-13
> Could you check if you can activate sound via xmms by cliking on play 2-3 times?


Tried this, not working... 
Anyway, when this problem occures, it is not only in xmms. I have tried to open music/video etc in totem/mplayer and vlc, but no sound there either. 
The problem have not occured the last days. So I have not tried to install the nforce installer again. A wise man thought me once, that I should not mess with something that worked... :) But the next time the sound dissappears again, I will try it at once..

---

### Post by Arktis on 2005-11-14
Isn't it funny how sometimes problems just mysteriously go away?  Glad to hear it.

---

### Post by hamil on 2005-11-15
yupp... :)
But it is nice...

Almost one week without any kind of trouble, so I think it has mysteriously dissapered... I have not upgraded or installed anything at all, so I do not understand why the problem disappered.. But it is working like a charm again! :D

---

### Post by garba on 2005-11-15
had a few problems with alsa and my soundstorm myself, say thanks to oss and alsa clashing against each other (backwards compatibility with stuff from the early seventies is a must, you know :smile: :rolleyes: ), discover in my case seemed to have a hard time picking the proper module to load... well at least this was the problem i was having... anyway, i would reccomend you try compiling your own kernel (it's not that hard) and get rid of discover, give it a try, it worked for me

---

### Post by grendel_khan on 2005-11-15
Just a note: the ID from lspci that showed up refers to, according to [the current pci.ids](http://pci-ids.ucw.cz/iii/?i=10de00ea), an "nForce3 250Gb AC'97 Audio Controller". You might want to send a note to the maintainer, containing the output of lspci -vvv and the details of the hardware you're using, so that the next person to run into this problem will have an easier time of it.

---

