---
title: "Notion Ink Cain"
date: 2015-06-23
forum: Hardware
---

### Post by sonic414 on 2015-06-23
Hi,
I'm the owner of a Notion Ink Cain 10'' 2 in 1 Tablet. There are some h/w problems when I installed Ubuntu Gnome 15.04 . 

The things not working are

1) Audio
Sound Hardware is not recognized by the kernel - AFAIK, it uses Baytail SOC BYT-RT5640.
Relevant Dmesg log:
```
[    7.731468] baytrail-pcm-audio baytrail-pcm-audio: error: invalid DMA engine 0
[    7.731480] baytrail-pcm-audio baytrail-pcm-audio: sst_dma_new failed -22
[    7.957729] baytrail-pcm-audio baytrail-pcm-audio: ipc: error DSP boot timeout
[    7.958029] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not registered
[    7.958065] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
```

2) 8723BS Wifi / Bluetooth

[https://github.com/endlessm/linux-meson/commit/dfd191846b597c67220ce2bf98f31fdac03f39a3](https://github.com/endlessm/linux-meson/commit/dfd191846b597c67220ce2bf98f31fdac03f39a3)
[https://github.com/endlessm/linux-meson/commit/d1fc61853c2327a12af805efa01d59bda72e1457](https://github.com/endlessm/linux-meson/commit/d1fc61853c2327a12af805efa01d59bda72e1457)

Both the above commits seems related to the bluetooth and wifi respectively..

I had some success in building the wifi modules. But the performance is slow. Moreover the whole system hangs after some time. I haven't been able to get any log details of that.
The funny thing is that if I use a firefox browser and browse the internet while the system is upgrading in the backgroud, I get around 200kbps , otherwise the speed remains around 4kbps.

3) Power/Charger/Battery Estimate/Power Button
It uses AXP288 X-Power chip for charging discharging. But it doesn't work. 

uname -a
```
Linux NotionInk-Sonic 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Attaching logs and DSDT
[ATTACH]262797[/ATTACH]
[ATTACH]262798[/ATTACH]
[ATTACH]262799[/ATTACH]
[ATTACH]262800[/ATTACH]

Sorry, had to zip files because the txt size was large.

Please HELP! :(

---

