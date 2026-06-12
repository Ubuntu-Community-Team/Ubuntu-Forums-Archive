---
title: "Gateway Laptop, no sound"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by DavidGX on 2006-10-12
I'm truly sorry if this has been solved but I can't find anything. I just bought a Gateway MX6448 notebook and I can't for the life of me get any sound. Not out of the speakers, not out of the headphone jack. It's not a hardware issue because the sound worked fine with windows before I removed it.

I've checked alsamixer and nothing is muted. It seems to be "HDA ATI SB" at least that's what I see when I check sound preferences. Anyone have any clues? I'm desperate here because I really don't want to have to put windows back on the laptop, but I don't see any other choice if I can't get this to work.

Thanks for your help.

Update. Here's my 'lsmod | grep snd'

snd_hda_intel          21088  1
snd_hda_codec         194376  1 snd_hda_intel
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  1 snd
snd_page_alloc         13328  2 snd_hda_intel,snd_pcm


Here's my 'aplay -l'

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by pentarinfosys on 2006-10-12
> **DavidGX said:**
> I'm truly sorry if this has been solved but I can't find anything. I just bought a Gateway MX6448 notebook and I can't for the life of me get any sound. Not out of the speakers, not out of the headphone jack. It's not a hardware issue because the sound worked fine with windows before I removed it.

I'm having similar trouble. The laptop model I'm using is MX6453. It's a 64-bit Turion laptop, which I had originally installed x86_64 on, but went back to the 32-bit install due to the unavailability of certain apps (flashplayer, etc.). SOund didn't work under 64bit install either.

One piece that might be of interest, however, is that the soundchip isn't Intel, according to the docs. It's a SigmaTel 9250. The device manager reports the sound as:

Vendor: ATI Technologies Inc
Device: Unknown (0x437b)

Results of cat /proc/asound/card0/codec#0:
```
Codec: SigmaTel ID 7634
Address: 0
Vendor Id: 0x83847634
Subsystem Id: 0x107b0367
Revision Id: 0x100101
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Power: 0x33
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x33
  Connection: 1
     0x14
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x07
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x1e0, bits 0x0e, types 0x5
Node 0x06 [Audio Selector] wcaps 0x300901: Stereo
  Connection: 3
     0x02* 0x07 0x14
Node 0x07 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN
  Pin Default 0x40c001f0: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x33
Node 0x08 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x404001f0: [N/A] SPDIF Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 2
     0x05* 0x14
Node 0x09 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 1
     0x0f
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP
  Pin Default 0x61813122: [N/A] Line In at Sep Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x02a11121: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x50a70120: [N/A] Mic at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x0e
Node 0x0e [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x19 0x19]
  Connection: 1
     0x06
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Connection: 5
     0x0b* 0x0c 0x0d 0x0a 0x11
Node 0x10 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x0810: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x12
Node 0x11 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x9033012e: [Fixed] CD at Int N/A
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x12 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x06
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Selector] wcaps 0x30090d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x09
```

Note that here, it's a SigmaTel 7634. I've noticed that the alsa version installed on Ubuntu is 1.0.10, while the current stable is 1.0.13. Our sound chip doesn't appear to be supported in either case.

Does anyone have any other suggestions for us?

---

### Post by DavidGX on 2006-10-13
Yes mine seems to be sigmatel as well. When I right-click on the volume icon on the taskbar there are two options.

First one is "HDA ATI SB (Alsa mixer)"

Second one is "SigmaTel ID 7634 (OSS Mixer)"

Neither one seems to work. Any suggestions would be greatly appreciated.

---

### Post by DavidGX on 2006-10-13
Man, it's like I'm so close. Playing an ogg in xmms seems to go swimingly. The file opens and begins to play without error, I can even see the audioscope moving normally. I just... can't hear it ](*,) 

No speakers, no headphones. Nothing works.

---

### Post by DavidGX on 2006-10-14
Still having this problem.

---

### Post by Fred Butyrate on 2006-10-14
I have a Gateway MX7118 and the sound would only work some of the time.

My problem was that the 'External Amplifier' switch was on, so try going into the audio mixer and turning it off.

---

### Post by DavidGX on 2006-10-14
> **Fred Butyrate said:**
> I have a Gateway MX7118 and the sound would only work some of the time.

My problem was that the 'External Amplifier' switch was on, so try going into the audio mixer and turning it off.

I've gone into the "preferences" menu that you get when right-clicking the volume icon, opened a terminal and did "alsamixer" and looked around that and.. nothing. I can't find any "external amplifier" option. Where EXACTLY do you find that?

---

### Post by Fred Butyrate on 2006-10-14
Right Click Volume icon > Open Volume Control > Edit > Preferences

Then check the External Amplifier box

Exit out of the Preferences and go to the switches tab

---

### Post by DavidGX on 2006-10-14
The only two options I get for the first device "HDA ATI SB (Alsa mixer)" are "Master" and "PCM". For the second device "SigmaTel ID 7634 (OSS mixer)" all I get is "Volume". And all are maxed out. I get no other options whatsoever.

Any ideas?

---

### Post by Fzbravozf on 2006-10-16
I just popped in a live cd into my MX6448 and I can't get any sound either.  Sorry don't have any idea how to get it working though.... 

snd_hda_intel          18964  5
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Here's the output I got.

---

### Post by DavidGX on 2006-10-16
> **Fzbravozf said:**
> I just popped in a live cd into my MX6448 and I can't get any sound either.  Sorry don't have any idea how to get it working though.... 

snd_hda_intel          18964  5
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Here's the output I got.

My best guess is that it's just not supported yet in ubuntu/linux. Anyhow, I'm back on windows (uhg) until it is. I really miss linux but.. what can ya do? ](*,)

---

### Post by kuni on 2006-10-18
Hello, I spent 3 days examining the same problem with my intel onboard sound chipset. I tried out some Linux distros, only Debian and Ubuntu refused to work... finally disabling 'External amplifier' worked. Just open KMix -> Switches; and uncheck 'External Amplifier'.. regards, Kuni

---

### Post by DavidGX on 2006-10-20
I never had an option like "External Amplifier" though.

---

### Post by wylie348 on 2006-10-23
> **DavidGX said:**
> The only two options I get for the first device "HDA ATI SB (Alsa mixer)" are "Master" and "PCM". For the second device "SigmaTel ID 7634 (OSS mixer)" all I get is "Volume". And all are maxed out. I get no other options whatsoever.

Any ideas?

You are probably getting sound out of your headphone jacks.  This seems to be a common problem with hda-intel 82801G embedded sound cards on laptops.

Still have not found anyone to solve the problem....any takers?!

---

### Post by spaceghoti on 2006-10-24
I've not had sound since I upgraded to 6.10.  After reading this thread, I opened KMix, went to Settings and Configure KMix.  I discovered that Volume Values were set to None, so I switched them to Absolute.  Suddenly, I have sound again!

---

### Post by sabbathpriest on 2006-11-03
> **spaceghoti said:**
> I've not had sound since I upgraded to 6.10.  After reading this thread, I opened KMix, went to Settings and Configure KMix.  I discovered that Volume Values were set to None, so I switched them to Absolute.  Suddenly, I have sound again!

No luck here with the above.... :-k

---

### Post by wylie348 on 2006-11-03
I also continue to only have sound from my headphone jack and not from the internal speakers.  There are no options to turn on other than two choices in alsamixer.  This under the Intel chipset sound system in my Fujistsu Lifebook T4210.  Apparently this is a problem with the kernel?
Hope this gets fixed soon...!
:confused:

---

### Post by usergentoo on 2007-01-01
Found this bug report [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2146](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2146)
GrueMaster says he has a patch to test. As soon as I get time to switch out this hard drive Im gona test it to see if it works.

---

### Post by Donn on 2007-01-12
I've got a Gateway MX6447 with similar issues with a Sigmatel card.  This is fixed for my hardware in the latest ALSA builds.  This seems to work fine under the standard 2.6.17.10 kernel and under a vanilla 2.6.19.1 kernel for me.  I did try the patch from GrueMaster and it worked swimmingly.  If you want to try compiling with the mercurial repositories, which now includes this patch, you can do the following:  

```
sudo apt-get install mercurial automake1.4 
mkdir alsa
cd alsa
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver
hg clone http://hg-mirror.alsa-project.org/alsa-kernel alsa-kernel
cd alsa-driver
./hgcompile
```

if everything compiles properly, it's probably a good idea to back up your current modules prior to installing.  I think this is a reasonable way to do this.

```
sudo tar zvcf oldsound.tgz /lib/modules/`uname -r`/kernel/sound/* 
```

Now, it should be safe to install the modules you just compiled.
```

make install
```

edit the /etc/modprobe.d/alsa-base file and add the following at the end

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1

```

reboot, or restart alsa

```
sudo /etc/init.d/alsasound restart

