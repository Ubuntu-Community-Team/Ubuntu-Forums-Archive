---
title: "Ubuntu 24.04 Sound not working"
date: 2024-12-07
forum: Hardware
---

### Post by axero on 2024-12-07
I've been using Ubuntu 18.04 for a long time and I had no issues with the audio on that distro. What I'm using is PulseAudio (I suspect) together with PulseEffects that allows me adjust the frequencies with the equalizer. With that I'm using an external USB device from which I listen to the sound. The USB device has a tendency to power off when no sound is going through it but that is not a problem because I can power it back up and continue using it. The only problem I had was that if I wanted to listen to audio through the HDMI on the major screen, that output tended to eventually break down and I had to enter "pulseaudio -k" to fix it but I'm rarely interested in using the speakers on the monitor anyway so it wasn't a big deal.

Yesterday, I decided to upgrade all the way to 24.4 and now I start to have pretty serious issues. If I boot up the system with the USB audio device, everything works fine and I can launch PulseEffects and use as before. However, once it powers off I will not be able to use it again until I reboot and pretty much everything in the audio stack seems to be broken. By broken I mean that the mixers cannot see the device and sometimes they do but I get some distorted sound from the device. I cannot run alsamixer with the error "cannot open mixer: No such file or directory" and pulseaudio -k returns "E: [pulseaudio] main.c: Failed to kill daemon: No such process"...

There used to be a list of all hardware devices under "Sound" in the graphical settings where you could drag and drop the hardware represented as icons to set the priority of the devices under audio playback. There no longer is such a thing in Ubunti 24.4, where did it go?

When running inxi -FAxz I get this for the audio:

