---
title: "Ubuntu 14.04 on Clevo P157SM w/ GeForce 780M multi-monitor issues."
date: 2014-07-02
forum: Hardware
---

### Post by macrosblackd on 2014-07-02
I've been having a lot of trouble with Ubuntu on my laptop with regards to multiple external monitors. This issue has prompted me to reinstall more than once as well as uninstall/purging nvidia drivers and reinstallng those even more times. I'm currently using the Nouveau driver, since that seems to be slightly more stable.


Some background information:
I use my laptop at work and at home, with the following configurations:
(Work) 2 External Monitors (1 on HDMI, the other on Display Port), Built-in disabled, lid closed.
(Home) Just the built-in


The issue:
Initially after a reinstall/configuration the Work configuration works just fine, even after reboots. However, after some time & switching between the configurations, the work configuration stops working correctly without a huge amount of fighting. The built-in display wont turn off / disable even when the lid is closed. I have to open the lid, adjust the monitors in settings and pray that closing the lid doesn't reset everything again (which it has done before). This has caused many hours of lost productivity and frustration. I've been scouring the internet (ubuntuforums.org, askubuntu.com, etc) for solutions, but nothing I do seems to work.


What I've tried:
I've tried using autorandr with both configurations saved, this seems to have worked for a bit, but doesn't work any more.
I've messed around with various xrandr settings.
I've looked at various configuration files that people have mentioned.


Terminal Stuff:
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 780M] (rev a1)

```


Note on this one: xrandr seems to read the DP port as HDMI3. The cable is a DVI<>DP.
```

$ xrandr | grep connected -w
eDP1 connected (normal left inverted right x axis y axis)
HDMI2 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 291mm
HDMI3 connected 1440x900+1920+99 (normal left inverted right x axis y axis) 408mm x 255mm

```


```

$ disper -l
display eDP1: eDP1
 resolutions: 640x480, 800x600, 1024x768, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1024, 1680x1050, 1920x1080
display HDMI3: HDMI3
 resolutions: 720x400, 640x480, 800x600, 832x624, 1024x768, 1280x720, 1152x864, 1280x1024, 1440x900
display HDMI2: HDMI2
 resolutions: 720x400, 640x480, 720x480, 720x576, 800x600, 1440x480, 1024x768, 1440x576, 1280x720, 1152x864, 1440x900, 1280x1024, 1680x1050, 1920x1080, 1920x1200

```

---