```

unmute things with alsamixer and if all is right, you should have sound.  You can check with the speaker-test command if you like.

Hope this helps.

---

### Post by pescarra on 2007-01-12
I own a Gateway MX6931 sounds works fine since the very  first moment.
Here is my  lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

Here is the aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: HDA Generic [HDA Generic]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---

### Post by EkoStorm on 2007-01-14
Many thanks Donn, I have a Gateway mx6453 and your instructions worked like a charm. This was with the SigmaTel STAC9250. The sound is now fully functional.

This is my wife's laptop and neither of us were wanting to use Windows on it.

---

### Post by mekas2024 on 2007-01-14
Hi guys, i have a problem here and i really need to have sound in this lap cuz im adicted to music lol, well. i have a gateway 6453 too, but i try the instructions but i get an error when i do this, this is the error:

mekas@mekas-laptop:~/Desktop/alsa/alsa-driver$ ./hgcompile
gcc utils/mod-deps.c -o utils/mod-deps
utils/mod-deps.c:23:20: error: stdlib.h: No such file or directory
utils/mod-deps.c:24:19: error: stdio.h: No such file or directory
utils/mod-deps.c:25:20: error: unistd.h: No such file or directory
utils/mod-deps.c:26:20: error: string.h: No such file or directory
utils/mod-deps.c:27:19: error: ctype.h: No such file or directory
utils/mod-deps.c:28:19: error: errno.h: No such file or directory
utils/mod-deps.c:93: error: ‘NULL’ undeclared here (not in a function)
utils/mod-deps.c:183: error: initializer element is not constant
utils/mod-deps.c:183: error: (near initialization for ‘no_cards[39]’)
utils/mod-deps.c:191: error: initializer element is not constant
utils/mod-deps.c:191: error: (near initialization for ‘kernel26_opts[5]’)
utils/mod-deps.c: In function ‘nomem’:
utils/mod-deps.c:201: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:201: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:201: error: (Each undeclared identifier is reported only once
utils/mod-deps.c:201: error: for each function it appears in.)
utils/mod-deps.c:202: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:202: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:202: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c: In function ‘read_file’:
utils/mod-deps.c:210: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:210: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:211: warning: incompatible implicit declaration of built-in function ‘sprintf’
utils/mod-deps.c:212: error: ‘R_OK’ undeclared (first use in this function)
utils/mod-deps.c: In function ‘read_file_1’:
utils/mod-deps.c:235: error: ‘FILE’ undeclared (first use in this function)
utils/mod-deps.c:235: error: ‘file’ undeclared (first use in this function)
utils/mod-deps.c:235: error: invalid operands to binary *
utils/mod-deps.c:242: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:242: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:242: error: ‘errno’ undeclared (first use in this function)
utils/mod-deps.c:243: error: ‘ENOENT’ undeclared (first use in this function)
utils/mod-deps.c:243: error: wrong type argument to unary minus
utils/mod-deps.c:243: warning: return makes integer from pointer without a cast
utils/mod-deps.c:247: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:250: error: ‘ENOMEM’ undeclared (first use in this function)
utils/mod-deps.c:250: error: wrong type argument to unary minus
utils/mod-deps.c:250: warning: return makes integer from pointer without a cast
utils/mod-deps.c:256: warning: cast to pointer from integer of different size
utils/mod-deps.c:257: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:258: error: wrong type argument to unary minus
utils/mod-deps.c:258: warning: assignment makes integer from pointer without a cast
utils/mod-deps.c:264: error: ‘EOF’ undeclared (first use in this function)
utils/mod-deps.c:264: warning: comparison between pointer and integer
utils/mod-deps.c:281: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:287: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:288: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:289: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:289: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:289: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:299: warning: incompatible implicit declaration of built-in function ‘strcpy’
utils/mod-deps.c:308: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:309: error: wrong type argument to unary minus
utils/mod-deps.c:309: warning: assignment makes integer from pointer without a cast
utils/mod-deps.c:339: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:340: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:340: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:361: error: ‘stdin’ undeclared (first use in this function)
utils/mod-deps.c: In function ‘include_file’:
utils/mod-deps.c:369: warning: initialization from incompatible pointer type
utils/mod-deps.c:372: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:372: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c: In function ‘create_cond’:
utils/mod-deps.c:387: warning: initialization from incompatible pointer type
utils/mod-deps.c:387: warning: initialization from incompatible pointer type
utils/mod-deps.c:388: warning: initialization from incompatible pointer type
utils/mod-deps.c:391: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:391: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:392: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:395: warning: incompatible implicit declaration of built-in function ‘calloc’
utils/mod-deps.c:396: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:398: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:411: warning: incompatible implicit declaration of built-in function ‘memmove’
utils/mod-deps.c:425: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:425: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:426: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:426: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:426: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:429: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:430: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:445: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:446: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:446: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c: In function ‘alloc_mem_for_dep’:
utils/mod-deps.c:460: warning: incompatible implicit declaration of built-in function ‘calloc’
utils/mod-deps.c:461: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘find_or_create_dep’:
utils/mod-deps.c:474: warning: initialization from incompatible pointer type
utils/mod-deps.c:476: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:476: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:477: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:481: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:484: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:485: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘duplicate_cond’:
utils/mod-deps.c:494: warning: initialization from incompatible pointer type
utils/mod-deps.c:494: warning: initialization from incompatible pointer type
utils/mod-deps.c:497: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:498: warning: return from incompatible pointer type
utils/mod-deps.c:509: warning: incompatible implicit declaration of built-in function ‘calloc’
utils/mod-deps.c:510: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:513: warning: assignment from incompatible pointer type
utils/mod-deps.c:514: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:515: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:517: warning: assignment from incompatible pointer type
utils/mod-deps.c:522: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘join_cond’:
utils/mod-deps.c:539: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:541: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘is_alsa_item’:
utils/mod-deps.c:564: error: initializer element is not constant
utils/mod-deps.c:564: error: (near initialization for ‘known_items[1]’)
utils/mod-deps.c: In function ‘add_select’:
utils/mod-deps.c:578: warning: initialization from incompatible pointer type
utils/mod-deps.c:581: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:581: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:582: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:590: warning: incompatible implicit declaration of built-in function ‘calloc’
utils/mod-deps.c:591: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:593: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:594: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:596: warning: assignment from incompatible pointer type
utils/mod-deps.c:598: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘get_word’:
utils/mod-deps.c:615: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:616: warning: return from incompatible pointer type
utils/mod-deps.c:629: warning: return from incompatible pointer type
utils/mod-deps.c:631: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:632: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:634: warning: incompatible implicit declaration of built-in function ‘strcpy’
utils/mod-deps.c: In function ‘find_dep’:
utils/mod-deps.c:675: warning: return from incompatible pointer type
utils/mod-deps.c:678: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:678: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:679: warning: return from incompatible pointer type
utils/mod-deps.c: In function ‘optimize_dep’:
utils/mod-deps.c:705: warning: assignment from incompatible pointer type
utils/mod-deps.c:726: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:727: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:731: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:732: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:732: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:733: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:733: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:733: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:739: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:740: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:741: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:741: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:748: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:753: warning: assignment from incompatible pointer type
utils/mod-deps.c: In function ‘is_toplevel’:
utils/mod-deps.c:827: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘output_ac_define’:
utils/mod-deps.c:849: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘is_always_true’:
utils/mod-deps.c:876: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c: In function ‘output_card_list’:
utils/mod-deps.c:896: warning: incompatible implicit declaration of built-in function ‘printf’
utils/mod-deps.c:914: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c: In function ‘sel_print_acinclude’:
utils/mod-deps.c:959: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:970: warning: incompatible implicit declaration of built-in function ‘printf’
utils/mod-deps.c: In function ‘output_acinclude’:
utils/mod-deps.c:988: warning: incompatible implicit declaration of built-in function ‘printf’
utils/mod-deps.c:1026: warning: assignment from incompatible pointer type
utils/mod-deps.c:1109: warning: assignment from incompatible pointer type
utils/mod-deps.c: In function ‘output_makeconf’:
utils/mod-deps.c:1193: warning: incompatible implicit declaration of built-in function ‘printf’
utils/mod-deps.c: In function ‘output_include’:
utils/mod-deps.c:1209: warning: incompatible implicit declaration of built-in function ‘printf’
utils/mod-deps.c: In function ‘convert_to_config_uppercase’:
utils/mod-deps.c:1226: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:1226: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:1227: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:1229: warning: incompatible implicit declaration of built-in function ‘strcpy’
utils/mod-deps.c: In function ‘remove_word’:
utils/mod-deps.c:1278: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:1278: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:1279: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:1281: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:1281: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:1282: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:1282: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:1282: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c: In function ‘get_card_name’:
utils/mod-deps.c:1296: warning: incompatible implicit declaration of built-in function ‘malloc’
utils/mod-deps.c:1296: warning: incompatible implicit declaration of built-in function ‘strlen’
utils/mod-deps.c:1299: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:1309: warning: return from incompatible pointer type
utils/mod-deps.c: In function ‘main’:
utils/mod-deps.c:1321: warning: initialization from incompatible pointer type
utils/mod-deps.c:1330: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:1331: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:1337: warning: incompatible implicit declaration of built-in function ‘strdup’
utils/mod-deps.c:1338: warning: comparison of distinct pointer types lacks a cast
utils/mod-deps.c:1363: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:1363: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:1364: error: ‘errno’ undeclared (first use in this function)
utils/mod-deps.c:1365: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:1365: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:1365: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c:1386: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:1394: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:1394: error: ‘EXIT_SUCCESS’ undeclared (first use in this function)
utils/mod-deps.c:1394: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
utils/mod-deps.c: In function ‘usage’:
utils/mod-deps.c:1400: warning: incompatible implicit declaration of built-in function ‘fprintf’
utils/mod-deps.c:1400: error: ‘stderr’ undeclared (first use in this function)
utils/mod-deps.c:1407: warning: incompatible implicit declaration of built-in function ‘exit’
utils/mod-deps.c:1407: error: ‘EXIT_FAILURE’ undeclared (first use in this function)
utils/mod-deps.c:1407: warning: passing argument 1 of ‘exit’ makes integer from pointer without a cast
make: *** [utils/mod-deps] Error 1
./hgcompile: line 42: aclocal: command not found
./hgcompile: line 43: autoconf: command not found
./configure --with-debug=full --with-isapnp=yes --with-sequencer=yes
./hgcompile: line 45: ./configure: No such file or directory

Please Can someone help me :(

I Apreciate!!!

Regards,

MeKaS

---

### Post by mekas2024 on 2007-01-14
OK, i installed the build essential... but i still have error messages :(

Please can some one help me :( 

This are the errores:

mekas@mekas-laptop:~/Desktop/alsa/alsa-driver$ ./hgcompile 
make: Nothing to be done for `all-deps'.
./hgcompile: line 42: aclocal: command not found
./hgcompile: line 43: autoconf: command not found
./configure --with-debug=full --with-isapnp=yes --with-sequencer=yes
./hgcompile: line 45: ./configure: No such file or directory


