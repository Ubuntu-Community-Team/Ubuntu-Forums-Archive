---
title: "No sound, suddenly!:("
date: 2010-06-01
forum: Hardware
---

### Post by sandokanw73 on 2010-06-01
Hi, I'm new with Ubuntu, 10.04 worked just fine until yesterday... suddenly the audio went away... I tried everything... searched for a solution but nothing...

It looks like it doesn't recognize my sound card (Acer Aspire 6920G)... 

Please, help me... I love Ubuntu, but this problem is frustrating me... a lot!!! I'm beginning to think that is an hardware problem...

---

### Post by dino99 on 2010-06-01
maybe you need to unmute it

install with synaptic: paprefs and gnome-alsamixer (set your prefs into "apps sound gnome-alsamixer")

---

### Post by sandokanw73 on 2010-06-01
> install with synaptic: paprefs and gnome-alsamixer (set your prefs into "apps sound gnome-alsamixer")

Tried it... didn't work :(

I just don't get it. It worked just fine for months, 9.10... then I upgraded it to 10.04, and it worked SUPER! Till yesterday, and apparently with no reason, the sound went away... :confused:

---

### Post by dino99 on 2010-06-01
check: system pref sound to know if the hardware is well recognized

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by sandokanw73 on 2010-06-01
Well, I did it already... 

The system does NOT recognize my sound card with command: 
sudo aplay -l (aplay: device_list:221: no soundcard found...)

Then...

The sound card physically installed and recognized by your hardware... YES Here it is: 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

Is my SoundCard supported?
 Well, I guess because it worked just fine till yesterday.

So, what do I do now... go on with asla correct mode? Sorry if I seem a bit insecure, it's just that I'm not really an expert and I already tried different things... Lost many hours... I appreciate a lot you help, Thank's!! :)

---

### Post by sandokanw73 on 2010-06-02
I reinstalled ubuntu 10.04... lost one day... had to save everything on an external Hd... now it works... but I almost gave up and went back to windows... 

Well, I'm happy now it works... but for how long...:(

---

