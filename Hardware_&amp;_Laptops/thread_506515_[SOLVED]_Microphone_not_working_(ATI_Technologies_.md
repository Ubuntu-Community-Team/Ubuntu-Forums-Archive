---
title: "[SOLVED] Microphone not working (ATI Technologies Inc SB450 HDA Audio (rev 01)"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by ugm6hr on 2007-07-21
I am trying to get Ekiga to work on my laptop (Acer Aspire 5051AWXMi - 5050 derivative) with sipgate.co.uk

I installed Ekiga, and set up Ekiga to register with sipgate.  It accepts incoming calls - sort of.  When dialling, the line goes dead after ringing a few times.  Then, about 20 seconds later, Ekiga notifies about an incoming call, but returns a "Remote user has stopped calling" error if I accept incoming call.

I think this probably reflects an issue with either sipgate or my firewall, which I will investigate later.

My main problem is that my microphone doesn't work.  I have an external headset that plugs into the microphone and headphone socket.  Unfortunately, I can't get it to work.

I have adjusted all the various settings in alsamixer.  There are 2 mics listed - "front mic" and "mic", and unmuting both, turning up the relevant "mic boost" doesn't help.  I have heard that it is necessary to "capture" the microphone to make it work - but there is no such option in my alsamixer.  I have set the 2 input sources to *mic* and *front mic*, which has made no difference.

I have tried Audacity too, with every input listed - none of them are my microphone.

Any ideas?

lspci:
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
```

lshw:
```
        *-multimedia
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: iomemory:d0000000-d0003fff irq:19

```

---

### Post by ugm6hr on 2007-07-22
Some progress - wanted to document it before I forgot how to do it!

Had to sort this from Terminal manually:
```
amixer
``` lists all inputs/outputs and controls:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [off]
  Front Right: Capture 0 [0%] [-12.00dB] [off]

```

```
amixer sset Capture 31
``` maximises Capture volume
```
amixer sset Capture cap
``` unmutes Capture

So now it looks like:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [on]
  Front Right: Capture 31 [100%] [34.50dB] [on]

```

Then in *alsamixer*:
Mute everything except Front and Front Mic (headset volume and mic volume), and PCM (obviously).
Leave Mic Boost OFF.
Ensure Input Source lists Front Mic

Then the mic test works on Ekiga - very clearly.  And Skype works flawlessly.  So must be an Ekiga / sipgate issue for me to resolve now.

Can't sort it out - so asked for more help:
[http://ubuntuforums.org/showthread.php?t=506760](http://ubuntuforums.org/showthread.php?t=506760)

---

### Post by YannickDefais on 2007-08-03
Hi,

I hope my documentation will help you: 
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

My advice, first upgrade to Ekiga 2.0.9, your version is more than 1 year old (2.0.3). There has been 6 releases of only bug fix in the meantime.

Feel free to ask more if you need.

Regards,
Yannick

---

### Post by maclenin on 2007-08-19
**ugm6hr:**

Worked like a charm with Skype 1.4.0.99 (Intel 82801H HDAudio Controller/HP 6910p)! Thank you.

---

### Post by ugm6hr on 2007-08-20
> **maclenin said:**
> **ugm6hr:**

Worked like a charm with Skype 1.4.0.99 (Intel 82801H HDAudio Controller/HP 6910p)! Thank you.

Glad it helped someone else :)

---

### Post by badmadrabbit on 2007-09-02
Wow, you're a genious!!! I tried every now and then to solve my recording problem for months now! Your solution worked flawlessly!! Thanks!

---

### Post by pwolanin on 2007-09-02
This put me on the right path for Ubuntu 7.04 on a Dell Inspiron 2400 (after much pulling of hair before).

Capture was on for me already, but not Mic, and Capture only has a rangoe of 0-15  so I ran:

```
$ amixer sset Mic cap

$ amixer sset Mic 31

$ amixer sset Capture 15

```

And now skype and teamspeak work with a headset with a boom mic using the rear (pink) mic input on the Dell.

---

### Post by rkoblick on 2007-09-06
:)
Tried almixer sset Mic cap
and got:
amixer: Unable to find simple control 'Mic',0
Where to go from hear?

---

### Post by xarroyo on 2007-09-08
Hey.. i was reading from other post like this one:
[http://ubuntuforums.org/showthread.php?t=314383&highlight=HDA+Intel+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=314383&highlight=HDA+Intel+SigmaTel+STAC9200)

I added the line into the ```
/etc/modprobe.d/alsa-base
``` the following line at the end ```
options snd-hda-intel model=ref
``` since according to the mentioned post i have a inspiron DELL laptop... the fact is that my computer still has disable the mic.

if i go to the terminal and do amixer i have the following information 

```
xavi@dellota:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [-42.00dB] [on]
  Front Right: Playback 3 [10%] [-42.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
xavi@dellota:~$ 
```

i've tried to do the following according to your post but this message i got ```
xavi@dellota:~$ amixer sset Capture 31
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
xavi@dellota:~$ amixer sset Capture cap
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
xavi@dellota:~$ 
```

I don't know what i have to do to make my mic work! Please, somebody help me!

I will add here a picture of the alsamixer

---

### Post by Pavel Mendl on 2007-09-18
[:KS SOLVED for me NOW] 

but I have several experiences to share, hope they could help:

My configuration:
Kubuntu 7.04 Feisty Fawn
Aspire 3104NWLMi laptop
ATI Technologies Inc SB450 HDA Audio (rev 01) [as after LSPCI]

Installing microphone for Skype, I encountered two major troubles:

1) (K)ubuntu kernel 2.6.20-16-generic is buggy (I am just about to post bug report, as I am pretty sure now).

Consequence: after 2.6.20-15 -> 2.6.20-16 upgrade (in my case as result of Full upgrade in Adept Manager) the KMix mixer goes completely wrong (displaying wrong card ID and even lacking any input/mic control panel).

Workaround: simple reboot to old kernel (e.g. via Grub menu) is enough. Seems no other configuration files are messed, thanks God.

Remark: ... but still to localize it took me three from-the-scratch instalations of Kubuntu (as I hesitated to suspect kernel itself for such behaviour).

2) The above Howto seemingly did not work for me, as I was no way able to get sound back from test call loop, even though amixer showed completly correct values, consistent with what alsamixer showed and I could hear mic if I set playback from microfone locally.

On very last attempt I just made to confirm before leaving Skype alone I got a signal. You can imagine I did not let it pass. So trying to find when I hear it and when not I found the following dependencies (which might be - and probably are - still horribly incomplete):

a) If you are using external headset, you will probably need to use MIC (and not Front Mic described in Howto, which seems to be designated for built in microphones -even though on my laptop I did not succeed to get any sound from built in mic, maybe even no one is below that hole ;) ).

b) IF USING KDE (as all Kubuntu users do) you MUST set CAPTURE slider(s) in KMix Input panel (at least one, but I did not test which one, simply set both) to 100%. This is tricky to find, as they DO NOTHING with value shown in amixer (neither increasing it nor limiting or caping it), but obviously they DO LIMIT input microphone settings in real world.

c) To be even worse, seems that MIC position in Output panel is linked with MIC position in Input panel, So decreasing mic loopback to ears in Output panel hiddenly decreases the mic input (capture) level. The other limit is, that setting 100% MIC and MIC BOOST in Output panel is dangerous for your ears (beware). I finally ended with 100% MIC (both Input and Output), 0% Output Mic Boost and 100% Input Mic Boost, what works for me fine even with Skype,

So my last "word of wisdom" is: do not resign on testing, as there are many combinations to check and there is REAL chance that some of them will finally work.

---