Thx

MeKaS

---

### Post by Donn on 2007-01-14
EkoStorm  - glad the instructions worked.  I had spent way too much time on this.  Major thanks goes to GrueMaster for creating the patch.

MeKaS - do you have aclocal and automake on your system?  I think a you may need to get the automake package.  The one I have on my system is 1.4.
> 
sudo apt-get install automake1.4

Should do the trick.

---

### Post by oranges2 on 2007-01-15
```
urza@Architect:~/alsa/alsa-driver$ make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/urza/alsa/alsa-driver/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

```
Everything seemed to work after I installed build-essential and automake, until I got to installing. Then this happened =/

Any ideas?

This would be the first thing thats almost gone right since I got Ubuntu (5th clean install =/)

---

### Post by mekas2024 on 2007-01-15
Thank you sooooooo much Donn, i really apreciate this ;) Now i have my sound working fine :D

This is why i like linux... cuz its a really community ! :D

THX


Regards 

MeKaS

---

### Post by EkoStorm on 2007-01-15
> **oranges2 said:**
> ```
urza@Architect:~/alsa/alsa-driver$ make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/urza/alsa/alsa-driver/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

```
Everything seemed to work after I installed build-essential and automake, until I got to installing. Then this happened =/

Any ideas?

This would be the first thing thats almost gone right since I got Ubuntu (5th clean install =/)

Run "make install" as root. 

Eko

---

### Post by oranges2 on 2007-01-15
I have sound

The instructions worked PERFECTLY :D

Gateway MX6446

---

### Post by amphoterous on 2007-01-22
Thanks so much for the instructions Donn! It also worked perfectly on my MX 6453.

Could you perhaps edit your post to include the sudo apt-get install automake1.4 so that people in the future don't run into those errors?

Thanks again!

---

### Post by MasTerYosHi on 2007-01-24
I have a gateway mx 6453 and i followed donn instruction but even after installing automake i get this error:

  CC [M]  /home/heuk21/alsa/alsa-driver/pci/asihpi/asihpi.o
