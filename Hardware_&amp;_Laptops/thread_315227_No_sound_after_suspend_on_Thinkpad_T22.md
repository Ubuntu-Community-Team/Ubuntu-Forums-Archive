---
title: "No sound after suspend on Thinkpad T22"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by xemvip on 2006-12-08
I hope I am not re-asking an old question... I used the search feature already, and found similar questions, but no answers.:???: 

My system:
[B]Edgy Eft, kernel 2.6.17-10-386
IBM Thinkpad T22, 900MHz w/ 256M RAM
Cirrus Logic CS 4614/22/24 audio[/B]

Everything works fine when booting up from a power-off state.  Putting the laptop into suspend/sleep mode works great with the exception that I have no sound on resume.  :( 

Running /etc/init.d/alsa-utils restart does not help.  Alsa seems to think the sound card is OK.  I can even open the volume control applet, or run alsamixer.

When I try to play an mp3 in XMMS it opens, but does not play.  There is no error message.  The time counter does not move.  It acts like I never hit the play button.

Trying to play an mp3 in mplayer shows:

[FONT="Courier New"][B]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
================================================== ========================
alsa-init: using device default
alsa: 22050 Hz/2 channels/4 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 0.0 (00.0) of 272.0 (04:32.0) ??,?%[/B][/FONT]

Then mplayer just hangs... nothing happens ever.  I can quit mplayer with CTRL-C.

In /etc/default/acpi-support I changed one line:

[FONT="Courier New"][B]
ACPI_SLEEP_MODE=standby[/B][/FONT]

...but this did not make any difference.

There are no acpi or apmd flags in my grub boot config.

All help or suggestions are greatly appreciated.  :KS
[B][I]
*** UPDATE ***[/I][/B]

I discovered that if I do: modprobe -r snd-cs46xx followed by modprobe snd-cs46xx that my sound system recovers!!

Umm...I'm wondering how to use this information to fix my problem permanently.  I think this is the part where I beg for more help! :)

*** UPDATE #2 - FIXED!! ***

I discovered after much searching and poking around regarding the modprobe results from earlier, and found that changing the /etc/default/acpi-support file to force the snd_cs46xx module to unload before suspend, and reload after...

See this part of /etc/default/acpi-support:

[FONT="Courier New"][B]# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_cs46xx"[/B][/FONT]

Maybe my search skills still need work, but man what a bummer that it was so hard to figure this out.  ](*,) 

I hope this info is useful to someone else out there.  Long live Ubuntu!!!  :-D

---

### Post by mdshann on 2007-03-08
Thank you for the information, it worked perfectly!

---

### Post by mengfei on 2007-03-12
Hi there, can you tell me exactly what you did?

I followed the steps you outlined and my sound still doesn't work.

There is also a guide at thinkwiki.org which has the same steps you have, except a lil more.

Perhaps that may be of some interest to you?

---

### Post by PhilipGanchev on 2007-03-20
I have an a21m thinkpad, which loses sound after resuming from sleep, as you described.  But "modprobe -r snd-cs46xx" gives an error, "FATAL: Module snd_cs46xx is in use.", and the problem persists if I after "modprobe snd-cs46xx".

"lspci" shows that the module is used by 16 other modules:

snd_cs46xx             87400  16
gameport               15368  2 snd_cs46xx
snd_rawmidi            25600  1 snd_cs46xx
snd_ac97_codec         96672  1 snd_cs46xx
snd_pcm                80520  19 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd                    55428  24 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10504  2 snd_cs46xx,snd_pcm

I appreciate any hints.

mengfei, where is the discussion on thinkwiki.org? I could not find it anywhere.

Thanks in advance!

---

### Post by rahov on 2008-01-20
I'm using kubuntu and I've also got
   ERROR: Module snd_cs46xx is in use
Then I stopped skype, kmix ... and all the 'sound' programs. This fixed the problem.

---

### Post by miiko on 2008-03-18
Like others on this list I am unable to unload the module. The acpi.conf trick doesn't work either. I'm running Gutsy on a T22. Any pointers would be gratefully accepted.

Thanks.

---

