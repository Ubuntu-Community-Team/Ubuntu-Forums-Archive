---
title: "No audio, dummy output, no sound card found, ubuntu 18.04"
date: 2018-10-17
forum: Hardware
---

### Post by jpfontenelle on 2018-10-17
[COLOR=#494949][FONT=&amp]Hello. [/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]The soundcard on my t480 stopped working today, after the bios update from system update on ubuntu.[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]running [/FONT][/COLOR]
lsmod | grep snd_hda_intel

[COLOR=#494949][FONT=&amp]returns[/FONT][/COLOR]
snd_hda_intel          40960  0
snd_hda_codec         126976  1 snd_hda_intel
snd_hda_core           81920  2 snd_hda_intel,snd_hda_codec
snd_pcm                98304  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd                    81920  9 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,thinkpad_acpi,snd_rawmidi,snd_seq_device,snd_pcm

[COLOR=#494949][FONT=&amp]when I run[/FONT][/COLOR]
lspci -v

[COLOR=#494949][FONT=&amp]I get no return.[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]when I check for the soundcard with[/FONT][/COLOR]
cat /proc/asound/cards[COLOR=#494949][FONT=&amp]it 

returns no soundcard[/FONT][/COLOR]
jpfontenelle@Wallace:~$ cat /proc/asound/cards
--- no soundcards ---[COLOR=#494949][FONT=&amp]I 

also already tried [/FONT][/COLOR]
sudo alsa force-reload

[COLOR=#494949][FONT=&amp]with no success[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]I've browsed around the internet and I tried to install/purge/remove/reinstall but still no success[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]I even tried to create a bootable usb with ubuntu and boot from it, but still no sound.[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]Any suggestions?[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]Cheers[/FONT][/COLOR]

[COLOR=#494949][FONT=&amp]JP[/FONT][/COLOR]

---

### Post by Autodave on 2018-10-18
Not a lot of thoughts here.  Have you tried going into the BIOS and seeing if the sound has been turned off there?  That is the only thing coming to mind at the moment......

---

