---
title: "sound is gone, when i tried fix one error"
date: 2015-10-20
forum: Hardware
---

### Post by righN on 2015-10-20
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]        i used this [tutorial]("http://thehumble.ninja/2014/02/06/fixing-alsa-lib-pcmc7843snd_pcm_recover-underrun-occurred-while-keeping-pulseaudio-in-your-system/") to fix my problem with this error in wine ALSA lib pcm.c:7843:(snd_pcm_recover) underrun occurred but now when i restart computer sound gone..
  I tried to delete pulse folder in .config folder but that doesn't help.
  i tried run pulseaudio in terminal and i got this
W: [pulseaudio] sink.c: Default and alternate sample rates are the same.
E: [pulseaudio] module.c: Failed to load module "module-alsa-sink" (argument: "device_id=1 "): initialization failed
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.[/TD]
[/TR]
[/TABLE]

---

### Post by Yellow Pasque on 2015-10-20
You need to undo your changes to the default.pa file. If you cannot figure out how to do that, the easy way is to reinstall the original:
```
sudo rm /etc/pulse/default.pa
sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install pulseaudio
```
Log out and back in and check if sound is restored.

---

### Post by righN on 2015-10-21
Ye, sound is back but anyways. But how i can fix that error for what i got this problem? 

ALSA lib pcm.c:7843:sad:snd_pcm_recover)

---

### Post by Yellow Pasque on 2015-10-21
I played around with it in my Ubuntu VM and found this to work well: [http://wiki.winehq.org/WineAndPulseaudio](http://wiki.winehq.org/WineAndPulseaudio)
Ignore the "Make Pulseaudio not grab the hardware ALSA device" section (i.e. DO NOT edit /etc/pulse/default.pa)
Instead, run:
```
echo "autospawn=no" >> ~/.config/pulse/client.conf
```

Then, create the ~/.asoundrc as the tutorial instructs and reboot the system. Test out the sound:
```
pulseaudio --kill
ALSA_DEFAULT_PCM="plug:dmix" winecfg   #(or maybe winecfg-development if you have wine-development installed)
```

Now, any time you want to run a program in wine, kill pulseaudio first:
```
pulseaudio --kill
ALSA_DEFAULT_PCM="plug:dmix" wine something.exe
pulseaudio&   #restart pulseaudio when you're done
```

Note that if you want to run another program that plays sound while pulseaudio isn't running, you need to start it the same way. So for example, if you want to listen to music in rhythmbox and still hear sound effects from a wine game:
```
pulseaudio --kill
ALSA_DEFAULT_PCM="plug:dmix" rhythmbox&
ALSA_DEFAULT_PCM="plug:dmix" wine something.exe
pulseaudio&
```

---

