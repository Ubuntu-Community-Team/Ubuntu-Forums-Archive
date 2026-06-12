---
title: "Ubuntu mate 22.04: external monitor problem"
date: 2023-11-12
forum: Hardware
---

### Post by alfredino on 2023-11-12
[COLOR=#333333][FONT=-apple-system]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=-apple-system]I have a problem since yesterday. I put my laptop on standby and when I rebooted it was stuck. So I turned it off and after rebooting it can't see the external monitor (I've already tried with different cables, monitors and laptops and everything works fine).
I am using linux 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC. I tried both the open source nouveau driver and the proprietary nvidia 535 driver (my video card is geforce 720m).
[/FONT][/COLOR]
```
inxi -G
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel
  Device-2: NVIDIA GF117M [GeForce 610M/710M/810M/820M / GT
  620M/625M/630M/720M]
    driver: nouveau v: kernel
  Device-3: IMC Networks USB2.0 UVC HD Webcam type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1366x768~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 4000 (IVB GT2)
    v: 4.2 Mesa 23.0.4-0ubuntu1~22.04.1
echo $XDG_SESSION_TYPE
x11

```[COLOR=#333333][FONT=-apple-system]I cannot show the journalctl output as it tells me it is empty even though the /var/log/journal folder is populated.[/FONT][/COLOR]
[COLOR=#333333][FONT=-apple-system]Do you have any ideas?[/FONT][/COLOR]
[COLOR=#333333][FONT=-apple-system]Thanks[/FONT][/COLOR]

---

