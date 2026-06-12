---
title: "Missing HDMI audio output, NVidia audio card not detected"
date: 2016-09-07
forum: Hardware
---

### Post by girishankar7 on 2016-09-07
[COLOR=#111111][FONT=Ubuntu]My **ALSA information** is located at:
[http://www.alsa-project.org/db/?f=85ca372146c77ccef3fd60151d30fb86dd6c2dcf](http://www.alsa-project.org/db/?f=85ca372146c77ccef3fd60151d30fb86dd6c2dcf)
*Introduction:*
I'm running **Ubuntu 16.04** with an **NVidia chipset 'GeForce GT 525M'**.
I've installed the **proprietary tested driver** of NVidia, **version 361.42** as suggested in 'Softwares and updates' section. I'm able to connect my laptop to my Sony Bravia TV 48W600B using a HDMI cable and I'm getting the video output perfectly.
*Problem Statement:*
The problem I'm facing is that I'm not getting any audio output.
NVidia audio card is not detected. In /proc/asound, I don't find an NVidia folder, but a PCH folder(the one for Intel), exists.
*Probes*:
i.) Command: aplay -l
Result:[INDENT]**** List of PLAYBACK Hardware Devices ****  card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]    Subdevices: 1/1    Subdevice #0: subdevice #0  card 0: PCH [HDA Intel PCH], device 1: ALC665 Digital [ALC665 Digital]    Subdevices: 1/1    Subdevice #0: subdevice #0  card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]    Subdevices: 1/1    Subdevice #0: subdevice #0  
[/INDENT]
ii.) Command:
lspci
Result:[INDENT]00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)
[/INDENT]
As you can see, there is no HDMI audio device listed.
*Things I've tried (with the help of various other links):*

[LIST=1]
[*]I tried going to sound settings but I don't see any HDMI option there.
[*]I tried pulseaudio -k but in vain.
[*]I opened alsamixer and there is no HDMI audio device listed when I press 'F6'.
[*]I tried using the command sudo adduser $Username audio and got myself added to the audio group, with no effect.
[*]If I use the command pactl set-card-profile 0 output:hdmi-surround, I get the HDMI 5.1 and 7.1 output option under 'Digital Output(S/PDIF)', but it doesn't work when I test it. Soon, the option disappears when I go back. And I'm not able to increase the**S/PDIF volume** from alsamixer window either.
[*]Ran the following utility to get static. speaker-test -c 2 -r 48000 -D hw:0,3. Did not get any noise.
[*]And finally, I had installed pavucontrol and set the [configuration]("http://i.stack.imgur.com/RhByW.png") as '**HDMI output+Analog Input**'. There is a dummy output and no sound.
[/LIST]
[/FONT][/COLOR]

---

### Post by gordintoronto on 2016-09-08
What makes you believe the laptop contains an Nvidia audio card? It has "optimus" technology, for which there is lots of information on the web, but it's not clear whether that is just for the display or it also includes audio.

BTW, "HDMI" is not a property of an audio device. HDMI is just a type of plumbing which might be attached to the audio device.

When you are not connected to the TV, do you get sound from the laptop's speakers? Do you have headphones you can plug in to test that option?

---

