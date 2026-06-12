---
title: "nVidia prime - can't run external monitor on Asus Zenbook"
date: 2016-07-27
forum: Hardware
---

### Post by dibo on 2016-07-27
Hi,

I bought a new ASUS Zenbook UX501VW with Intel card + Nvidia Geforce 960M. First what I did after installation was set grub option to **nouveau.modeset=0** because fans were really loud. I guess that this turn off my nvidia card. Then plugged external monitor via HDMI. Everything worked perfect, could do whatever want in KDE display settings, both screens, only one etc. So I'm pretty sure that HDMI port is connected to the Intel card.

Then installed latest nvidia drivers (nvidia-367), nvidia-prime and nvidia-settings. Changed grub options (recommended for optimus) to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1"
```

Here are my experiences with external monitor on nvidia-prime profiles:

**Intel**

[LIST]
[*]nvidia-settings doesn't show anything about secondary display. Infact, settings on this profile are really poor
[*]in KDE display settings I see my secondary monitor but when try select it for change "enabled" checkbox then it becomes unselected after 2 seconds. Even if I try do this really fast and accept, then I get message that it could not be enabled because resolution is too big or my driver doesn't allow more than one active display
[*]in KDE display settings, don't see external monitor in "main display" popup list. A bit regression between what is "visually" presented
[/LIST]
**nVidia**

[LIST]
[*]nvidia-seetings show only *Screen 0* section. That kind of screen configuration is missing on Intel profile for me
[*]KDE settings doesn't show anything about secondary display at all
[/LIST]
**Notes**

[LIST]
[*]secondary monitor is running on login screen but turn off after login in
[*]everytime when external monitor show "no signal", interface on laptop display is frozen for a half second or less (including mouse cursor). Looks like monitor ping interrupt X server
[*]when external monitor is connected then kworker/N (N=CPU core) has abnormal CPU usage (~5-10%)
[/LIST]
**System**
Kubuntu 16.04 64bit, updated


Don't suggest me to try bumbelebee. Already did and doesn't work at all. I used it 4 years ago on my Dell XPS and worked perfect but seems that it is not developed anymore, especially for ASUS support. That brings me sad thoughts, after 4 years nothing changed in optimus support. This is not novelty technology :(

---

