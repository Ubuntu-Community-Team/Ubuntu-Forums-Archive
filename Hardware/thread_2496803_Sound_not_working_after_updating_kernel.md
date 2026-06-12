---
title: "Sound not working after updating kernel"
date: 2024-04-13
forum: Hardware
---

### Post by renato-cavalcante on 2024-04-13
[COLOR=#0D0D0D][FONT=Söhne]Hey everyone,[/FONT][/COLOR]
[COLOR=#0D0D0D][FONT=Söhne]I've been encountering an issue with my Dell G3 running Ubuntu 22.04. Everything was  fine until I updated my system last week with a new kernel using the commands:[/FONT][/COLOR]

 >>> sudo apt update
>>> sudo apt dist-upgrade


[COLOR=#0D0D0D][FONT=Söhne]Since then, my audio has gone silent. In the system settings under Sound, I now see "Cannon Lake PCH cAVS" as the output device, whereas it used to show something else. Adding
[/FONT][/COLOR]
>>> GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=#00A67D]"quiet splash snd_hda_intel.dmic_detect=0"[/COLOR]

[COLOR=#0D0D0D][FONT=Söhne]to /etc/default/grub restores the audio, but unfortunately, my microphone no longer works. It seems like there might be a regression in the latest kernel update. Has anyone else encountered a similar issue? Any ideas or suggestions would be greatly appreciated![/FONT][/COLOR]

---

### Post by renato-cavalcante on 2024-04-20
[COLOR=#0D0D0D][FONT=Söhne]Hi everyone,[/FONT][/COLOR]
[COLOR=#0D0D0D][FONT=Söhne]I wanted to share a solution for this issue I was experiencing with my computer's sound. Despite having the volume set to the maximum in Settings -> Sound, I couldn't hear anything from the internal speaker. After some troubleshooting, I managed to fix the problem, and here's how:[/FONT][/COLOR]

[LIST=1]
[*]Open your terminal.
[*]Type alsamixer and press Enter to launch the mixer.
[*]Press F6 to select your sound card. In my case, I chose "sof-hda-dsp."
[*]Navigate to "PGA 1.0" and "PGA 3.0."
[*]Increase the volume bars to maximum for these settings.
[/LIST]
[COLOR=#0D0D0D][FONT=Söhne]This adjustment brought the sound back on my system. I hope this helps anyone facing a similar issue![/FONT][/COLOR]

---

