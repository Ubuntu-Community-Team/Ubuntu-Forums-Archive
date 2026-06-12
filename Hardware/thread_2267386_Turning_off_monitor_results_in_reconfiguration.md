---
title: "Turning off monitor results in reconfiguration"
date: 2015-03-01
forum: Hardware
---

### Post by christophe-detroyer on 2015-03-01
Hi,

I've recently purchased a Radeon R9 280x along with a [Samsung 4K monitor]("http://www.samsung.com/us/computer/monitors/LU28D590DS/ZA"). The monitor is connected to the Radeon via DisplayPort 1.2. One of my older monitors, a Iiyama E2210HDS is connected to the AMD card using DVI connection. As for drivers I have followed this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD). The operating system itself is Xubuntu 14.10.

One problem I've been experiencing is that when I turn off the 4K monitor (pressing its powerbutton) Ubuntu removes the monitor completely. It reconfigures itself automatically such that my Iiyama monitor becomes the only connected monitor. The procedure I have to go through then is a rather painstaking process. Configre the monitor. Sometimes it remains black, sometimes it shows output. If it remains black I have to wait for the countdown timer ("keep these settings?") to revert the settings. Sometimes it makes my secondary monitor black and I have to reset. Bottom line, it's annoying me to death. However, I have zero ideas on how to go and fix this?

Any help figuring this out is greatly appreciated!

Edit

This is my [xorg.conf]("http://paste.ubuntu.com/10484919/") file, if that were of any help

---

### Post by gifford on 2015-03-01
Have you tried switching the Samsung to using the DVI connection?

---

### Post by kerry_s on 2015-03-01
did you go in to display & use the detect button ?

---

### Post by christophe-detroyer on 2015-03-02
> **gifford said:**
> Have you tried switching the Samsung to using the DVI connection?

That wouldn't help much since displayport 1.2 is the only connection that supports 4K resolutions. I could try HDMI (which the monitor has) just to see if it shows the same behaviour though. I will do that!

> **kerry_s said:**
> did you go in to display & use the detect button ?

It does detect the display. I'm not home atm so I can't take a screenshot but when I go to display settings, you can see both monitors on their right position (where you can drag them next to eachother, on top of eachother etc), but the 4K monitor is shown in black. So it seems like all I have to do do i re-check "use this output". When I do that the monitor comes back, but both displays are shown as "mirror displays", so I can't drag them anymore, they are one big blue block and the iiyama display is showing a part of the 4K displays output. (actually sort of mirrored indeed). The checkbox "mirror displays" is unchekced though.. When I want to put them next to eachother again I have to check the box "mirror displays", wait for the configuration box "use these settings" to revert back to the old settings. If that works the display is configured again. But, most of the time it just remains black and I have to reset my machine.

---

### Post by christophe-detroyer on 2015-05-07
In the meanwhile I gave HDMI a shot. Using the HDMI port on the 4k display works as expected. The displays both go into sleep mode because they lose signal and when I move my mouse they both wake up instantly.  So I think its safe to say that the problem is the GPU and displayport.

HDMI not a permanent fix because it seems to only support 30hz frequency on 4k resolutions.

---