```
[FONT=monospace][COLOR=#5454FF]**S**[/COLOR][/FONT][FONT=monospace][COLOR=#5454FF]**ystem:**[/COLOR]
  [COLOR=#5454FF]**Kernel:**[/COLOR][COLOR=#000000] 6.8.0-49-generic [/COLOR][COLOR=#5454FF]**arch:**[/COLOR][COLOR=#000000] x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**compiler:**[/COLOR][COLOR=#000000] gcc [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 13.2.0[/COLOR]
  [COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 5.27.11 [/COLOR][COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#000000] Kubuntu 24.04.1 LTS (Noble Numbat)[/COLOR]
    [COLOR=#5454FF]**base:**[/COLOR][COLOR=#000000] Ubuntu[/COLOR]

[/FONT][FONT=monospace][COLOR=#5454FF]**Graphics:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Intel UHD Graphics 620 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel[/COLOR]
    [COLOR=#5454FF]**arch:**[/COLOR][COLOR=#000000] Gen-9.5 [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#000000] 00:02.0[/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Realtek Integrated_Webcam_HD [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] uvcvideo [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB[/COLOR]
    [COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#000000] 1-5:3[/COLOR]
  [COLOR=#5454FF]**Display:**[/COLOR][COLOR=#000000] wayland [/COLOR][COLOR=#5454FF]**server:**[/COLOR][COLOR=#000000] X.org [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.21.1.11 [/COLOR][COLOR=#5454FF]**with:**[/COLOR][COLOR=#000000] Xwayland [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 23.2.6[/COLOR]
    [COLOR=#5454FF]**compositor:**[/COLOR][COLOR=#000000] kwin_wayland [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#5454FF]**X:**[/COLOR][COLOR=#5454FF]**loaded:**[/COLOR][COLOR=#000000] modesetting [/COLOR][COLOR=#5454FF]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa[/COLOR]
    [COLOR=#5454FF]**dri:**[/COLOR][COLOR=#000000] iris [/COLOR][COLOR=#5454FF]**gpu:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454FF]**resolution:**[/COLOR][COLOR=#5454FF]**1:**[/COLOR][COLOR=#000000] 1920x1080 [/COLOR][COLOR=#5454FF]**2:**[/COLOR][COLOR=#000000] 1920x1080[/COLOR]
  [COLOR=#5454FF]**API:**[/COLOR][COLOR=#000000] EGL [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.5 [/COLOR][COLOR=#5454FF]**drivers:**[/COLOR][COLOR=#000000] iris,swrast [/COLOR][COLOR=#5454FF]**platforms:**[/COLOR]
    [COLOR=#5454FF]**active:**[/COLOR][COLOR=#000000] wayland,x11,surfaceless,device [/COLOR][COLOR=#5454FF]**inactive:**[/COLOR][COLOR=#000000] gbm[/COLOR]
  [COLOR=#5454FF]**API:**[/COLOR][COLOR=#000000] OpenGL [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 4.6 [/COLOR][COLOR=#5454FF]**compat-v:**[/COLOR][COLOR=#000000] 4.5 [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] intel mesa [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 24.0.9-0ubuntu0.2[/COLOR]
    [COLOR=#5454FF]**glx-v:**[/COLOR][COLOR=#000000] 1.4 [/COLOR][COLOR=#5454FF]**direct-render:**[/COLOR][COLOR=#000000] yes [/COLOR][COLOR=#5454FF]**renderer:**[/COLOR][COLOR=#000000] Mesa Intel UHD Graphics 620 (KBL[/COLOR]
    GT2)
  [COLOR=#5454FF]**API:**[/COLOR][COLOR=#000000] Vulkan [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.3.275 [/COLOR][COLOR=#5454FF]**drivers:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**surfaces:**[/COLOR][COLOR=#000000] xcb,xlib,wayland [/COLOR][COLOR=#5454FF]**devices:**[/COLOR][COLOR=#000000] 2[/COLOR]
[COLOR=#5454FF]**Audio:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Intel Sunrise Point-LP HD Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel[/COLOR]
    [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#000000] 00:1f.3[/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] FiiO Q5 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd-usb-audio [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#000000] 3-1:4[/COLOR]
  [COLOR=#5454FF]**API:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] k6.8.0-49-generic [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#000000] kernel-api[/COLOR]
  [COLOR=#5454FF]**Server-1:**[/COLOR][COLOR=#000000] PipeWire [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.0.5 [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#000000] active[/COLOR]
  [COLOR=#5454FF]**Server-2:**[/COLOR][COLOR=#000000] PulseAudio [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 16.1 [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#000000] off (using pipewire-pulse)[/COLOR]
[/FONT]
```

This is after I powered the USB device back on and not being able to use it anymore. The output indicates that the hardware is there (FiiO Q5) and there is a driver for it (snd-usb-audio). So what do I do? This must be a bug or something. It seems that the audio stack is broken once again and that essential software to manage multiple audio devices as they come and go is missing.

Edit it seems that the sound stack has been replaced with pipewire. I looked into these instructions here:

