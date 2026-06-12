---
title: "[Rpi4] [ARM64] vc4-kms-v3d-pi4 causes hdmi reset when mousepointer is over a video"
date: 2020-09-27
forum: Hardware
---

### Post by m-fasel on 2020-09-27
Hi there,

since i installed Ubuntu 20.04 with the latest kernel "vc4-kms-v3d-pi4" causes a blackscreen/hdmi reset everytime i move the mousecursor over a videoframe.

> [Timestamp] vc4_hdmi fef05700.hdmi: ASoC: can't open interface fef05700.hdmi: -19
[Timestamp] vc4_hdmi fef05700.hdmi: ASoC: can't open interface fef05700.hdmi: -19
[Timestamp] vc4_hdmi fef05700.hdmi: ASoC: can't open interface fef05700.hdmi: -19

This comes everytime the Blackscreen/Hdmi reset appears. The Usercfg.txt looks like that, but is also tried this in config.txt.
```
max_framebuffers=2
arm_64bit=1
gpu_mem=128
dtoverlay=vc4-kms-v3d-pi4, cma-128
disable_overscan=1
hdmi_enable_4kp60=1
dtparam=audio=on
boot_delay
kernel=vmlinux
initramfs initrd.img followkernel 
```

I also tried the beta version odf RPI OS and had the same problem. I saw that one or two other ppl in the Raspi-Forums had the same issue but no soloution, so i decided to make another Thread for that.

I had an old installation on an usb-stick without this issue. The "vc4-kms-v3d-pi4"-Driver worked like hell and Youtube and VLC had max famerated output without lags or issues. But i accidently deleted this OS. I noticed that my HMDI connetor looks a little bit strange so i am not sure if the connector causes this. But i removed the "pi4" option and i didn't get any error. But without, the video output is very slow and i got a laggy framerate on both Ubuntu and RPI OS.


I had an old installation on an usb-stick without this issue. The "vc4-kms-v3d-pi4"-Driver worked like hell and Youtube and VLC had max famerated output without lags or issues. But i accidently deleted this OS. I noticed that my HMDI connetor looks a little bit strange so i am not sure if the connector causes this. But i removed the "pi4" option and i didn't get any error. But without, the video output is very slow and i got a laggy framerate on both Ubuntu and RPI OS.

Is it possible that this issue comes from a new firmware update?

Hope someone could help, because on my old USB-Stick Ubuntu with "vc4-kms-v3d-pi4" worked so good, thats i did not use my Desktop-PC for a week. :) OpenGL worked good, video-output in both VLC and Firefox/Youtube went like clockwork... So you can uinderstand why i wish it back

Thanks and regards,
Marc.

---

