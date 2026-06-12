---
title: "Xubuntu crach"
date: 2015-12-22
forum: Hardware
---

### Post by alo12 on 2015-12-22
Hellow,

Iam using xubuntu for two months now and iam really imprerssed by the utilities that this free softwarwe provides. Unfotunately  i often come across with "computers craches" that force me to restart the computer. I have to restart my computer when my screen look like [this]("http://www.screencast.com/t/1UA3ERH1t") or like [this]("http://www.screencast.com/t/GBnT6PAd"). As iam a new user of xubuntu and genearally of linux could you please help me find a solution to this problem? Thank you in advance.

My computer specs are the following
[COLOR=#3C3B37][FONT=Verdana]2 Ubuntu 14.04 trusty 3.19.0-39-generic 64bit (en_US.UTF-8, XFCE xubuntu), Ubuntu 3.19.0-37-generic
3 Intel Xeon CPU E5405 2.00GHz &#8214; RAM 3949 MiB &#8214; Dell Inc. 0RW203 - Dell Inc. Precision WorkStation T5400
4 nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau} &#8942; nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau}
5 eth0: Broadcom NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
[/FONT][/COLOR]
[RIGHT][COLOR=#E9E9E9][FONT=Verdana][URL="http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=31843#wrap"][URL="http://forum.ubuntu-gr.org/print_post.php?f=4&p=334387"]
&#917;&#954;&#964;&#973;&#960;&#969;&#963;&#951;[/URL]&#922;&#959;&#961;&#965;&#966;&#942;[/URL][/FONT][/COLOR][/RIGHT]
[COLOR=#E9E9E9][FONT=Verdana][/FONT][/COLOR]

---

### Post by kc1di on 2015-12-22
I would say it't the nouveau driver that your using.  Go to all settings icon (bottom left of menu ) then to additional drivers click on that see if it offers you a new driver if so install it. And reboot. See if that solves the problem -- good luck ;)

for your card it should be the nvidia-304.  driver.

If you can't find it in the additional driver app.
you can install it from a terminal with this command:```
sudo apt-get install nvidia-304
```

---

### Post by alo12 on 2015-12-22
thank you for your answer. could you please tell me which one i should install from [these]("http://www.screencast.com/t/NDFRlhcx")

---

### Post by kc1di on 2015-12-22
Nvidia 304.131  ***(Not the -updates one)***

It's the 4th one down ..

---

### Post by alo12 on 2015-12-22
i have follow your advice and the pv look to work fine now. thank you.

---

### Post by kc1di on 2015-12-22
Your Welcome , Enjoy :)

---

### Post by alo12 on 2015-12-23
Since i have change the drivers the computer hasn't crashed but when i open the computer before i see the xubuntu welcome page i see for a while a message says" ACPI PCC probe failed". Is this a problem?
Thank you in advance.

---

### Post by gordintoronto on 2015-12-23
It's a warning, you can ignore it.

> **alo12 said:**
> Since i have change the drivers the computer hasn't crashed but when i open the computer before i see the xubuntu welcome page i see for a while a message says" ACPI PCC probe failed". Is this a problem?
Thank you in advance.

---

### Post by wsteffen on 2016-02-04
This fixed a problem of "garbage full screen" on xubuntu 14.04. I changed from an "X" driver to an NVIDIA driver.

---

### Post by alo12 on 2016-02-04
hello,

Even though after the changes I have  made to the drivers, my system still crashed sometimes when I open some websites such as the google maps...

---