In file included from /home/heuk21/alsa/alsa-driver/pci/asihpi/asihpi.c:50:
/home/heuk21/alsa/alsa-driver/pci/asihpi/hpi.h:2261: error: expected specifier-qualifier-list before ‘HPI_DATA_LEGACY32’
make[4]: *** [/home/heuk21/alsa/alsa-driver/pci/asihpi/asihpi.o] Error 1
make[3]: *** [/home/heuk21/alsa/alsa-driver/pci/asihpi] Error 2
make[2]: *** [/home/heuk21/alsa/alsa-driver/pci] Error 2
make[1]: *** [_module_/home/heuk21/alsa/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [compile] Error 2

did I miss something?

---

### Post by Donn on 2007-01-25
MasTerYosHi, I don't think you missed anything.  This isn't even in the last source tree I built from the Mercurial repository.  If I get a chance, I'll grab the 1.0.14-rc2 sources and try them and write up  some instructions.

Donn

---

### Post by MasTerYosHi on 2007-01-25
Thank You Donn.
I appreciate the help.  I am looking forward to get this working.

---

### Post by Donn on 2007-01-26
MasTerYosHi --

I did a build with Alsa 1.0.14rc2, and it's working for me.  Step by step instructions are as follows:


```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2
tar xvjf alsa-driver-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc2
./configure
make
sudo make install
```

I rebooted after, and things are working just fine.  You'll probably need to add these lines to the /etc/modprobe.d/alsa-base file.

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

---

### Post by MasTerYosHi on 2007-01-27
Thank you so much Donn, I got sound now just after doing your instruction on alsa and adding those two lines to the alsa-base file.  I haven't finish doing the instructions on page 2. 
Should I go back and do those or just leave it like it is?

Again :D  and :KS

---

### Post by Donn on 2007-01-27
Nope, I'd say if you've got sound, you're all set.  :)  Unmuting with alsamixer would be the only other thing I forgot to mention.  Congrats!

---

### Post by fooman on 2007-01-27
for three months i have not heard a peep out of this thing (gateway mx6453).

...not anymore!!!  :D 

thank you Donn,  thank you very much.

---

### Post by euthypro on 2007-02-08
I didn't have to ask. I came across this thread. Now I have sound. Just wanted to say, thanks!:)

---

### Post by iamtherealwoody on 2007-02-11
Hi,
I have a Gateway M675 with SigmaTel and Intel ac97 ICH5
and I cant get my sound to work either.  I have followed the Comprehensive sound problem guide and compiled the ALSA driver and alsamixer is all unmuted, 
Im very new to linux, finally got the wireless working on my broadcom 4306.
Should I try those commands DON that worked for the others?
I am willing to learn, help me please.

> lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer


> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


What am I doing wrong?

---

### Post by Donn on 2007-02-11
You could try the 1.0.14-rc2 from Alsa as a start.  I'd try that first.  It's likely you don't need to make the changes to alsa-base, listed above.  Without having that specific notebook, it's hard for me to tell.

One of the other issues you may run up against is PCI express support.  I was looking on Gateway's site to see if that notebook used PCIe, and it doesn't explicitly say it.  If your notebook needs PCIe support, you may need a new kernel version.  I've recently upgraded to 2.6.20, and things seem to be working well.

---

### Post by iamtherealwoody on 2007-02-12
Donn, Im very new to linux, Ive been using Windows for years and OSX for about one year.  Im  getting used to the terminal prompt but dont know much of anything about linux.  I went to ALSA website, I downloaded the alsa-driver-1.0.14rc2.  It was downloaded to the desktop, and I tried to extract it using sudo apt-get install alsa-driver-1.0.14rc2.  I also tried this ./configure --with-cards=intel8x0 --with-debug=full from this thread [http://www.ubuntuforums.org/showthread.php?t=353950](http://www.ubuntuforums.org/showthread.php?t=353950).
I tried to read everything I could find on it last night and was unable to do it.  If you or someone could talk me through it or point me in the right direction I would be very grateful.  I do not mind reading and researching for my self.
Thanks for all your help.
matt

---

### Post by Donn on 2007-02-12
Matt --

If you open up a terminal window, then paste these in, you should be good to go with a 1.0.14rc2 build from Alsa.


```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2
tar xvjf alsa-driver-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc2
./configure
make
sudo make install

```

- The wget command will download 1.0.14rc2 from ALSA.
- The tar xvjf will unzip the archive file - the 'x' is to extract, the 'v' is verbose, the 'j' will take care of the bz2 decompression, and the 'f' is to specify what file.
- The cd command changes directory (of course!)
- ./configure sets options correctly for compilation
- make builds the alsa drivers
- sudo make install installs the newly built ALSA code.

If you want to use ./configure --with-cards=intel8x0 --with-debug=full that will likely be fine as well.

Best of luck!

Donn

---

### Post by iamtherealwoody on 2007-02-12
Thanks for the relpy Donn,
I was trying to install the alsa-driver-1.0.14.rc2 package since you posted last night.  Its really easy when you tell me what to do.  After the install, i opended alsamixer and unmuted all channels, still no sound.  Restarted, no sound, checked alsamixer, no sound.  It sucks because I really dont want to go back to Windows, EVER.  If you can think of anything else, let me know.

Thanks,
Matt

---

### Post by Donn on 2007-02-13
Matt --

You may want to go with a new kernel.  Perhaps some bug was fixed for your laptop between 2.6.17 and 2.6.20.  Here are some steps.

```
# only need to do this once...
sudo apt-get update
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

cd /usr/src

# change version numbers to get current kernel version
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2

sudo tar xjf linux-2.6.20.tar.bz2
# may need to remove 'linux' symbolic link first?
sudo ln -s linux-2.6.20 linux

cd /usr/src/linux
sudo cp /boot/config-`uname -r` ./.config

sudo make menuconfig
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

cd /usr/src
ls -l *.deb
sudo dpkg -i linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb

```

---

### Post by iamtherealwoody on 2007-02-13
Donn,
Every time I get to the 
tar xjf linux-2.6.20.tar.bz2 
Step, its gives me a whole bunch of errors, cannot mkdir, permission dinied, no such file or directory.
I have no idea.  Everything else goes fine, no errors what so ever.
Matt

---

### Post by Donn on 2007-02-14
Matt --

Sorry about that - left of a bunch of sudos.  I edited the post.  Can you try it again?

Thanks,

Donn

---

### Post by Ricky Yong on 2007-02-14
Try this

Typed in "man alsamixer" at your terminal screen.

This is the manual....read it...if you do not understand then email me...at [email]cwyong1@streamyx.com[/email]

Chao

---

### Post by iamtherealwoody on 2007-02-14
Donn,
Everything was fine until this,

> matt@matt-laptop:/usr/src$ sudo dpkg -i linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb
dpkg: error processing linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb
matt@matt-laptop:/usr/src$ sudo dpkg -i linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb
dpkg: error processing linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_i386.deb


Thanks for editing that stuff.  Ill try this stuff again in a few hours, now i have to take an exam.

Ricky--
Ill check that out also in a few hours

Thanks guys for all your help,
Matt

---

### Post by Donn on 2007-02-14
Matt --

I must have the filename wrong.  If you:

```
  cd /usr/src
  ls *.deb

```
you should see 2 files.  On my machine it looks like this:
```
  linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_amd64.deb
  linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_amd64.deb

```
use dpkg -i on whatever filenames that is.  On my machine, I did:

```
sudo dpkg -i linux-image-2.6.20-custom_2.6.20-custom-10.00.Custom_amd64.deb
sudo dpkg -i linux-headers-2.6.20-custom_2.6.20-custom-10.00.Custom_amd64.deb

```
Good luck, and good luck on your exam.

Donn

---

### Post by iamtherealwoody on 2007-02-15
Donn--
I upgraded the Kernal, thanks for the help, but the sound still isnt working. Im gonna go back and check everything to make sure that I havent missed anything small that is causing the problem.  Also, when I installed the new kernel, I lost support for my Broadcom 4306 wireless.  I believe this is a common problem so Im going to switch back.  Seems like Im going to have to keep windows around for a little bit, at least until I buy a new computer, gonna get a macbook pro for school and stuff.

Ricky--
Read the manual, Ive checked the mixer a few times, dont think Ive missed anything.  I must be though since Im probably the only one with this computer that doesnt have sound.  Ill keep reading and trying to find out what the problem is though.

Thanks guys,

Matt
Oh I also lost the boot up screen with the new kernel, after the grub menu, it was black until the splash screen

---

### Post by Donn on 2007-02-15
Matt -- I hate messing with the wireless also.  About the sound, do you have any error messages in dmesg?  If you look at more /proc/asound/cards, what's there?

---

### Post by iamtherealwoody on 2007-02-15
Here's the dmesg 
(> )
[17179574.436000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.436000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.436000] TCP: Hash tables configured (established 32768 bind 32768)
[17179574.436000] TCP reno registered
[17179574.436000] TCP bic registered
[17179574.436000] NET: Registered protocol family 1
[17179574.436000] NET: Registered protocol family 8
[17179574.436000] NET: Registered protocol family 20
[17179574.436000] Using IPI Shortcut mode
[17179574.436000] ACPI wakeup devices:
[17179574.436000] ICSA MDM0 ILAN USB1 USB2 USB3 USB4 USB7  LID
[17179574.436000] ACPI: (supports S0 S3 S4 S5)
[17179574.436000] Freeing unused kernel memory: 288k freed
[17179574.472000] vga16fb: initializing
[17179574.472000] vga16fb: mapped to 0xc00a0000
[17179574.580000] Console: switching to colour frame buffer device 80x25
[17179574.580000] fb0: VGA16 VGA frame buffer device
[17179575.696000] Capability LSM initialized
[17179575.724000] ACPI: Fan [FAN0] (off)
[17179575.728000] ACPI: Thermal Zone [THRM] (38 C)
[17179576.204000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179576.204000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.204000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[17179576.204000] ICH5: chipset revision 2
[17179576.204000] ICH5: not 100% native mode: will probe irqs later
[17179576.204000]     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:pio, hdb:pio
[17179576.204000]     ide1: BM-DMA at 0x1888-0x188f, BIOS settings: hdc:pio, hdd:pio
[17179576.204000] Probing IDE interface ide0...
[17179576.496000] hda: HTS548080M9AT00, ATA DISK drive
[17179577.168000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.184000] Probing IDE interface ide1...
[17179577.920000] hdc: HL-DT-ST DVD-RW GWA-4040N, ATAPI CD/DVD-ROM drive
[17179578.256000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.260000] hda: max request size: 1024KiB
[17179578.268000] hda: 156301488 sectors (80026 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.268000] hda: cache flushes supported
[17179578.268000]  hda: hda1 hda2 hda3 hda4
[17179578.324000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.324000] Uniform CD-ROM driver Revision: 3.20
[17179578.744000] usbcore: registered new driver usbfs
[17179578.744000] usbcore: registered new driver hub
[17179578.748000] USB Universal Host Controller Interface driver v2.3
[17179578.748000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179578.748000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.748000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.748000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.748000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x00001800
[17179578.748000] hub 1-0:1.0: USB hub found
[17179578.748000] hub 1-0:1.0: 2 ports detected
[17179578.816000] ieee1394: Initialized config rom entry `ip1394'
[17179578.852000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179578.852000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.852000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.852000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.852000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x00001820
[17179578.852000] hub 2-0:1.0: USB hub found
[17179578.852000] hub 2-0:1.0: 2 ports detected
[17179578.956000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179578.956000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.956000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.956000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.956000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001840
[17179578.956000] hub 3-0:1.0: USB hub found
[17179578.956000] hub 3-0:1.0: 2 ports detected
[17179579.060000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 193
[17179579.060000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179579.060000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179579.060000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179579.060000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x00001860
[17179579.060000] hub 4-0:1.0: USB hub found
[17179579.060000] hub 4-0:1.0: 2 ports detected
[17179579.164000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 209
[17179579.164000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.164000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.164000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.164000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.164000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179579.164000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xe0000000
[17179579.168000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.168000] hub 5-0:1.0: USB hub found
[17179579.168000] hub 5-0:1.0: 8 ports detected
[17179579.272000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179579.272000] ACPI: PCI Interrupt 0000:03:01.1[A] -> GSI 17 (level, low) -> IRQ 177
[17179579.320000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[e0306000-e03067ff]  Max Packet=[2048]
[17179579.528000] Attempting manual resume
[17179579.556000] usb 5-5: new high speed USB device using ehci_hcd and address 2
[17179579.568000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.584000] kjournald starting.  Commit interval 5 seconds
[17179580.592000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b8060100d053]
[17179589.028000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.052000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.352000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.352000] agpgart: Detected an Intel 865 Chipset.
[17179589.356000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179589.408000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17179589.408000] Copyright (c) 1999-2005 Intel Corporation.
[17179589.408000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179589.408000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[17179589.432000] Real Time Clock Driver v1.12
[17179589.432000] input: PC Speaker as /class/input/input1
[17179589.456000] hw_random: cannot enable RNG, aborting
[17179589.808000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:e0:b8:5c:c5:d6
[17179589.968000] SCSI subsystem initialized
[17179589.984000] parport: PnPBIOS parport detected.
[17179589.984000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.032000] Initializing USB Mass Storage driver...
[17179590.032000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179590.032000] usb-storage: device found at 2
[17179590.032000] usb-storage: waiting for device to settle before scanning
[17179590.032000] usbcore: registered new driver usb-storage
[17179590.032000] USB Mass Storage support registered.
[17179590.052000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection[17179590.052000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179590.052000] Yenta: CardBus bridge found at 0000:03:01.0 [107b:0603]
[17179590.052000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179590.052000] Yenta: Routing CardBus interrupts to PCI
[17179590.052000] Yenta TI: socket 0000:03:01.0, mfunc 0x011c1112, devctl 0x64
[17179590.092000] Floppy drive(s): fd0 is 1.44M
[17179590.108000] FDC 0 is a National Semiconductor PC87306
[17179590.132000] ieee80211_crypt: registered algorithm 'NULL'
[17179590.144000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179590.144000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179590.168000] bcm43xx driver
[17179590.284000] Yenta: ISA IRQ mask 0x0c38, PCI irq 177
[17179590.284000] Socket status: 30000086
[17179590.284000] Yenta: Raising subordinate bus# of parent bus (#03) from #03 to #07
[17179590.284000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[17179590.284000] cs: IO port probe 0x5000-0x5fff: clean.
[17179590.284000] pcmcia: parent PCI bridge Memory window: 0xe0300000 - 0xe03fffff
[17179590.284000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179590.288000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179590.524000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb3, caps: 0xa44713/0xc0000
[17179590.556000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179590.716000] ts: Compaq touchscreen protocol output
[17179590.808000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 177
[17179590.808000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179590.984000] cs: IO port probe 0x100-0x3af: clean.
[17179590.988000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179590.988000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.988000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.988000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.632000] intel8x0_measure_ac97_clock: measured 55449 usecs
[17179591.632000] intel8x0: clocking to 48000
[17179592.524000] lp0: using parport0 (interrupt-driven).
[17179592.556000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179592.556000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.556000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.604000] Adding 819304k swap on /dev/hda3.  Priority:-1 extents:1 across:819304k
[17179592.752000] EXT3 FS on hda2, internal journal
[17179592.880000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.880000] md: bitmap version 4.39
[17179593.436000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179594.056000] cdrom: open failed.
[17179594.420000] kjournald starting.  Commit interval 5 seconds
[17179594.420000] EXT3 FS on hda4, internal journal
[17179594.420000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.032000]   Vendor: USB2.0    Model: CardReader CF RW  Rev: 0.0>
[17179595.032000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.036000]   Vendor: USB2.0    Model: CardReader Combo  Rev: 0.0>
[17179595.036000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179595.036000] usb-storage: device scan complete
[17179595.096000] Driver 'sd' needs updating - please use bus_type methods
[17179595.100000] sd 0:0:0:0: Attached scsi removable disk sda
[17179595.112000] sd 0:0:0:1: Attached scsi removable disk sdb
[17179595.124000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179595.124000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[17179596.124000] NET: Registered protocol family 17
[17179599.164000] ACPI: AC Adapter [ACAD] (off-line)
[17179599.236000] ACPI: Battery Slot [BAT1] (battery present)
[17179599.304000] ACPI: Power Button (FF) [PWRF]
[17179599.304000] ACPI: Lid Switch [LID]
[17179599.304000] ACPI: Sleep Button (CM) [SLPB]
[17179599.440000] ibm_acpi: ec object not found
[17179599.472000] pcc_acpi: loading...
[17179599.552000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179604.992000] SoftMAC: Authentication response received from 00:16:cb:bb:93:05 but no queue item exists.
[17179604.996000] ieee80211: eth1: IEEE80211_ASSOC_REQ received
[17179607.936000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179607.936000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179607.936000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179608.096000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179609.584000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179609.588000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179609.588000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[17179609.588000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179609.588000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179609.588000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179609.588000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179609.592000] [fglrx] total      GART = 134217728
[17179609.596000] [fglrx] free       GART = 118222848
[17179609.596000] [fglrx] max single GART = 118222848
[17179609.596000] [fglrx] total      LFB  = 59682816
[17179609.596000] [fglrx] free       LFB  = 48893952
[17179609.596000] [fglrx] max single LFB  = 48893952
[17179609.596000] [fglrx] total      Inv  = 0
[17179609.596000] [fglrx] free       Inv  = 0
[17179609.596000] [fglrx] max single Inv  = 0
[17179609.596000] [fglrx] total      TIM  = 0
[17179610.088000] ppdev: user-space parallel port driver
[17179610.564000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179610.564000] apm: overridden by ACPI.
[17179610.808000] Bluetooth: Core ver 2.8
[17179610.808000] NET: Registered protocol family 31
[17179610.808000] Bluetooth: HCI device and connection manager initialized
[17179610.808000] Bluetooth: HCI socket layer initialized
[17179610.840000] Bluetooth: L2CAP ver 2.8
[17179610.840000] Bluetooth: L2CAP socket layer initialized
[17179610.844000] Bluetooth: RFCOMM socket layer initialized
[17179610.844000] Bluetooth: RFCOMM TTY layer initialized
[17179610.844000] Bluetooth: RFCOMM ver 1.7
[17179616.108000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357420)
[17179616.108000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.108000] Backtrace:
[17179616.108000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.108000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.108000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.108000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.108000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.108000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.108000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.108000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.108000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.108000] Trying to fix it up, but a reboot is needed
[17179616.108000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357440)
[17179616.108000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.108000] Backtrace:
[17179616.108000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.108000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.108000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.108000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.108000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.108000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.108000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.108000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.108000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.108000] Trying to fix it up, but a reboot is needed
[17179616.108000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357460)
[17179616.108000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.108000] Backtrace:
[17179616.108000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.108000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.108000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.108000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.108000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.108000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.108000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.108000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.108000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.108000] Trying to fix it up, but a reboot is needed
[17179616.108000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357480)
[17179616.108000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.108000] Backtrace:
[17179616.108000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.108000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.108000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.108000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.108000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.108000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.108000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13574a0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13574c0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13574e0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357500)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357520)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357540)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357560)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c1357580)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13575a0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13575c0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179616.112000] Bad page state at free_hot_cold_page (in process 'aplay', page c13575e0)
[17179616.112000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17179616.112000] Backtrace:
[17179616.112000]  [<c0143a5d>] bad_page+0x5d/0xb0
[17179616.112000]  [<c01443a8>] free_hot_cold_page+0x38/0x120
[17179616.112000]  [<c014ee90>] zap_pte_range+0x120/0x2a0
[17179616.112000]  [<c014f0f2>] unmap_page_range+0xe2/0x130
[17179616.112000]  [<c014f1fe>] unmap_vmas+0xbe/0x210
[17179616.112000]  [<c0153650>] unmap_region+0x80/0x120
[17179616.112000]  [<c015391f>] do_munmap+0xaf/0xf0
[17179616.112000]  [<c015399a>] sys_munmap+0x3a/0x60
[17179616.112000]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[17179616.112000] Trying to fix it up, but a reboot is needed
[17179659.204000] NET: Registered protocol family 10
[17179659.204000] lo: Disabled Privacy Extensions
[17179659.204000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179659.204000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179659.204000] IPv6 over IPv4 tunneling driver
[17179695.792000] SoftMAC: Open Authentication completed with 00:12:0e:53:4d:ee
[17179695.804000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179697.652000] ieee80211_crypt: registered algorithm 'WEP'
[17179698.036000] SoftMAC: Open Authentication completed with 00:12:0e:0e:ee:3a
[17179704.260000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[17179704.392000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179704.392000] usb-storage: device found at 3
[17179704.392000] usb-storage: waiting for device to settle before scanning
[17179706.544000] eth1: no IPv6 routers present
[17179709.392000]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[17179709.392000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179709.392000] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[17179709.396000] sdc: Write Protect is off
[17179709.396000] sdc: Mode Sense: 43 00 00 00
[17179709.396000] sdc: assuming drive cache: write through
[17179709.396000] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[17179709.396000] sdc: Write Protect is off
[17179709.396000] sdc: Mode Sense: 43 00 00 00
[17179709.396000] sdc: assuming drive cache: write through
[17179709.396000]  sdc: sdc1
[17179709.440000] sd 1:0:0:0: Attached scsi removable disk sdc
[17179709.440000] sd 1:0:0:0: Attached scsi generic sg2 type 0
[17179709.440000] usb-storage: device scan complete
[17179709.792000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179757.404000] SoftMAC: Open Authentication completed with 00:12:0e:0e:ee:3a
[17179773.356000] eth1: no IPv6 routers present


In /proc/asound I dont have a file called cards.  
I have 
card0, Ich5, oss, seq     folders.

I have a cards gedit file that is empty.
This is probably something thats wrong huh?  Told you I really dont know what Im doing.
Im booting with the old kernel and Im using the fwcutter, so my wireless is done pretty easy.  Dont want to mess with ndiswrapper yet.

Thanks Donn
Matt

---

### Post by iamtherealwoody on 2007-03-07
Fixed the sound, well I wouldnt say I fixed anything, but I found out why I wasnt making any sound.  There is a switch in the volume applet that i didnt find in alsamixer, Center/LFE output, the second I changed it to mixer output. BAM, had sound.  Feel kinda dumb, 2 weeks to figure that out.  Hey Im a noob, what can I say. But now I can FINALLY DELETE MY WINDOWS PARTITION, too bad I dont physical remove it... Id burn it.

Thanks 
Matt

---

### Post by bdogg64 on 2007-03-09
Awesome post Donn... got my sound working on a Gateway MT6451

---

### Post by yosselw on 2007-03-10
Gateway 6441 works out of the box. 

I feel lucky.:KS

---

### Post by yomba1 on 2007-03-26
GATEWAY MT6451 LAPTOP, No Sound & other Gateway related problems:

I have a Gateway MT6451 laptop and a IBM Think-pad laptop, both running Feisty. Both are dual-boot with Windows.

The IBM Think-pad has absolutely no problems with any of the issues cited herein. The Gateway has a number of issues.

The Gateway MT6451 had No Sound. I used the suggested fix by Donn for the No Sound problem. After some time spent, this worked, but not altogether!

I now have Sound Playback but no Sound Capture. This is a heck of a lot better than no sound at all, but I don't understand why still no Sound Capture?. 

The SigmaTel Stac9250 (OSS Mixer) has now been replaced with the HDA ATI SB (Alsa Mixer)

In System Preferences Sound (Sound Preferences):

All Sound Playback tests work with ALSA - Advanced Linux Sound Architecture enabled. 
Music CD's play perfectly. No complaints here. 

However, the Sound Capture Test invariably fails and returns the following message:

Failed to construct test pipelin for gconfaudiosrc!
audioconvert | audioresample | gconfigaudiosink profile = chat'

Anyone have any ideas on how to deal with this one remaining sound issue?

Other problems with the Gateway MT6451 that I do NOT have with my IBM Think-pad when running the same Feisty setup include:

1)  HP Model: PSC-1310 Print-Scan-Copy (All in one printer,scanner, copier)

Printer Recognized but Xsane Image Scanner cannot find the scanner. (Both Printer and Scanner are recognized with this same setup in Feisty on IBM Thinkpad)

2)  On Booting Ubuntu there is a "bug found" notice that runs by so quickly that I cannot read the entire one line notice. 

The only problem I've seen that may be related to this is that only the USB mouse works after booting into Ubuntu and attempting to login. 

If any other USB connections are present at boot up, it is impossible to log in and start Ubuntu. Once logged in, any after the fact USB connections are allowed and function correctly.

The point of all of the above is that the Gateway MT6451 laptop seems to be the source of the problems since none of these problems exist using the same Feisty setup on my IBM Thinkpad.

The Gateway MT6451 did also have the Synaptic Touch Pad problem that required forum research and xorg file editing to fix. This is the sort of problem that needs to have a simpler cure if Ubuntu wants to get the masses on its desktop.

I'm a non-programming noob to Linux but really like Ubuntu as opposed to Big Brother MS. I sincerely hope the improvements to ease of installation continue, but these Gateway MT6451 problems are quite off-putting. 

I realize Feisty is pre-release, but it does work without any problems at all on my IBM Thinkpad. The Gateway MT6451 is another can of worms.

Thanks in advance for any assistance rendered.

---

### Post by treesurf on 2007-03-26
I have the same Sigmatel Stac9250 in a Gateway NX570X and while playback worked for me out of the box I have never been able to get capture to work.  I get the same error with the Sound Capture Test.  I have spent hours on this already doing everything related that I could find on the forums.   If you ever figure it out, please let me know, and I will do the same for you.  It is very frustrating.

---

### Post by moxiot on 2007-04-17
sorry if to late. just for future reference, i got the advice given in page 4 to work under a gateway mx-6447. 

thank you so much.

---

### Post by delgotit99 on 2007-04-19
WOO HOO you guys rock.  All I had to do was:

right click volume icon
open volume control
click switches tab
uncheck External Amplifier

Thanks again guys this has been bugging me for months.

---

### Post by iamtherealwoody on 2007-04-23
Ya that took me too long to figure out, about 2 weeks! But I definitely can understand your joy.

matt

---

### Post by AJYablo on 2007-05-05
So I set up my gateway laptop (MX3422) with Feisty and do all the updating and such.
I finally get around to checking to see if I have sound (there wasnt any on boot up, so I figured I should check) and behold. Nada.

I tried getting the alsa drivers, but I ended up with this:


/alsa-driver-1.0.14rc2$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Does anyone need to see the log?new alsa


If anyone has any suggestions, I'd love them.

Ive tried the whole alsa properties and trying to find the external amplifier check box.

---

### Post by g00ngh0st on 2007-08-15
I followed all of DON's steps and I still have NO sound at ALL! I'm on a gateway Mt3708...  with a sigmatel 9200 card builtin.. Any help would be GREATLY aprreciated

---

### Post by netron on 2007-08-22
> **delgotit99 said:**
> WOO HOO you guys rock.  All I had to do was:

right click volume icon
open volume control
click switches tab
uncheck External Amplifier

Thanks again guys this has been bugging me for months.

i dont have an "external amplifier" option.

however in sound preferences i see two options for "default mixer tracks":

HDA NVidia (Alsa mixer)
Sigmatel STAC9200 (OSS Mixer)


followed Don's advice (compiling alsa) and still no sound after reboot.

there is nothing muted in alsamixer.


(fresh feisty install , new gateway laptop)

---

### Post by byronknoll on 2007-08-25
> **AJYablo said:**
> So I set up my gateway laptop (MX3422) with Feisty and do all the updating and such.
I finally get around to checking to see if I have sound (there wasnt any on boot up, so I figured I should check) and behold. Nada.

I tried getting the alsa drivers, but I ended up with this:


/alsa-driver-1.0.14rc2$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


Does anyone need to see the log?new alsa


If anyone has any suggestions, I'd love them.

Ive tried the whole alsa properties and trying to find the external amplifier check box.

Try installing g++

---

### Post by themadhatter on 2007-08-26
Hooo boy. I've tried everything mentioned on this page, and no luck. Details are:

Gateway MX6446
Ubuntu 7.04

It says it has a Sigmatel sound card.

I used the Wget routine, edited the alsa file, and no luck. The latest is that the sound control icon has a little red marker on it, and when I click on it the message is "No volume Control GStreamer Plugins and/or Devices Found".

Now this is new - only started happening.  I'm going to edit out the Intel lines in alsa-base and see if the icon at least comes back, should have done that before posting this but I just thought of it, so give me a minute and I'll be back.

---

### Post by themadhatter on 2007-08-26
OK, I took out the Intel lines and the sound icon is normal again, but still no sound. Think I will sleep on it for now - any suggestions would be appreciated, my wife wants to do some recording, and I'd rather use my laptop instead of her Acer.
:guitar:

---

### Post by themadhatter on 2007-08-26
Hah - now this is interesting - read another post which said if you typed:

alsamixer 

in a terminal window it would pop up a graphic equalizer. What I got was:

alsamixer: function snd_mixer_load failed: Invalid arguement

---

### Post by donkihote on 2007-08-26
> **themadhatter said:**
> Hah - now this is interesting - read another post which said if you typed:

alsamixer 

in a terminal window it would pop up a graphic equalizer. What I got was:

alsamixer: function snd_mixer_load failed: Invalid arguement

me too!???

---

### Post by themadhatter on 2007-08-26
Glad to know I'm not the only one - I suspect we'll get an answer Monday.

:guitar:

Wayne

---

### Post by iamcanadian4 on 2007-08-29
You are a freakin Genious!

Or whoever figured this out.

Thanks!

> **delgotit99 said:**
> WOO HOO you guys rock.  All I had to do was:

right click volume icon
open volume control
click switches tab
uncheck External Amplifier

Thanks again guys this has been bugging me for months.

---

### Post by ngeddes on 2007-08-30
I have a Gateway MX 3701 which also behaves as you have written.  On board sound card is ATI SB 540.  Works fine in Xp using Sigmatel Driver.

There must be a solution somewhere.

Neil

---

### Post by opacha on 2007-09-09
I've done everything. It doesn't work with a gateway ml3706 either(sigmatel 9200). I have the most up to date ubuntu Gutsy and updated every day hoping.

---

### Post by ngeddes on 2007-09-10
I purchased and installed  Turtle Beach USB Audio Advantage Micro.  I first tested it with Xp using drivers that came with unit.  Very slick sound but it doesn't use the laptop's speakers. You can plug in a headset or powered speakers.

Well. I rebooted into UBUNTU with USB plugged in.  Ubuntu detected unit and installed drivers.  I now have three options when I open vol control.  This time I seleted the USB one and then in Admin/----/Sound selected USB device.  

SHE WORKS LIKE A CHARM.

I am almost sure this is a driver issue with Alsamixer and Gateway's on board sound card.  Perhaps the new version .....14  which is available but not as a packet will solve our problem.

---

### Post by Corvair on 2007-09-11
I also have the same problem with a Gateway MX6453, ATI IXP SB400 : no sound.

I did the following as quoted by Don  



Code:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2)
tar xvjf alsa-driver-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc2
./configure
make
sudo make install

the sound is off by default and I don't know where to go to activate it.

If I go to volume control I have SigmaTel STAC9250 ()SS Mixer)  and volume is up but I get no sound.

I also just got a Logitec headset, usb 350 and I get no sound either.
I have the latest kernel. On the previous kernel the sound is OK but the headset will not work.

I am lost and green on this stuff as you can see.

Can anyone help?

---

### Post by ngeddes on 2007-09-11
Open Terminal and type alsamixer.

Please report what version of alsa mixer is running?

I was really hoping that if I could get my driver uopdated from 13 to 14 that it might work.  Being a newbe I wasn't sure how to install the latest driver as it is not yet packaged for snaypatic manager.

Looks like if you suceeded, it isn't the answer/  I havbe seen plenty of posts with Gateway Laptops, looks like a common problem.

Neil

---

### Post by Corvair on 2007-09-11
I forgot to mention that I have Ubuntu 7.04 for 64 bit
I have sound when I run Kernel 2.6.20.15 but I have no sound when I run version 2.6.20.16
either way my Logitech does not give out any sound.

When I open Volume Control the only mixer I have listed is SigmaTel STAC9250 (OSS Mixer)


When I do [COLOR="Red"]sudo apt-get update [COLOR="Red"][COLOR="Red"][COLOR="Black"]I get this[/COLOR][/COLOR][/COLOR][/COLOR]


Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg                            
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10), connection timed out
99% [Connecting to ca.archive.ubuntu.com (206.167.141.10)]

---

### Post by opacha on 2007-09-13
I too tried to upgrade to alsa-driver-1.0.15rc2, but when I try to compile I get some error, and I just gave up. Really I think the fix is going to come through the ALSA people not the ubuntu people. I'm hoping that this new version of alsa will be full released soon. This problem is taking FOREVER.

---

### Post by ngeddes on 2007-09-13
Hear Hear

I agree with you, this is a driver issue with some PC's.  I have read a lot of Gateway owners are disappointed.

---

### Post by mperedithe on 2007-09-16
> **Donn said:**
> MasTerYosHi --

I did a build with Alsa 1.0.14rc2, and it's working for me.  Step by step instructions are as follows:


```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2
tar xvjf alsa-driver-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc2
./configure
make
sudo make install
```

I rebooted after, and things are working just fine.  You'll probably need to add these lines to the /etc/modprobe.d/alsa-base file.

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```


when I tried this everything worked great up til the ./configure command and at that point I received the following message.

"configure: error: no acceptable C compiler found in $PATH
See 'config.log' for more details"

I don't know how to check the config.log.

---

### Post by opacha on 2007-10-01
Ok, I went up to Gutsy Beta. What a disaster! Firstly it wont start in the regular mode it will boot with a black screen and do nothing. Probably a videocard problem(changing the resolution to 640x480 16 didnt help.). In safe graphics mode after several restarts I was able to get past some segmentation fault errors and see the desktop. I had to attempt to install 5 or 6 times before it actually completed without error(except for the error about mounting at 88% that has been described elsewhere on the forums). After installation I cannot actually boot to the desktop as I get errors repeatedly about my upgraded(not the one that came in this laptop) wireless card. I don't see how all this is going to be resolved in 1 month. Ubuntu....what happened to you? You were so promising...:confused:

---

### Post by bricar2 on 2007-10-07
So I have the same Gateway MT3708 laptop as some of the other people on this forum. Everything works except for the sound. I've spent the last couple weeks trying to get it working. I've tried everything on this forum and still nothing. I have no external amplifier to unmute when I check out alsamixer in the console. 

If anyone has any suggestions they are greatly appreciated. This sound issue is the only thing wrong. 

Feisty 7.04

So here's some basic info:
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
__________________________________________________________________________________
lsmod | grep snd

snd_hda_intel          22296  1
snd_hda_codec         200320  1 snd_hda_intel
snd_pcm_oss            44672  0
snd_mixer_oss          17792 1 snd_pcm_oss
snd_pcm                80900  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            35200  0
snd_seq_midi            9728  0
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  13 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
___________________________________________________________________________________________________________
cat /proc/asound/card0/codec#0

Codec: SigmaTel STAC9200
Address: 0
Vendor Id: 0x83847690
Subsystem Id: 0x107b0318
Revision Id: 0x102201
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Power: 0x0
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x0a
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x08
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM:
    rates [0x1e0]: 44100 48000 88200 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
Node 0x06 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x07 [Audio Selector] wcaps 0x300901: Stereo
  Connection: 3
     0x02* 0x08 0x0a
Node 0x08 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  Pin Default 0x40c500f0: [N/A] SPDIF In at Ext N/A
    Conn = Optical, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x0
Node 0x09 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x404500f9: [N/A] SPDIF Out at Ext N/A
    Conn = Optical, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 2
     0x05* 0x0a
Node 0x0a [Audio Selector] wcaps 0x30090d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 1
     0x0c
Node 0x0b [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 1
     0x07
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Connection: 5
     0x10* 0x0f 0x0e 0x0d 0x12
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP Detect
  Pin Default 0x400000f1: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x0b
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP Detect
  Pin Default 0xd2114110: [Both] Speaker at Int Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0b
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect
  Pin Default 0x400700f5: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0b
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x02a19020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 1
     0x0b
Node 0x11 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x0810: OUT
  Pin Default 0x400000f3: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x13
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x503300f7: [N/A] CD at Int N/A
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x13 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
_________________________________________________________________________________
 lspci -v

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: b0000000-b1ffffff
        Prefetchable memory behind bridge: 00000000b2000000-00000000b3ffffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0507000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8225
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at b000 [size=256]
        Memory at d0200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

So there's some basic info. If anyone out there needs more output of some command let me know.

Thanks  in advance for any help. It feels like I'm so close to getting this figured out. Like I said before, I have tried everything on this particular thread and still no luck. I've tried the latest alsa build and still nothing. Maybe I'm missing something. I am fairly new to linux so if anyone out there can point me in the right direction I'd greatly appreciate it.

---

### Post by ngeddes on 2007-10-07
It seems to related to the gateway hardware.  I have the MX 3701 and those specs you posted are very similiar to mine.  I got some sound by using a plug in USB sound card.  But this is a pain and it doesn't work for everything.

Neil

---

### Post by bricar2 on 2007-10-07
Unfortunately Gateway laptops seem to be hard to configure as evidenced by all the people with them. If I had known before I bought this laptop I probably would have gone with something else. But I really like this laptop and it will be so nice once I get the sound working. 

I have a USB Soundblaster SB0270 soundcard and I don't get any sound with it either. Same for the headphones. Some people have reported they got sound only through the headphone jack. Anyway, who wants to tote around an external soundcard and speakers with a laptop?

---

### Post by bricar2 on 2007-10-08
Don't know if this matters, but I'm running 6.10 through VirtualBox on my HP desktop. Sounds works fine there. When I go to System>Administration>Sound and test the various sound units (for lack of a better word), I get movement of the bar when the box "Testing Pipeline" pops up. On my laptop there is no movement.

---

### Post by ngeddes on 2007-10-10
With the Gateway laptop, when I test the pipeline connection nothing happens.  But when I test it with the USB soundcard installed and configured, nothing happens but it makes a sound.

On my Tobisha Laptop where everything works fine, the pipeline shows activity.

Neil

---

### Post by rkrisher on 2007-10-16
I think you all have the same motherboard as my MT3705.  Try the detailed steps I posted to get mine working.  I list all the compilers you need for the alsa 15rc1 compile plus a change you need to do in the script to get it to compile correct.

[http://ubuntuforums.org/showthread.php?p=3524207](http://ubuntuforums.org/showthread.php?p=3524207)

---

### Post by bg1256 on 2007-10-16
> **Donn said:**
> MasTerYosHi --

I did a build with Alsa 1.0.14rc2, and it's working for me.  Step by step instructions are as follows:


```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2
tar xvjf alsa-driver-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc2
./configure
make
sudo make install
```

I rebooted after, and things are working just fine.  You'll probably need to add these lines to the /etc/modprobe.d/alsa-base file.

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

New Gateway for me today.

Running alsamixer lets me know I was running v1.0.13 so I installed .14 per the instructions quoted above.
I have a SigmaTel STAC9200 card.

I followed the instructions, but it didn't seem to make a difference.

If anyone knows how to get this working, I would really appreciate it!

If I can't figure some of my problems out soon, I'm taking this back to the store and exchanging it for something else, because this is ridiculous.

---

### Post by opacha on 2007-10-18
Ubuntu 7.10 RC1-- Stil no sound. Worked nicely otherwise until I updated the first set of updates-- now it won't boot. Argh!

---

### Post by ngeddes on 2007-10-18
Same result here no sound.  I ran it off the live CD, didn't install.  I don't expect much more from the release version.

Neil

---

### Post by PreviousN on 2007-10-21
Hmm.. I didn't read the 9 pages here...but I've got a Gateway Mt3707. 

I've got the sound to work following instructions here:
[https://bugtrack.alsa-project.org/alsa-bug/login_page.php?return=%2Falsa-bug%2Fview.php%3Fid%3D3036](https://bugtrack.alsa-project.org/alsa-bug/login_page.php?return=%2Falsa-bug%2Fview.php%3Fid%3D3036)

I had to compile alsa from source and apply a patch. Its really not that bad. Do it once and sound works for a long time. I even made a script (with wget and everything!. just run, it downloads source, and configures, applys patch, magics stuff, and i have sound).

---

### Post by jcrow on 2007-10-22
I have the same laptop MX6448 and I had the same issue with sound with the fiesty kernel upgrade, but it worked OK with the original fiesty kernel. I am now on Gusty and the .14 kernel works.

---

### Post by ngeddes on 2007-10-22
I will try Gutsy and report

---

### Post by PreviousN on 2007-10-23
I've made a kinda guide for sound and/or wifi. Here's a link to the post. It's on page 6.
[http://ubuntuforums.org/showthread.php?t=352553&page=6&highlight=gateway+3705](http://ubuntuforums.org/showthread.php?t=352553&page=6&highlight=gateway+3705)

---

### Post by mekas2024 on 2007-10-24
Hi everyone!

I hope someone could help me!! :(

i have an error when i try to do the ./hgcompile... everything seems to be ok but at the end i get this error messages...

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/hwdep.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/memory_wrapper.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/memalloc.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/sgbuf.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_native.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_lib.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_timer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_misc.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/pcm_memory.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/rawmidi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/rtctimer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/timer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/wrappers.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/misc_driver.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/memory_debug.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/sound.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/init.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/memory.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/info.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/control.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/misc.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/device.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/isadma.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/sound_oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/info_oss.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-hwdep.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-timer.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-rtctimer.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-pcm.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-page-alloc.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/snd-rawmidi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/mixer_oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/pcm_oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/pcm_plugin.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/io.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/copy.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/linear.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/mulaw.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/route.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/rate.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/snd-mixer-oss.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/oss/snd-pcm-oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_device.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_dummy.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_instr.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi_emul.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi_event.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_midi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_virmidi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_lock.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_clientmgr.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_memory.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_queue.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_fifo.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_prioq.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_timer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_system.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_ports.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/seq_info.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-device.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi-event.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-dummy.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-virmidi.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-midi-emul.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/snd-seq-instr.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_fm.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_gf1.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_iw.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/ainstr_simple.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-fm.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-gf1.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-simple.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/instr/snd-ainstr-iw.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_init.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_timer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_ioctl.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_event.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_rw.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_synth.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_midi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_readq.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/seq_oss_writeq.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/acore/seq/oss/snd-seq-oss.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/aloop.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/dummy.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mtpav.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mts64.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/portman2x4.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/serial-u16550.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/virmidi.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-aloop.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-dummy.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-virmidi.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-serial-u16550.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-mtpav.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-mts64.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/snd-portman2x4.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/mpu401_uart.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/mpu401.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/snd-mpu401-uart.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/mpu401/snd-mpu401.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_lib.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_synth.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_seq.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_midi.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_drums.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/opl3_oss.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/snd-opl3-lib.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl3/snd-opl3-synth.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_lib.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_mixer.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_proc.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_seq.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/opl4_synth.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/yrw801.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/snd-opl4-lib.o
LD [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/opl4/snd-opl4-synth.o
CC [M] /home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.o
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c: In function ‘snd_pcsp_create’:
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: ‘PIT_TICK_RATE’ undeclared (first use in this function)
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: (Each undeclared identifier is reported only once
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: for each function it appears in.)
make[4]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers] Error 2
make[1]: *** [_module_/home/mekas/Desktop/alsa/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
mekas@mekas-laptop:~/Desktop/alsa/alsa-driver$

I think it something of the headers, but i dont know what to do.. Did somebody  have an idea what could be? Im sorry but im kind of newbi here lol

THX

---

### Post by mperedithe on 2007-10-24
Mekas,
Try the long drawn out line of code in the terminal from this post:
[http://ubuntuforums.org/showthread.php?t=586058](http://ubuntuforums.org/showthread.php?t=586058)

I had similar problems with mine and entering that code prior to ./hgcompile corrected the problem.

---

### Post by mekas2024 on 2007-10-24
Ho Thanks mperedithe , 

I already have sound with these steps:

1) sudo aptitude install build-essential
2) mkdir alsa
3) cd alsa
4) sudo wget [ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)
5) tar xvjf alsa-driver-1.0.15.tar.bz2
6) cd alsa-driver-1.0.15
7) sudo ./configure
8)sudo make
9) sudo make install
10) sudo reboot now
11) unmute all channels in mixer and sound work

