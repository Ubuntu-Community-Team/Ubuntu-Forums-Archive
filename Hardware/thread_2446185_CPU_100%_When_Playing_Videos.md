---
title: "CPU 100% When Playing Videos"
date: 2020-06-25
forum: Hardware
---

### Post by garotobossanova on 2020-06-25
The CPUs go to up to 100% usage when playing video on youtube, or opening 4 tabs with no videos, and when playing videos on de HD too... Can it be caused by software problems, or by the old thermal paste, or both? Otherwise can it be caused by a problem in the NVIDIA GeForce GT 640 drive or hardware?

OS: Ubuntu 20.04 LTS x86_64 
Host: P5K Deluxe 
Kernel: 5.4.0-37-generic 
Uptime: 3 hours, 48 mins 
Packages: 1812 (dpkg), 17 (snap) 
Shell: bash 5.0.16 
Resolution: 1680x1050 
DE: GNOME 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel Core 2 6600 (2) @ 2.394GHz 
GPU: NVIDIA GeForce GT 640 
Memory: 2148MiB / 7961MiB 


 [IMG][[IMG]https://i.postimg.cc/F1VpxFdM/Captura-de-tela-de-2020-06-25-23-08-35.png[/IMG]]("https://postimg.cc/F1VpxFdM")  [[IMG]https://i.postimg.cc/pmpBxDGv/Captura-de-tela-de-2020-06-25-23-12-55.png[/IMG]]("https://postimg.cc/pmpBxDGv")  [[IMG]https://i.postimg.cc/Wh97Q97S/Captura-de-tela-de-2020-06-25-23-13-48.png[/IMG]]("https://postimg.cc/Wh97Q97S")  [[IMG]https://i.postimg.cc/mtZwpx7t/Captura-de-tela-de-2020-06-25-23-15-18.png[/IMG]]("https://postimg.cc/mtZwpx7t")[/IMG]

---

### Post by CelticWarrior on 2020-06-26
Welcome.

Please open Additional Drivers and select and apply the recommended Nvidia proprietary drivers.

---

### Post by Autodave on 2020-06-26
Also, install the ad blocker called "uBlock".

---

### Post by garotobossanova on 2020-06-26
> **CelticWarrior said:**
> Welcome.

Please open Additional Drivers and select and apply the recommended Nvidia proprietary drivers.

It is with the recommended proprietary Nvidia driver already.
[ [IMG]https://postimg.cc/NLs3Bcbt[/IMG]]("https://treetop100babynames.com/")

---

### Post by garotobossanova on 2020-06-26
> **Autodave said:**
> Also, install the ad blocker called "uBlock".

The problem happens with the web browser closed too...

---

### Post by CelticWarrior on 2020-06-26
> **garotobossanova said:**
> It is with the recommended proprietary Nvidia driver already.
[ [IMG]https://postimg.cc/NLs3Bcbt[/IMG]]("https://treetop100babynames.com/")

So which driver version are you using? And is it loaded? (Hint: If Sec ure Boot is enabled in UEFI then it isn't).

---

### Post by Yellow Pasque on 2020-06-26
Youtube uses VP9 by default, which may be a bit demanding for your system. You should try the "h264ify" extension: [https://addons.mozilla.org/en-US/firefox/addon/h264ify/?src=search](https://addons.mozilla.org/en-US/firefox/addon/h264ify/?src=search)

Also, Firefox only supports GPU video decode acceleration in a Wayland session: [https://www.phoronix.com/scan.php?page=news_item&px=Firefox-76-VA-API-Formats](https://www.phoronix.com/scan.php?page=news_item&px=Firefox-76-VA-API-Formats)
And you would need "vdpau-va-driver" package if you want to try that. And you would still need h264ify because GT640 cannot accelerate VP9.

> The problem happens with the web browser closed too... 

What video player and output are you using? Try this:
```
sudo apt-get install mpv vdpauinfo
vdpauinfo | grep string    #This command should return "Information string: NVIDIA VDPAU Driver Shared Library 440.xx"
mpv --vo=gpu --hwdec=vdpau  filename
```

---

### Post by Shibblet on 2020-06-26
The browsers (Firefox, Chrome, Brave, etc.) do not have hardware decoding built in.  There is a chromium branch that does, but it's still in testing.

If you don't mind watching the video at 720p, you can copy the YouTube link directly into VLC, and it will use hardware decoding to play it back.

---

