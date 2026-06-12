---
title: "Installation does not work NVIDIA® GeForce® RTX ™ 3060 6GB LENOVO Legion 5, R5-5600H"
date: 2021-12-06
forum: Hardware
---

### Post by pp1 on 2021-12-06
Hi

i have 21.10 installed but the graphic driver if i add a second monitor via hdmi show nothing!

Installation does not work NVIDIA® GeForce® RTX ™ 3060 6GB LENOVO Legion 5, R5-5600H here are instructions 
[https://www.if-not-true-then-false.com/2021/debian-ubuntu-linux-mint-nvidia-guide/](https://www.if-not-true-then-false.com/2021/debian-ubuntu-linux-mint-nvidia-guide/)

This is also visible under additional devices. 460.xx NVIDIA drivers

I cannot connect a 2 monitor via HDMI


How can you correctly install the driver!

here:

[COLOR=#C65D09]**root@xxx:/#**[/COLOR] lspci -nnk | grep -A3 [COLOR=#4070A0]"\[03..\]:"[/COLOR]
[COLOR=#808080]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GA106M [GeForce RTX 3060 Mobile / Max-Q] [10de:2560] (rev a1)[/COLOR]
[COLOR=#808080]	Subsystem: Lenovo GA106M [GeForce RTX 3060 Mobile / Max-Q] [17aa:3a81][/COLOR]
[COLOR=#808080]	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia[/COLOR]
[COLOR=#808080]01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:228e] (rev a1)[/COLOR]
[COLOR=#C65D09]**root@xxx:/#**[/COLOR]

 i have done this

[TABLE="class: topic, width: 1104"]
[TR]
[TD="class: post -own"][INDENT]
[LIST]
[*][FONT=Verdana]Uninstall any parts that have already been installed:[/FONT]
[TABLE="class: notranslate syntaxtable, width: 844"]
[TR]
[TD="class: linenos, align: right"]1
2
[/TD]
[TD="class: code, bgcolor: #F0F0F0"][COLOR=#007020]cd[/COLOR] /
sudo apt purge nvidia*

[/TD]
[/TR]
[/TABLE]


[*][FONT=Verdana]Update package sources, package source contents and installed packages:[/FONT]
[TABLE="class: notranslate syntaxtable, width: 844"]
[TR]
[TD="class: linenos, align: right"]1
[/TD]
[TD="class: code, bgcolor: #F0F0F0"]sudo apt update [COLOR=#666666]&&[/COLOR] sudo apt full-upgrade

[/TD]
[/TR]
[/TABLE]


[*][FONT=Verdana]Install proprietary drivers in the correct version for this GPU:[/FONT]
[TABLE="class: notranslate syntaxtable, width: 844"]
[TR]
[TD="class: linenos, align: right"]1
[/TD]
[TD="class: code, bgcolor: #F0F0F0"]sudo apt install nvidia-driver-465 nvidia-settings

[/TD]
[/TR]
[/TABLE]


[*]Reboot:
[TABLE="class: notranslate syntaxtable, width: 844"]
[TR]
[TD="class: linenos, align: right"]1
[/TD]
[TD="class: code, bgcolor: #F0F0F0"]sudo reboot
[/TD]
[/TR]
[/TABLE]

[/LIST]
[/INDENT]
[/TD]
[/TR]
[TR]
[TD="class: author -own, bgcolor: #EAECEE"][/TD]
[TD="class: post -own"][/TD]
[/TR]
[/TABLE]


But it is not working

how could i fix this?
thx
Peter

---