But the sound its too low, so its not even half of loud it should be, 

I will try whit the method u say, i hope that makes my sound really sound!

THANKS a lot!

Regards 

Mekas

---

### Post by cmbryan on 2007-10-24
> **mekas2024 said:**
> 

/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c: In function ‘snd_pcsp_create’:
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: ‘PIT_TICK_RATE’ undeclared (first use in this function)
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: (Each undeclared identifier is reported only once
/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.c:48: error: for each function it appears in.)
make[4]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers/pcsp] Error 2
make[2]: *** [/home/mekas/Desktop/alsa/alsa-driver/drivers] Error 2
make[1]: *** [_module_/home/mekas/Desktop/alsa/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
mekas@mekas-laptop:~/Desktop/alsa/alsa-driver$

I think it something of the headers, but i dont know what to do.. Did somebody  have an idea what could be? Im sorry but im kind of newbi here lol

THX



I'm also having this error.  Is it because of the tickless kernel??  This is only a problem in the daily snapshots, not the 1.0.15 release.  I found what seemed to be a patch here:  [http://www.geocities.com/stssppnn/pcsp.html](http://www.geocities.com/stssppnn/pcsp.html)  but still no luck...

I need the bleeding edge alsa to get my audio interface working, so any help is very appreciated!

-Chris

---

### Post by mekas2024 on 2007-10-25
> **cmbryan said:**
> I'm also having this error.  Is it because of the tickless kernel??  This is only a problem in the daily snapshots, not the 1.0.15 release.  I found what seemed to be a patch here:  [http://www.geocities.com/stssppnn/pcsp.html](http://www.geocities.com/stssppnn/pcsp.html)  but still no luck...

I need the bleeding edge alsa to get my audio interface working, so any help is very appreciated!

-Chris


Hey Chris, that problem its because of the headers, something that its entering to a wrong directory or something, its because its not linked well... at least thats what i read in google. Anyway, y can use the solution that i post above ur comment, its almost the same but in a diferent way, that thing install alsa, and everything works ok , i just have the problem that the sound doesnt sound too loud, but i have sound, i will keep trying to get a louder sound...

Good Luck

---

### Post by cmbryan on 2007-10-25
SOLVED:  by specifying the desired card during configure, thus avoiding pcsp altogether!



> **mekas2024 said:**
> Hey Chris, that problem its because of the headers, something that its entering to a wrong directory or something, its because its not linked well... at least thats what i read in google. Anyway, y can use the solution that i post above ur comment, its almost the same but in a diferent way, that thing install alsa, and everything works ok , i just have the problem that the sound doesnt sound too loud, but i have sound, i will keep trying to get a louder sound...

Good Luck

---

### Post by mekas2024 on 2007-10-25
Hey cris, u solve it whit the method i post or with the method in this thread, because if u did it like this method:

sudo apt-get install mercurial automake1.4 
mkdir alsa
cd alsa
hg clone [http://hg-mirror.alsa-project.org/alsa-driver](http://hg-mirror.alsa-project.org/alsa-driver) alsa-driver
hg clone [http://hg-mirror.alsa-project.org/alsa-kernel](http://hg-mirror.alsa-project.org/alsa-kernel) alsa-kernel
cd alsa-driver
./hgcompile

I would like to know how you did it, because as i told i have sound by the method i found in other thread but it sound not too loud... 

Well.. let me know how u did it please :P

Have a good day:P

Regards, 

Mekas

---

### Post by cmbryan on 2007-10-25
I have good volume here.  Dumb question, but have you set the levels in alsamixer?

I'm only listening through headphones, so I can't double-check the line out level.

Chris

---

### Post by mekas2024 on 2007-10-25
Yes i did, i have 100% volume, but it sound like half of what it should sound... 

How u set up the driver... via the solution of this thread or the solution i posted above?

Regards!

Mekas

---

### Post by mekas2024 on 2007-10-26
> **cmbryan said:**
> SOLVED:  by specifying the desired card during configure, thus avoiding pcsp altogether!


Hey, Cris, how u solve it? how u did that ?

Please tell me cuz i need my sound loud :(

THX

---

### Post by cmbryan on 2007-10-26
> **mekas2024 said:**
> Hey, Cris, how u solve it? how u did that ?

Please tell me cuz i need my sound loud :(

THX



I just did:

./hgcompile --with-cards=emu10k1
sudo make install

with the generic gutsy kernel and alsa snapshot 20071024.

Don't know what else to say....

Chris

---

### Post by teledyn on 2007-11-03
the ALSA snapshots place the kernel modules in a different location than the ubunto kernel packages, so be aware that you will end up with two, or three copies of everything!!

$ find /lib/modules/2.6.22-14-generic -name snd-hda-int\* -exec ls -l {} \;
total 340
-rw-r--r-- 1 root root 343328 2007-10-13 01:43 snd-hda-intel.ko
-rw-r--r-- 1 root root 343328 2007-10-13 01:43 /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
-rw-r--r-- 1 root root 2015696 2007-11-03 21:42 /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

---

### Post by mekas2024 on 2007-11-20
> **mekas2024 said:**
> Yes i did, i have 100% volume, but it sound like half of what it should sound... 

How u set up the driver... via the solution of this thread or the solution i posted above?

Regards!

Mekas

Hey i found a solution for the not too loud sound!

I did this:

# echo options snd-hda-intel model=3stack > /etc/modprobe.d/sound

# aptitude install alsa-source alsa-tools alsa-tools-gui alsamixergui alsa-oss

# m-a a-i alsa

And nos i have sound loudly!!

I found the solution here: [http://www.esdebian.org/forum/viewtopic.php?forum=38&showtopic=108918](http://www.esdebian.org/forum/viewtopic.php?forum=38&showtopic=108918)

I hope this helps someppl with the same problem :P

Have a nicee day everyone :P

Regards, 

Mekas

---

### Post by themadhatter on 2007-11-21
Note that this issue no longer exists as of 7.10 on my Gateway MX6446. I'm sure what changes were made but sound now works fine.
:KS

---