[https://www.baeldung.com/linux/pulseaudio-pipewire-replace](https://www.baeldung.com/linux/pulseaudio-pipewire-replace)

but it seems to be broken. I get this when running `systemctl status --user pipewire`:

```

[FONT=monospace][COLOR=#54FF54]**&#9679;**[/COLOR][COLOR=#000000] pipewire.service - PipeWire Multimedia Service[/COLOR]
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; [COLOR=#54FF54]**enabled**[/COLOR][COLOR=#000000]; preset: [/COLOR][COLOR=#54FF54]**enabled**[/COLOR][COLOR=#000000])[/COLOR]
     Active: [COLOR=#54FF54]**active (running)**[/COLOR][COLOR=#000000] since Sat 2024-12-07 23:56:43 MSK; 3h 25min ago[/COLOR]
TriggeredBy: [COLOR=#54FF54]**&#9679;**[/COLOR][COLOR=#000000] pipewire.socket[/COLOR]
   Main PID: 1693 (pipewire)
      Tasks: 3 (limit: 18761)
     Memory: 24.9M (peak: 25.9M)
        CPU: 2min 59.059s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;[COLOR=#8A8A8A]1693 /usr/bin/pipewire[/COLOR]

dec 07 23:56:43 pod systemd[1678]: Started pipewire.service - PipeWire Multimedia Service.
dec 07 23:56:43 pod pipewire[1693]: [COLOR=#D7D75F]**mod.jackdbus-detect: Failed to receive jackdbus reply: org.freedesktop.DBus.Error.ServiceUnknown: **[/COLOR][COLOR=#ffffff]>[/COLOR]
dec 08 00:03:51 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432e65ed10: unknown peer 0x5a432e6380a0 fd:69**[/COLOR]
dec 08 00:03:52 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432e6382d0: unknown peer 0x5a432e5c9850 fd:128**[/COLOR]
dec 08 02:35:12 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432f2f1b60: unknown peer 0x5a432e314180 fd:55**[/COLOR]
dec 08 03:16:12 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432e68a2a0: unknown peer 0x5a432e4bac10 fd:55**[/COLOR]
dec 08 03:16:13 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432e68a2a0: unknown peer 0x5a432f2f9550 fd:55**[/COLOR]
dec 08 03:16:14 pod pipewire[1693]: [COLOR=#D7D75F]**mod.client-node: 0x5a432f4d4c10: unknown peer 0x5a432e2f4a40 fd:106**[/COLOR]
[/FONT]
```

and this is for wireplumber

```

[FONT=monospace][COLOR=#54FF54]**&#9679;**[/COLOR][COLOR=#000000] wireplumber.service - Multimedia Service Session Manager[/COLOR]
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; [COLOR=#54FF54]**enabled**[/COLOR][COLOR=#000000]; preset: [/COLOR][COLOR=#54FF54]**enabled**[/COLOR][COLOR=#000000])[/COLOR]
     Active: [COLOR=#54FF54]**active (running)**[/COLOR][COLOR=#000000] since Sat 2024-12-07 23:56:43 MSK; 3h 28min ago[/COLOR]
   Main PID: 1696 (wireplumber)
      Tasks: 6 (limit: 18761)
     Memory: 6.0M (peak: 9.4M)
        CPU: 4.404s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;[COLOR=#8A8A8A]1696 /usr/bin/wireplumber[/COLOR]

dec 07 23:56:43 pod systemd[1678]: Started wireplumber.service - Multimedia Service Session Manager.
dec 07 23:56:43 pod wireplumber[1696]: [COLOR=#000000]**SPA handle 'api.libcamera.enum.manager' could not be loaded; is it installed?**[/COLOR]
dec 07 23:56:43 pod wireplumber[1696]: [COLOR=#000000]**PipeWire's libcamera SPA missing or broken. libcamera not supported.**[/COLOR]
dec 08 02:52:25 pod wireplumber[1696]: [COLOR=#000000]**<WpSiStandardLink:0x5b482a494350> si-standard-link: in/out items are not valid anymore**[/COLOR]
dec 08 03:24:54 pod wireplumber[1696]: [COLOR=#000000]**<WpSiNode:0x5b482a6fbb60> Object activation aborted: proxy destroyed**[/COLOR]
dec 08 03:24:54 pod wireplumber[1696]: [COLOR=#000000]**<WpSiNode:0x5b482a6fbb60> failed to activate item: Object activation aborted: proxy destroyed**[/COLOR]
[/FONT]
```

Edit 2:
I rebooted the system and got it all working again with the effects of installing pipewire and purging pulseaudio. Pulse effects was now gone but I was offered Easy Effects to replace it. I tried turning off and on the USB audio device and it seems to be fine now. It seems to be robust under the new installation for now. The error messages from systemctl are the same also when it is working so I doubt they would be useful in a troubleshooting scenario.

---

### Post by axero on 2024-12-07
After some more extensive testing, the problem with the external USB audio device persists. Pipewire fails to get it back into the audio stack after the device have been restored from sleep/power off state. Running the command

[COLOR=#F2F2F2][FONT=&amp]systemctl --user restart pipewire pipewire-pulse wireplumber

[/FONT][/COLOR]fixes the issue temporarily

---

