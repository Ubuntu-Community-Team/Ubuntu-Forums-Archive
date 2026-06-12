---
title: "Dell XPS 15 7590 Ubuntu 20.04 stop booting after kernel 5.11.0 update"
date: 2021-09-02
forum: Hardware
---

### Post by roockycoller on 2021-09-02
[COLOR=#111111][FONT=Roboto]I manage to get Ubuntu 20.04 working on my Dell XPS 15 7590 with some difficulty but it was running ok. Until I updated the Generic Linux kernel and headers to version 5.11.0.25.27. This update completely breaks my computer and it no longer boots into Ubuntu. It only shows a blinking cursor in a black screen and that is all. Sometimes (don't know exactly the sequence to get this error) when doing a reset I get the following error instead of the blinking cursor:

[/FONT][/COLOR]snd_hda_intel 0000:00:1f.3: control 2:0:00CM Playback Volumen:0 is already present

[COLOR=#111111][FONT=Roboto]Now, if I try to install Ubuntu 20.04.03 from scratch (erasing everything in the disk) and I reboot again the same thing, I have to go back to Ubuntu 20.04.02 to be able to boot into Ubuntu.

[/FONT][/COLOR]

[COLOR=#111111][FONT=Roboto]Does anyone is having the same issue when updating?[/FONT][/COLOR]
[COLOR=#111111][FONT=Roboto]Thanks in advance.[/FONT][/COLOR]

---

### Post by oldfred on 2021-09-02
Usually black screen relates to not correctly installing nVidia driver?
How have you installed it? From Ubuntu repository & as part of new install?

Other issues with older Ubuntu:
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)

---

