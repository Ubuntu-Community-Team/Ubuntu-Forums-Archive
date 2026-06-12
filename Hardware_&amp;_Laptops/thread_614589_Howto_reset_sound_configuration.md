---
title: "Howto reset sound configuration"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by AlexE on 2007-11-16
I don't know how and when, but my 7.04 sound configuration  is corrupted. The sound (ex. ubuntu welcome sound) is played distorted.

When I insert the 7.10 CD the sound is ok. After system update to 7.10 the sound is still distorted.

So I guess the sound configuration is broken. How can I delete the current sound configuration and init a new sound installation?

Thanks a lot 
Alexander

---

### Post by fiprojects on 2008-01-28
Did you get an update on this?

I have 7.10 and my sound was working yesterday but not today.  The only thing I can think of is that I installed various software since yesterday for a curiosity thing (web design packages like Amaya and Bluefish) plus audio/video related software (sound converter and others though they've not appeared on my Applications menu so I can't recall).

I did read a post elsewhere about someone who said they unplugged their USB mouse and that somehow buggered their sound.

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

Restricted devices is enabled for Nvidia...

Anyone direct me forward?

Cheers!

---

### Post by kesman on 2008-02-02
[B]Nevermind, I solved the problem by going to alsamixer in terminal. My PCM was muted for some reason. It displays MM in the bottom of the bar if the channel is muted. Then press M to unmute it. There are several channels so browse trough all of them. Then press ESC to exit, and then type 
```
sudo alsact storel
```
to save the settings permanently. Worked for me.[/B]


I also lost my sound when doing a dist-upgrade with apt. No error messages, just no sound. I've checked all levels in alsamixer, and no problem there.
```

$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: IXP SB400 AC'97 Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.5
       bus info: pci@0000:00:14.5
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp


```
I think I could re-enable the snd_atiixp module, but modprobe -r complains that it is in use. How do I first disable it?

---

