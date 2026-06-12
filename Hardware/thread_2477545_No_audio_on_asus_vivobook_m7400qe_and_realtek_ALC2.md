---
title: "No audio on asus vivobook m7400qe and realtek ALC294"
date: 2022-07-29
forum: Hardware
---

### Post by Mangus on 2022-07-29
Hi.
I've just bought a new asus vivobook m7400qe (ryzen, nvidia rtx, 16gb ram, etc), with the onboard notorius REALTEK ALC294 audio chipset

Setup:
dual boot with windows 11 pro and ubuntu 22.04 (I need both).

Installed windows and everything is fine.
Installed ubuntu and everything is fine EXCEPT the audio:
- mic works correctly
- NO AUDIO FROM ONBOARD SPEAKERS and neither from the headphones jack.
If I connect the headphone jack I hear some cracks an bumps but no audio at all.

The audio output is recognized as "speakers: family 17h (models 10h-1fh) HD audio controller"

I'm working on this problem in the last 4 days without any success.
I've read hundreds of workaround, guides, bug reports etc, tried everything I found but with no success at all.

The ONLY workaround that worked is this, but with a HUGE "but":
[https://askubuntu.com/questions/1394452/sound-not-working-on-ubuntu-20-04-asus-vivobook-pro]("https://askubuntu.com/questions/1394452/sound-not-working-on-ubuntu-20-04-asus-vivobook-pro")

> 
After a lot of research through the internet, I got a temporary solution to fix this issue.

sudo #!/bin/bash
sudo hda-verb /dev/snd/hwC0D0 0x20 0x500 0x1b
sudo hda-verb /dev/snd/hwC0D0 0x20 0x477 0x4a4b
sudo hda-verb /dev/snd/hwC0D0 0x20 0x500 0xf
sudo hda-verb /dev/snd/hwC0D0 0x20 0x477 0x74

Run this script then use the power button to shutdown your system(The normal power Off/restart/ with sudo privilege also didn't fix). I don't know how but this fixed my system. This will solve the issue until you boot to windows again, then you have to redo the process. I don't know if there is any other methods available to fix this issue permanently, but this is the only method that worked for me after trying multiple methods.


Trying this, at the next boot audio works but if I boot on windows, and then to ubuntu again, the audio is gone again, as the guy says in the link that I quoted.
I tried putting the script in crontab (even root's crontab), to execute at every boot but if a boot to windows is involved, then still no audio on ubuntu next time.
Other quirk thing is that sometime, when I boot to windows, audio is broken there too and I need to reinstall the realtek drivers there.

Also disabled fastboot (both on windows AND bios), but no luck. Tried reinstalling alsa, pulseaudio, resetting all. Nothing.

I'm desperate, I need this to work, it's a notebook that was given to me from my employer and I have to keep this one. No way he would change it with another model.

here some useful info:
```

$ cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfc5c8000 irq 87
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfc5c0000 irq 88

```

```
$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Generic_1 [HD-Audio Generic], dispositivo 0: ALC294 Analog [ALC294 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
```

```
$ inxi -SMA
System:
  Host: nbced04 Kernel: 5.15.0-43-generic x86_64 bits: 64 Desktop: GNOME 42.2
    Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: ASUSTeK product: Vivobook_ASUSLaptop M7400QE_M7400QE
    v: 1.0 serial: <superuser required>
  Mobo: ASUSTeK model: M7400QE v: 1.0 serial: <superuser required>
    UEFI: American Megatrends LLC. v: M7400QE.307 date: 03/07/2022
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor driver: N/A
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-43-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

---

### Post by Yellow Pasque on 2022-08-01
This is a longshot, but make sure this isn't interfering, especially when your sound doesn't work in Windows: [https://www.asus.com/us/support/FAQ/1046946](https://www.asus.com/us/support/FAQ/1046946)

---

### Post by Mangus on 2022-08-08
> **Yellow Pasque said:**
> This is a longshot, but make sure this isn't interfering, especially when your sound doesn't work in Windows: [https://www.asus.com/us/support/FAQ/1046946](https://www.asus.com/us/support/FAQ/1046946)

I do not have that feature on my notebook.
Also, I kept the notebook turned off a couple of days and next time I used it the audio worked like a charm, in ubuntu and windows. Without any update installed in the between or any workaround activated.

Now I'm hoping to not have to format the computer anytime soon bc I absolutely don't know what happened and how to replicate that.

---

### Post by shakealot on 2022-09-13
> **Mangus said:**
> I do not have that feature on my notebook.
Also, I kept the notebook turned off a couple of days and next time I used it the audio worked like a charm, in ubuntu and windows. Without any update installed in the between or any workaround activated.

Now I'm hoping to not have to format the computer anytime soon bc I absolutely don't know what happened and how to replicate that.
Hi Mangus,

I'm facing the same problem, with the same computer, is your issue definitively solved ?
I have a dual boot with Windows, and I noticed that since I installed Ubuntu 22.04, when I come back to Windows the sound doesnt work but I can hear loud "plops" sound from onboard speakers. And when I reboot the computer again on Windows, the sound is back to normal.

Do you experiment the same thing ?

Best regards

---

### Post by Mangus on 2022-09-13
> **shakealot said:**
> Hi Mangus,

I'm facing the same problem, with the same computer, is your issue definitively solved ?
I have a dual boot with Windows, and I noticed that since I installed Ubuntu 22.04, when I come back to Windows the sound doesnt work but I can hear loud "plops" sound from onboard speakers. And when I reboot the computer again on Windows, the sound is back to normal.

Do you experiment the same thing ?

Best regards

Hi, honestly I don't know how to put it.
It's "solved" but I don't know how. If I reboot, often I have problems. If after using windows I shut down (no reboot), the system and then power up it again in ubuntu, the sound seems fine.
It's a very strange situation.

---

### Post by shakealot on 2022-09-13
> **Mangus said:**
> Hi, honestly I don't know how to put it.
It's "solved" but I don't know how. If I reboot, often I have problems. If after using windows I shut down (no reboot), the system and then power up it again in ubuntu, the sound seems fine.
It's a very strange situation.

It's not working for me, I've tried different scenarios (I have to reboot twice when I'm coming from Ubuntu and get back to Windows) but I never get to hear the sound with Ubuntu.

---

### Post by mteijpe on 2023-06-20
It's been almost a year, have you found a solution to this issue? I bought my m7400qe a few months ago and wanted to try dualbooting windows and ubuntu 23.04 though the issue is still present (unfortunately).

---

### Post by Mangus on 2023-06-21
> **mteijpe said:**
> It's been almost a year, have you found a solution to this issue? I bought my m7400qe a few months ago and wanted to try dualbooting windows and ubuntu 23.04 though the issue is still present (unfortunately).

Sadly, no news about it.
I've reinstalled ubuntu with dual boot just last week. 
If I start the notebook with ubuntu, sound is ok.
If I start with windows, sound is ok.

IF AFTER USING WINDOWS, I just reboot to ubuntu, sound is broken.
To get it work again I have to: SHUTDOWN from windows (just reboot doesn't work), than unplug the power supply from notebook, then start the notebook and only then, attach the power supply again.
This way, sound is working again in ubuntu.

I absolutely doesn't know what's the problem, it seems to me that windows somehow "block" some resources until the pc is shut down and Ubuntu cannot claim them when it boots.
Maybe the full shutdown releases these resources somehow, I don't know.
Other than that, the power supply must be unplugged to get that work.

It's a very strange behavior and I don't have enough knowledge to debug it. Sorry.

BTW, this notebook is a very beast, maybe the best notebook I've ever had.

---

### Post by jaapz2 on 2024-03-13
Have been struggling with the same  problem for weeks.
Tried all the more advanced solutions (reinstall ALSA, Pipewire, etc.: to no avail. :(
Followed the instruction for the "silly"  (shutdown from Win, unplug power, start ubuntu) solution: presto! :D

---

### Post by mythicshockwavehammer on 2024-04-11
"sudo: hda-verb: command not found" :(

---

