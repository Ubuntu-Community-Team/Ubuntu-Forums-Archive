---
title: "Sound and Headphones"
date: 2017-11-10
forum: Hardware
---

### Post by Bigpat on 2017-11-10
[COLOR=#222222][FONT=&amp]I may have posted this in the past I don't remember getting an answer. Currently I have switch to Ubuntu mate and the reason [/FONT][/COLOR][COLOR=#222222][FONT=&amp]for the [/FONT][/COLOR][COLOR=#222222][FONT=DejaVu Sans]switches is at the time I was using Mint 17 and after I update to 18.2 well I got that black screen and I was unable to get rid of it. It so happened that after I installed Ubuntu Mate I had the same issue and because I [/FONT][/COLOR][COLOR=#222222][FONT=&amp]instantly [/FONT][/COLOR][COLOR=#222222][FONT=&amp]fell in love with Mate so I decided run with it.[/FONT][/COLOR]


[FONT=DejaVu Sans][COLOR=#222222]Myissue as always been the same for every version of Ubuntu Iinstalled. When I input my headphones it does not auto switch to theheadphones I have to manually do myself unlike windows Computer [/COLOR][COLOR=#222222]whenthe headphone sare plugged in the main speaks are muted and only theheadphones work and then after the headphones are removed the mainspeakers are back on again so to speak.[/COLOR][/FONT]

[FONT=DejaVu Sans][COLOR=#222222]I have an AMD/ATI RV710 Radeon HD 4350/4550 which also does sound via HDMI. .Also, on board sound on motherboard [/COLOR][/FONT]
[FONT=DejaVu Sans][COLOR=#222222]The worst part is I have no idea what my computer is using. Meaning I'm I using my HDMI for sound and video as my current hook up monitor is HDMI or my regular on board sound?[/COLOR][/FONT]

[COLOR=#222222][FONT=DejaVu Sans]How do I get my head phones to auto select and mute the main speaks until I remove them. Just like a windows computer.[/FONT][/COLOR]

[FONT=DejaVu Sans][COLOR=#222222]I have my video and audio terminal output below if this helps.[/COLOR]

**Videooutput**[/FONT]
[FONT=DejaVu Sans]
lspci -nnk | grep VGA -A1
[/FONT]
[FONT=DejaVu Sans]01:00.0 VGA compatiblecontroller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710[Radeon HD 4350/4550] [1002:954f][/FONT]
[FONT=DejaVu Sans]    Subsystem: Gigabyte TechnologyCo., Ltd RV710 [Radeon HD 4350/4550] [145[/FONT]


**[FONT=DejaVu Sans]Audio output[/FONT]**
[FONT=DejaVu Sans]
lspci -v | grep -A7 -i "audio"
[/FONT]
[FONT=DejaVu Sans]00:14.2 Audio device: AdvancedMicro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)[/FONT]
[FONT=DejaVu Sans]    Subsystem: ASRock IncorporationSBx00 Azalia (Intel HDA)[/FONT]
[FONT=DejaVu Sans]    Flags: bus master, slow devsel,latency 32, IRQ 16[/FONT]
[FONT=DejaVu Sans]    Memory at feb00000 (64-bit,non-prefetchable) [size=16K][/FONT]
[FONT=DejaVu Sans]    Capabilities: <accessdenied>[/FONT]
[FONT=DejaVu Sans]    Kernel driver in use:snd_hda_intel[/FONT]
[FONT=DejaVu Sans]    Kernel modules: snd_hda_intel
[/FONT]
[FONT=DejaVu Sans]--[/FONT]
[FONT=DejaVu Sans]01:00.1 Audio device: AdvancedMicro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000series][/FONT]
[FONT=DejaVu Sans]    Subsystem: Gigabyte TechnologyCo., Ltd RV710/730 HDMI Audio [Radeon HD 4000 series][/FONT]
[FONT=DejaVu Sans]    Flags: bus master, fast devsel,latency 0, IRQ 32[/FONT]
[FONT=DejaVu Sans]    Memory at fea30000 (64-bit,non-prefetchable) [size=16K][/FONT]
[FONT=DejaVu Sans]    Capabilities: <accessdenied>[/FONT]
[FONT=DejaVu Sans]    Kernel driver in use:snd_hda_intel[/FONT]
[FONT=DejaVu Sans]    Kernel modules: snd_hda_intel[/FONT]


[FONT=DejaVu Sans]02:00.0 USB controller: EtronTechnology, Inc. EJ168 USB 3.0 Host Controller (rev 01) (prog-if 30[XHCI])

[/FONT]
Please note I may have asked this in the past but I don&#8217;t think I ever got a correct answer.
I need to be able to put my headphones in and hear sound at the same time my main volume speaks are muted until my headphones are removed just like a windows desktop environment.
[FONT=DejaVu Sans]

[/FONT]

---

### Post by untrustytahr on 2017-11-10
I had a similar problem although not using hdmi... mine was switching between laptop speakers, bluetooth headset, & normal earbuds.  This link worked for me:
[https://wiki.archlinux.org/index.php/PulseAudio#Switch_on_connect](https://wiki.archlinux.org/index.php/PulseAudio#Switch_on_connect)

I used the switch-on-connect.  If you want to test it type this command in a terminal:

```
pactl load-module module-switch-on-connect
```

If it fixes it, you have to make it permanent by adding this line to /etc/pulse/default.pa :
```
load-module module-switch-on-connect
```

---

