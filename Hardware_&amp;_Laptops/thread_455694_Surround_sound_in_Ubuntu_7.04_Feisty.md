---
title: "Surround sound in Ubuntu 7.04 Feisty"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by voxel on 2007-05-26
I have an Alienware Area51m laptop that has 4 channel audio, and I have never been able to get my 2 'rear' (mounted under the LCD) speakers working under Ubuntu, I tried everything using the Volume Control settings.

But when I recently installed 7.04 and hit up ubuntuguide.org to help me get set up with the essentials like flash, java, codecs, etc... I discovered a section under Hardware -> Sound called [How to setup the surround speakers (5.1 and others) with ALSA]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA")

The only thing I had to change was 
```
slave.channels **6**
```
to
```
slave.channels **4**
```
to reflect my 4 speaker setup... and VOILA, it worked like a charm! I had music pumping out of all 4 speakers and it sounded great!

But the next time I was on YouTube, I noticed that every video I played had a really bad 'crackling / skipping' sound to it... So I disabled the ~/.asoundrc hack, and low and behold... No more crackling/skipping

Has anyone else had this issue? I would love to have my 4 channel audio working, but the sound on flash videos is just too annoying to justify it :(

---

### Post by vasilis34 on 2007-05-28
Hi!!
U r not alone!!!

I have the same problem too with a Hercules Fortissimo III 7.1 soundcard. In fact I have sound cracklings general while playing with VLC. U have that problem only with flash videos?
Also, regardess the player (I tried also totem and rythmbox) my PC acts like been heavy loaded even on playing mp3s at 'normal' bitrates as 128bps. After making several efforts i switched to default sound. I think ,although i don't know if it is correct, that the solution proposed in [www.ubuntuguide.org](www.ubuntuguide.org) tries to duplicate sound on the rear speakers and so places a heavy load to the CPU. Using htops i can see a 99% load on the CPU occasionally while just playing music with rythmox. 
In preferences->sound &#921; can  see among others, 4 options regarding my sound chipset. CS46xx, CS46xx rear, CS46xx Center LFE and CS46xx IEC 958. So, I guess that the solution would be to compose all these "cards" at one and then use it, and not trying to duplicate the signal to the rear speakers. Well, that's just a thought I don't know anything on how to accomplishe it. I wish someone more relevant with ALSA and generally sound could provide us with some hints. I am stuck with 2.1 for now being :(

---

### Post by voxel on 2007-06-01
Hi vasilis34,
Yeah I've also noticed a higher than average CPU load when running the 4-channel audio hack... I'm assuming the way the hack is implemented must use proportionally more CPU time.. eg: 7 channels > 4 channels > 2 channels..
When I am at home I usually have my laptop 'docked' and plugged into my stereo system... So I guess I can live with it, but I would still love to be able to enjoy 4.0 channel audio when out and about! :) Glad to know I'm not the only one experiencing this problem. Also, I can't confirm if the problem was only on flash videos, it was just the only time I noticed it; I'm not sure if I even played any videos in Totem/VLC while having 4 channel enabled..

---

### Post by Rice_slayer on 2007-06-04
IT WORKED!!!! SWEET JESUS IT WORKED!!!!! I FINALLY HAVE SURROUND SOUND BACK!!! You  dont know how excited  I am!!!!

---

### Post by voxel on 2007-06-04
Glad to hear it, Rice_slayer :)
do let us know if you have any of the issues mentioned above, though

---

### Post by vasilis34 on 2007-06-04
Good for u rice_slayer!!!!!:D

Have you managed to get away with the crackling/stopping of sound too? Plz tell us the way u enabled suuround sound. Was it with the .asoundrc hacking described at [www.ubuntuguide.org](www.ubuntuguide.org) ? And let us praise the Lord all together ..!!!:D




PS: I didn't mention that sometimes I observe sound delay between the front and rear speakers, too. It sounds like echo. At least, this is a kinda funny bug....!!!

---

### Post by Rice_slayer on 2007-06-04
No cracking/ popping to report! It runs smoother than XP does imo. My setup for surround is a SOundblaster Live 24bit internal PCI card and Z530 Logitech speakers. I hate to create the .asoundrc file. I tried the EXACT same thing in edgy 6.10, but had no success but now it works flawlessly. All of my complaints towards Linux are gone, it is now my 100% OS, only if I could play Crysis and other DX10 games when they come out...

For videos i have noticed, you can have only 1 sound application running. I have tried to running an MP3 and then run a video but the video says something about media being used. I dont care, At least i have surround sound.

---

### Post by rchan on 2007-06-05
hello folks,

i have the same problem with the crackling sound in vlc ever since i enabled my 4.1 surround sound.  however, when i play movies, i find that gxine doesn't skip and plays perfectly when i have the hack enabled.

my only gripe about gxine is that i can't multitask with a movie running because its always has focus with the keyboard....

hope this helps... 

- ray
happy newbie ubuntu user

---

### Post by rootkowski on 2007-06-07
Hi there!

I just found this post, i immediatly went to the feisty guide, created the .asoundrc file, restarted the system and... YES, THERE IT WAS!!! SURROUND SOUND!!! ALL 6 CHANNELS!  It's a really lovely feeling having the sound come from all 6 loudspeakers. Before there was never sound coming from the centre. 

Anyway, my happiness was short until I discovered the sound no longer worked in skype. Sure I got disappointed but I started playing a bit and I got it working again. This is how: in skype i chose OSS instead of ALSA and then did the same in System/Sound for Audio Conferencing both Sound playback and Sound capture. I restarted the system and all now works great! 

I hope this will be helpful for someone!

another happy newbie ;-)

Edit:
I almost forgot about the noises from your loudspeakers. Sorry. Have you tried muting the microphone or at least mic boost? for me that was the reason.

---

### Post by Rice_slayer on 2007-06-07
For some Reason, it doesnt work anymore! WTF happened, it worked fine last night, its to do with the Asound file as I deleted it and my sound worked, but only woofer+ 2 front speakers. Will 5.1 EVER work right!

---

