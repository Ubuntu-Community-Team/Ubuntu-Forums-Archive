---
title: "No integrated audio on new HP 15s-eq3030nl"
date: 2023-03-20
forum: Hardware
---

### Post by nappa85 on 2023-03-20
Long story short, I bought this notebook blindfolded because I needed it ASAP.
I've installed Kubuntu 22.10, everything works, except for integrated audio, both speakers/heaphones and microphone.
HDMI audio works, Bluetooth audio works, so I've a temporary workaround.
This is my hardware probe: [https://linux-hardware.org/?probe=83fbe3a3d6](https://linux-hardware.org/?probe=83fbe3a3d6)

What's really strange, is that the hardware seems to be recognized, but alsamixer shows no volumes for it:
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/alsamixer0.jpg[/IMG][IMG]https://raw.githubusercontent.com/nappa85/storage/master/alsamixer1.jpg[/IMG][IMG]https://raw.githubusercontent.com/nappa85/storage/master/alsamixer2.jpg[/IMG]

sudo inxi -Fxa

[FONT=monospace][COLOR=#5454ff]**Audio:**[/COLOR]
  [COLOR=#5454ff]**Device-1:**[/COLOR][COLOR=#000000] AMD Renoir Radeon High Definition Audio [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR]
    [COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454ff]**pcie:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 3 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 8 GT/s [/COLOR][COLOR=#5454ff]**lanes:**[/COLOR][COLOR=#000000] 16 [/COLOR]
    [COLOR=#5454ff]**link-max:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 4 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 16 GT/s [/COLOR][COLOR=#5454ff]**bus-ID:**[/COLOR][COLOR=#000000] 03:00.1 [/COLOR][COLOR=#5454ff]**chip-ID:**[/COLOR][COLOR=#000000] 1002:1637 [/COLOR]
    [COLOR=#5454ff]**class-ID:**[/COLOR][COLOR=#000000] 0403 [/COLOR]
  [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] AMD ACP/ACP3X/ACP6x Audio Coprocessor [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR]
    [COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_rn_pci_acp3x [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR]
    [COLOR=#5454ff]**alternate:**[/COLOR][COLOR=#000000] snd_pci_acp3x,snd_pci_acp5x,snd_pci_acp6x,snd_acp_pci,snd_pci_ps,snd_sof_amd_renoir [/COLOR]
    [COLOR=#5454ff]**pcie:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 3 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 8 GT/s [/COLOR][COLOR=#5454ff]**lanes:**[/COLOR][COLOR=#000000] 16 [/COLOR][COLOR=#5454ff]**link-max:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 4 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 16 GT/s [/COLOR]
    [COLOR=#5454ff]**bus-ID:**[/COLOR][COLOR=#000000] 03:00.5 [/COLOR][COLOR=#5454ff]**chip-ID:**[/COLOR][COLOR=#000000] 1022:15e2 [/COLOR][COLOR=#5454ff]**class-ID:**[/COLOR][COLOR=#000000] 0480 [/COLOR]
  [COLOR=#5454ff]**Device-3:**[/COLOR][COLOR=#000000] AMD Family 17h/19h HD Audio [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR]
    [COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454ff]**pcie:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 3 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 8 GT/s [/COLOR][COLOR=#5454ff]**lanes:**[/COLOR][COLOR=#000000] 16 [/COLOR]
    [COLOR=#5454ff]**link-max:**[/COLOR][COLOR=#5454ff]**gen:**[/COLOR][COLOR=#000000] 4 [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 16 GT/s [/COLOR][COLOR=#5454ff]**bus-ID:**[/COLOR][COLOR=#000000] 03:00.6 [/COLOR][COLOR=#5454ff]**chip-ID:**[/COLOR][COLOR=#000000] 1022:15e3 [/COLOR]
    [COLOR=#5454ff]**class-ID:**[/COLOR][COLOR=#000000] 0403 [/COLOR]
  [COLOR=#5454ff]**Sound Server-1:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k5.19.0-35-generic [/COLOR][COLOR=#5454ff]**running:**[/COLOR][COLOR=#000000] yes [/COLOR]
  [COLOR=#5454ff]**Sound Server-2:**[/COLOR][COLOR=#000000] PipeWire [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 0.3.58 [/COLOR][COLOR=#5454ff]**running:**[/COLOR][COLOR=#000000] yes

[/COLOR]
My alsa-info: [http://alsa-project.org/db/?f=f11765d1c0fff7ffbd7fc5f10f87fe590651f60f](http://alsa-project.org/db/?f=f11765d1c0fff7ffbd7fc5f10f87fe590651f60f)
Scrolling down on aplay you can see it recognizes only HDMI output

wireplumber spams a lot of errors like those:
[/FONT][IMG]https://raw.githubusercontent.com/nappa85/storage/master/wireplumber.png[/IMG]

I tryed upgrading to Kubuntu 23.04, no changes.
I tryed using kernel 6.2.7 from mainline, no changes.
I'm out of ideas

---

### Post by nappa85 on 2023-03-21
Little update:
I don't know if it's related, but yesterday I installed pipewire-alsa, this morning I rebooted the notebook and the internal audio started working.
alsamixer now shows a new card with volumes
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/alsamixer3.png[/IMG]

---

### Post by nappa85 on 2023-03-21
Another update:
KDE's audio config is behaving really strange here.
I was searching for how to force the audio output to my headphones, and I found the "Port" select:
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/KDEaudio1.png[/IMG]
While on "Speaker" it works correctly, audio goes on the selected card, no surprises.
As soon as I select "Headphones" card selection returns to HDMI
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/KDEaudio2.png[/IMG]
More, I can select second card, the first one remains selected
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/KDEaudio3.png[/IMG]
Same thing happens on audio control on systray
[IMG]https://raw.githubusercontent.com/nappa85/storage/master/KDEaudio4.png[/IMG]
As you can see on the lighter blue, the audio is currently going on the headphones, but the selected card is HDMI

---

### Post by nappa85 on 2023-03-23
New update: the thing is completely random.
After every reboot I can find the integrated audio card or only the HDMI output

---

