---
title: "Radeon HD 7730M GPU driver not working on XUbuntu 16.04"
date: 2018-05-03
forum: Hardware
---

### Post by Richard_Nai on 2018-05-03
[COLOR=#111111][FONT=Ubuntu]So I moved my harddrive from one laptop that had an NVIDIA graphics card to another one that has a Radeon HD 7730M graphics card. I deleted my NVIDIA drivers and used the default drivers as the NVIDIA drivers caused issues, but a game that used to run decently now runs sluggishly, and I'm trying to get drivers for my Radeon graphics card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I went to here: [https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx) and downloaded the Radeon™ Software for Linux® version 18.10 for Ubuntu 16.04.4, and installed them. I then ran[/FONT][/COLOR]
```
sudo apt-get install xserver-xorg-video-amdgpu
```

and

```
sudo apt-get install firmware-amd-graphics
```

[COLOR=#111111][FONT=Ubuntu]Except it still doesn't work.

[/FONT][/COLOR]```
seedship@destiny:~$ inxi -G
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           Card-2: Advanced Micro Devices [AMD/ATI] Chelsea LP [Radeon HD 7730M]
           Display Server: X.Org 1.18.4 driver: FAILED: amdgpu
           Resolution: 1920x1080@60.02hz
           GLX Renderer: N/A GLX Version: N/A



```

---

