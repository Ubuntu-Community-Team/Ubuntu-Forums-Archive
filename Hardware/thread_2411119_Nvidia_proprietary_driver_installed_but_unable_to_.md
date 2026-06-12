---
title: "Nvidia proprietary driver installed but unable to switch in X Server Setting"
date: 2019-01-24
forum: Hardware
---

### Post by frostweskbrok on 2019-01-24
[COLOR=#242729][FONT=Arial]I have a Thinkpad T460s which has an Intel HD520 as well as Nvidia 930M graphics card. I want to install the driver for the 930M.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I installed the proprietary nvidia-driver-390 and switch to it software & updates:
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/8N2Du.png[/IMG]
[COLOR=#242729][FONT=Arial]
But I could not find the PRIME option in Nvidia X Server Settings, and I can still only use the integrated graphics card:
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/chQJh.png[/IMG]
[IMG]https://i.stack.imgur.com/tVE5h.png[/IMG]

[COLOR=#242729][FONT=Arial]Still new to Ubuntu and any help is appreciated, thank you![/FONT][/COLOR]

---

### Post by mikasu on 2019-01-26
Have you tried the drivers from the graphics drivers ppa? I use the 415 from that ppa and my GPU is a 840M. Just mentionning, don't expect dynamic switching like on Windows. Apparently Manjaro got it working but it's not there yet for Ubuntu, eve on 18.04. It's full nVidia rendering or full Intel rendering saddly :(

---

### Post by frostweskbrok on 2019-01-31
HI there, how can I choose / install the option of other ppa drivers? Since the 390 is the only option I get from the list? Thanks!

---

