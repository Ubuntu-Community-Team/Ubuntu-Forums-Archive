---
title: "No sound from internal speakers after upgrade to 16.04 (headphones work)"
date: 2016-05-05
forum: Hardware
---

### Post by Juhele on 2016-05-05
Hi,
I cannot make my internal speakers work (Dell Latitude E5510 with i3) after upgrade to 16.04.
Tried various threads here, but nothing helped. Multiple purge and reinstall of alsa-base and pulseaudio - no effect, updating packages - no effect... :confused:
Also checked this [thread]("http://ubuntuforums.org/showthread.php?t=1467307&page=3") but nothing worked...

Here is what Alsamixer shows me:

[ATTACH=CONFIG]268862[/ATTACH]

and here is console output for particular commands:

```
$ uname -a
Linux Latitude 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 i686 i686 i686 GNU/Linux
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k4.4.0-21-generic.
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card0/codec#3 <==
Codec: Intel IbexPeak HDMI
$ aplay -l
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
karta 0: MID [HDA Intel MID], za&#345;ízení 0: 92HD81B1X5 Analog [92HD81B1X5 Analog]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 0: MID [HDA Intel MID], za&#345;ízení 3: HDMI 0 [HDMI 0]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0                                                                                           
karta 0: MID [HDA Intel MID], za&#345;ízení 7: HDMI 1 [HDMI 1]                                                                
  Podza&#345;ízení: 1/1                                                                                                       
  Podza&#345;ízení #0: subdevice #0                                                                                           
$    

```

Any ideas?

---

### Post by howefield on 2016-05-05
Thread moved to the "*Hardware*" forum.

---

### Post by Juhele on 2016-05-09
It is strange that **pavucontrol **shows me something called "analog stereo" but marked as "unvailable". The same here:

```
~$ pactl list sinks
Sink #1
        State: RUNNING
        Name: alsa_output.pci-0000_00_1b.0.analog-stereo
        Description: Vnit&#345;ní zvukový systém Analogové stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 48000Hz
        Channel Map: front-left,front-right
        Owner Module: 6
        Mute: no
        Volume: front-left: 53084 /  81% / -5,49 dB,   front-right: 53084 /  81% / -5,49 dB
                balance 0,00
        Base Volume: 65536 / 100% / 0,00 dB
        Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        Latency: 232176 usec, configured 341333 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Properties:                                                                                                       
                alsa.resolution_bits = "16"                                                                               
                device.api = "alsa"                                                                                       
                device.class = "sound"                                                                                    
                alsa.class = "generic"                                                                                    
                alsa.subclass = "generic-mix"                                                                             
                alsa.name = "Generic Analog"                                                                              
                alsa.id = "Generic Analog"                                                                                
                alsa.subdevice = "0"                                                                                      
                alsa.subdevice_name = "subdevice #0"                                                                      
                alsa.device = "0"                                                                                         
                alsa.card = "0"
                alsa.card_name = "HDA Intel MID"
                alsa.long_card_name = "HDA Intel MID at 0xd7d40000 irq 28"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "3b56"
                device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analogové stereo"
                device.description = "Vnit&#345;ní zvukový systém Analogové stereo"
                alsa.mixer_name = "IDT Generic"
                alsa.components = "HDA:111d7605,10280428,00100104 HDA:80862804,80860101,00100000"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Porty:
                analog-output-lineout: Linkový výstup (priority: 9900, not available)
                analog-output-speaker: Analogové stereo (priority: 10000, not available)
                analog-output-headphones: Analogová sluchátka (priority: 9000, available)
        Aktivní port: analog-output-speaker
        Porty:
                pcm
~$ 

```

and output for *pacmd list-cards*

```
~$ pacmd list-cards
1 card(s) available.
    index: 0
        name: <alsa_card.pci-0000_00_1b.0>
        driver: <module-alsa-card.c>
        owner module: 6
        properties:
                alsa.card = "0"
                alsa.card_name = "HDA Intel MID"
                alsa.long_card_name = "HDA Intel MID at 0xd7d40000 irq 28"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "3b56"
                device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
                device.form_factor = "internal"
                device.string = "0"
                device.description = "Vnit&#345;ní zvukový systém"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                input:analog-stereo: Analogové stereo vstup (priority 60, available: unknown)
                output:analog-stereo: Analogové stereo výstup (priority 6000, available: unknown)
                output:analog-stereo+input:analog-stereo: Analogové duplexní stereo (priority 6060, available: unknown)
                output:hdmi-stereo: Digital Stereo (HDMI) výstup (priority 5400, available: unknown)
                output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) výstup + Analogové stereo vstup (priority 5460, available: unknown)
                off: Vypnuto (priority 0, available: unknown)
        active profile: <output:analog-stereo>
        sinks:
                alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Vnit&#345;ní zvukový systém Analogové stereo
        sources:
                alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#2: Monitor of Vnit&#345;ní zvukový systém Analogové stereo
        ports:
                analog-input-internal-mic: Interní mikrofon (priority 8900, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-dock-mic: Mikrofon dokovací stanice (priority 7800, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-mic: Mikrofon (priority 8700, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-output-lineout: Linkový výstup (priority 9900, latency offset 0 usec, available: no)
                        properties:

                analog-output-speaker: Analogové stereo (priority 10000, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-speakers"
                analog-output-headphones: Analogová sluchátka (priority 9000, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "audio-headphones"
                hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "video-display"
~$ 

```


No idea... Never had problem with audio.

---

### Post by Juhele on 2016-11-20
OK,
problem solved for now although I have absolutely no idea how I did it :lolflag:

I just started (after a really long time) the Windows XP I have in dualboot. I just tried whether the problem with no sound from speakers is also there. Sound worked and after reboot is also started to work in Kubuntu.

strange :confused:

---

### Post by PopsTheSailor on 2017-03-11
I know this thread is getting old but here is what I did to fix it. Although I use Ubuntu MATE but on 16.04 so not sure this will work or the directions will be exactly the same. I use a diff UI from Unity. Also note, I had both my laptop volume and app volumes turned up and it still showed up at 0 volume in step 7 below. I hope this helps someone. It's plagued me for a long time. It also fixed youtube / online video sounds. They now play. I'd post some screenshots but I guess I have to save them somewhere online and then insert the URL. Have no idea where to save them.

Good Luck

1. Go to Menu
2. Go to Sound
3. Click on Preferences
4. Go to applications
5. Start the application you want to have sound playing from your speakers
6. Wait a bit (a few seconds) for the application to show up on the list
7. All my apps had the sound set to 0 or off. 
8. Set the volume 
9. Listen and enjoy
10. I just found this an have not turned off my laptop yet so I have no idea if the volumes stay up or you have to set each time. I'm about to find out.

---

