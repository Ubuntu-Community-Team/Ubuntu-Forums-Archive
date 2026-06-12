---
title: "System does not switch automatically to my headphones"
date: 2021-11-13
forum: Hardware
---

### Post by cafebagels08 on 2021-11-13
Hi,

I've got an issue where my headphones are not properly detected in **Ubuntu 21.10** when I plug them on the front plug of my desktop PC. However, they work fine if I booted the computer with my headphones already plugged in and I don't have any issue with my sound switching  automatically to my DisplayPort monitor once I unplug them. The problem is that whenever I plug them back into my front plug, they are not detected in the system.

One of the ways that I've been able to switch back my sound to my headphones without rebooting my PC was to user **pavucontrol**. Once I was in it, I would then go to the "Configuration" tab, then switch the profile of the audio controller of my front plug from "Off" to anything else, then it would start detecting it and switch the profile automatically to "Duplex stereo analog". Then, my headphones start working as they should.

Another way to get it working was simply to open **HDAJackRetask**. Whenever I open it, my headphones start working as they should.

To me, it seems to be some kind of polling issue or some sort, where whenever I unplug the my headphone jack, the system stops checking whether there's something plugged in into that plug or not, but when I open **HDAJackRetask**, it checks my sound car and then it finds that something is plugged in into it. This is just my theory and I don't have the technical knowledge to verify that. However, this is what I can confirm :
[LIST]
[*]It is not a hardware issue, since I have no problem with Windows 10. 
[*]On my other laptop, which runs Ubuntu as well, with the same headphones, things just worked as they should out the box, with no config required. 
[*]I tried with  Fedora 35 on the same desktop PC in the live environment and I had exactly the same issue than with Ubuntu, so it's probably not a Ubuntu specific issue. I haven't tried any other distribution. 
[*]All the packages on my computer are up-to-date. 
[*]I've had this issue since I installed Ubuntu for the first time on this PC. I've never tested any other Linux/BSD distro before that, so I can't tell whether this is a new issue or not. 
[/LIST]

As I said before, I am using **Ubuntu 21.10** (x64) and these is my hardware specs :
[LIST]
[*]PC: Dell Inspiron 5675 
[*]CPU: AMD Ryzen 1700X 
[*]Sound card for my front-panel plug: Family 17h (Models 00h-0fh) HD Audio Controller 
[*]Codec: Realtek ALC3861 
[*]GPU: AMD Radeon RX 580 8G 
[/LIST]

No proprietary drivers are available for any of my components and aside from the headphone issue, I don't have any problem with any of my other components (games run great, Wi-Fi and Bluetooth work as I was expecting, etc.).

Also, whenever I try to apply a setting in **HDAJackRetask**, I keep getting an error saying "tee: /sys/class/sound/hwC1D0/reconfig: Device or resource busy".

Lastly, I've tried resetting **alsamixer**, but with no success.


If anyone has any clues as to what's the cause of the problem, feel free to let me know! Thanks in advance! :)

---

### Post by TheFu on 2021-11-14
Try
```
$ pacmd load-module module-switch-on-connect
```

Then unplug and replug the headphones.

---

### Post by cafebagels08 on 2021-11-14
Thanks for your answer, it's really appreciated!

I tried activating it, but it didn't change anything unfortunately. :neutral: I even tried rebooting to see if it would do something, but it's still the same. After trying, I reverted back to my default config and I found that it was actually already activated by default. Here is the list of the modules that I have installed:

```
$ pactl list modules short

0    module-device-restore        
1    module-stream-restore        
2    module-card-restore        
3    module-augment-properties        
4    module-switch-on-port-available        
5    module-switch-on-connect        
6    module-udev-detect        
7    module-bluetooth-policy        
8    module-bluetooth-discover        
9    module-bluez5-discover        
10    module-native-protocol-unix        
11    module-default-device-restore        
12    module-always-sink        
14    module-intended-roles        
15    module-suspend-on-idle        
16    module-systemd-login        
17    module-position-event-sounds        
18    module-role-cork        
19    module-snap-policy        
20    module-filter-heuristics        
21    module-filter-apply        
22    module-alsa-card    device_id="0" name="pci-0000_09_00.1" card_name="alsa_card.pci-0000_09_00.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1"    
23    module-alsa-card    device_id="1" name="pci-0000_0b_00.3" card_name="alsa_card.pci-0000_0b_00.3" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1"
```

If you have any clues as to what could be the issue, feel free to let me know! :)

Thanks again!

---

