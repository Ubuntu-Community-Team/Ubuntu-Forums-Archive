---
title: "Sounds stops working after ~day with 8.10"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by davidhoenig on 2008-12-22
I've tried searching for this problem, but have not found anything, especially with all the other sound problems people have.

I was running 8.04 successfully all summer -- all my hardware worked fine. After upgrading to 8.10, my sound now stops working after 12-24 hours. I cannot figure out what triggers it, and it almost always happens overnight while the machine is idle. I know my way around a linux box a bit and have checked logs, audio settings, daemons, and processes, but cannot find any indication of what the error is.

50% of the time I just need to restart X, and then sound works again. The other 50% of the time I need to reboot and sounds works again. This tells me there is some sound-related process that is getting wedged and needs to be restarted, but I do not know how to find out what that is.

When sound works, I see there is a "pulseaudio" processes running, but when it does not work, I do not see the process. If I try to start it manually by hand I get:

$ pulseaudio 
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

and sound still does not work. Could it be that there is some rogue process that is causing the sound hardware to appear busy?

My hardware is an ASUS P5k motherboard with the built in Intel HDA sound chip:

lsmod | grep intel | grep snd
snd_hda_intel         381488  7 
snd_pcm                83204  5 snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd                    63268  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

If I try reinstalling the module I get another "in use" error:

$ sudo modprobe -r snd
FATAL: Module snd is in use.
_intel,snd_pcm

Any help will be greatly appreciated.

---

### Post by kostkon on 2008-12-22
> **davidhoenig said:**
> I've tried searching for this problem, but have not found anything, especially with all the other sound problems people have.

I was running 8.04 successfully all summer -- all my hardware worked fine. After upgrading to 8.10, my sound now stops working after 12-24 hours. I cannot figure out what triggers it, and it almost always happens overnight while the machine is idle. I know my way around a linux box a bit and have checked logs, audio settings, daemons, and processes, but cannot find any indication of what the error is.

50% of the time I just need to restart X, and then sound works again. The other 50% of the time I need to reboot and sounds works again. This tells me there is some sound-related process that is getting wedged and needs to be restarted, but I do not know how to find out what that is.
Sound in recent versions of Ubuntu (actually >= 8.04) is controlled by *PulseAudio*.
> **davidhoenig said:**
> When sound works, I see there is a "pulseaudio" processes running, but when it does not work, I do not see the process. If I try to start it manually by hand I get:
Hmm, it seems then that *PulseAudio* is crashing after some time. It is a user level process thus it loads when your sessions starts (i.e. when you login). So, in most cases, when it crashes it's just a matter of logging out and in again to make it work again.
> **davidhoenig said:**
> $ pulseaudio 
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

and sound still does not work. Could it be that there is some rogue process that is causing the sound hardware to appear busy?

My hardware is an ASUS P5k motherboard with the built in Intel HDA sound chip:

lsmod | grep intel | grep snd
snd_hda_intel         381488  7 
snd_pcm                83204  5 snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd                    63268  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

If I try reinstalling the module I get another "in use" error:

$ sudo modprobe -r snd
FATAL: Module snd is in use.
_intel,snd_pcm

Any help will be greatly appreciated.
The correct way to start PulseAudio from the cmd is
```
pulseaudio -D
```
(in order to start as a daemon)
Try restarting it using the above command to see if it makes any difference. If not, maybe some application tries to use the sound card exclusively and it does not allow *PulseAudio* to restart (*PulseAudio* also needs to have the exclusive use of the sound card to work) or maybe is even causing it to crash afterall.

But, I don't really know what it may cause it to crash. But I have seen some other cases like yours here in the forums.

It is a fact that some applications have buggy ALSA plugin or only use OSS to produce sound, so you may indeed use some application that tries to get an exclusive use of the sound card and thus blocking *PulseAudio* (and the problems that this may cause).

I recommend you to try [this very good how-to]("http://ubuntuforums.org/showthread.php?t=789578") to better setup your *PulseAudio* because there is a possibility that it will fix your problem.

---

### Post by davidhoenig on 2008-12-22
Thanks for the info. I began going through the PulseAudio configuration instructions in the link you sent, but when I got to this step:

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system.

I have a problem: Under the "Output devices" tab, no devices are shown and it says in grey "No output devices avaiable". But this cannot be right -- I am listening to music (in Flash-based last.fm) as I type this so there is obviously some sound device.

I tried restarting the pulseaudio user process and got:

$ pulseaudio -k
W: ltdl-bind-now.c: Failed to find original dlopen loader.
$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
$ ps aux | grep pulse
dhoenig   2346  0.0  0.1  29800  4044 ?        Ssl  20:21   0:00 pulseaudio -D
dhoenig   2350  0.0  0.0   7528  2512 ?        S    20:21   0:00 /usr/lib/pulseaudio/pulse/gconf-helper

So it appears to be running, but there was a warning.

Does this give anyone any more information as to what the problem is? So right now I have:

1) Audio stops working after the machine has been on for a few hours
2) Restarting X (or probably logging out then back in) usually restores sound
3) PulseAudio control does not list any output devices, but I do have sound support (at least in Flash apps)

Looking further in the instructions I see:

*The application does plays audio and does not list an entry in the Playback tab;
- the application is either accessing your sound card directly or playing sound via ALSA's dmix device. This will prevent PulseAudio from working correctly & cause audio mixing errors.

So maybe ALSA is getting in the way -- is there a way to completely remove ALSA? I do not have or need any special audio applications so as long as the base Ubuntu stuff is supported in PulseAudio I should be good.

---

### Post by davidhoenig on 2008-12-23
A bit more information gathered this morning: when I woke up, sound did not work (like every morning). The pulse process was running:

$ ps aux | grep pulse
dhoenig  21023  0.4  0.1  29800  4024 ?        Ssl  10:09   0:00 pulseaudio -D

I tried playing an mp3 in Rhythmbox and there was no sound, and the slider did not move (indicating it was "stuck" at the start of the song). In a terminal, I killed and restarted pulseaudio (with -k and -D). As soon as I did so Rythmbox started playing the mp3 just fine.

But, sound in Flash applications in Firefox (e.g. youtube) still did not work. I restarted X (via ctrl-alt-backspace), logged back in, and now sound works in everything again.

---

### Post by davidhoenig on 2008-12-31
This sound problem was so annoying (I have to log out/log in everyday to get sound to work again) that I reverted to a fresh install of 8.04. To my dismay, the problem remained (even though I had no problems with my previous install of 8.04)!

After reading a lot of sound problem threads relating to PulseAudio I have concluded that PulseAudio and Flash player in FF3 are the culprits. The one other friend I have who uses Ubuntu (on a modern Lenovo Thinkpad) also loses sound whenever he suspends, and also has to log in/out to restore it. I still do not have a resolution, and am very disappointed with Ubuntu right now.

Could anyone point me to a forum thread or Wiki page that is the best source of information for problems with PulseAudio and Flash? I have just installed libflashsupport to see if that helps because some people have reported it does, but others report it does not, or that removing it eliminates their sound problems.

My wife continues to make fun of me (jokingly) and reminds me of how easy/well her Macbook always "just works". I'd like to show her that the FOSS model can work just as well :)

---

