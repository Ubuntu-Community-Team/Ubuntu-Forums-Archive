---
title: "Lenovo IdeaPad 340 Issues"
date: 2023-07-04
forum: Hardware
---

### Post by hardcopy2 on 2023-07-04
Hello,

I’ve only been using ubuntu for a couple months but my laptop freezes during media playback, and has usb connection issues.

Hoping to get some help on determining if I’m missing certain drivers, or if I have faulty hardware on my ideapad.


Specs:


[LIST]
[*]MD Ryzen 5 3500U (Quad Core/ up to 3.7GHz, 2MB L2 / 4MB L3) Processor, 2.1 GHz frequency 
[*] 8GB DDR4 RAM, 256GB SSD storage (2.5" SATA 6Gb/s ); Integrated AMD Radeon Vega 8 Graphics 
[*] WiFi 802.11ac 1x1 Wi-Fi + Bluetooth 4.2; Webcam; 2x USB 3.1 Gen 1; 1x USB-C 3.1 Gen 1; 1x HDMI 1.4b; 1x Ethernet (RJ-45) 
[/LIST]


When it freezes the audio continues but everything else is locked. After a few minutes the audio cuts off as well. I’ve tried ffmpeg conversions of video files. It happens almost asap on a usb drive. It happens with vlc player most often. with the default media player it will give me an error saying it can't open the file, even though the file is viewable.

Also noticed on reboot before OS launch I see 
```
0.863946] integrity: Problem loading X.509 certificate
dev/sda2: recovering journal , dev/sda2: Clearing orphaned inode 3158678 (uid=1000, gid=10(…)
```


never done diagnostics on a linux machine so I’m not sure how to proceed.

Thanks in advance.

---

### Post by Rubi1200 on 2023-07-09
Hi and welcome to the forums :-)

Please run the system info script in my signature and post the results here. It will gather hardware and system information that will help us diagnose the situation.

As for the errors at boot time:

```
[COLOR=#000000][FONT=&quot]integrity: Problem loading X.509 certificate[/FONT][/COLOR]
```

Is this a dual-boot system with Windows?

```
[COLOR=#000000][FONT=&quot]dev/sda2: recovering journal , dev/sda2: Clearing orphaned inode 3158678 (uid=1000, gid=10(…)[/FONT][/COLOR]
```

recovering journal errors are often associated with hard shutdowns. But before suggesting using something like fsck to check the integrity of the filesystem I would prefer to see the results of the script.
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

