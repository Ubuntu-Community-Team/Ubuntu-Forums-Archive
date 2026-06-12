---
title: "External Monitor Problems Ubuntu 10.04 and 10.10"
date: 2010-09-24
forum: Hardware
---

### Post by Aztek on 2010-09-24
Hi,

I'm running Ubuntu 10.10 beta (though I also ran into problems with 10.04) on

Sony Vaio VGN-N365E ([www.docs.sony.com/release/specs/VGNN365EB_mksp.pdf](www.docs.sony.com/release/specs/VGNN365EB_mksp.pdf))

(Intel 945GM graphics)

With a 27 inch Asus VE276Q 1920x1080 

external monitor hooked up via VGA. When configuring dual-screens it won't behave properly, even trying different settings. I've tried different combinations of having the laptop to the left or the right of the monitor, and above and below, and with different resolutions. Each time they behave differently, but never correctly. Sometimes it will only display on a portion of the screen. Sometimes the image will be stretched partially on one screen and partially on the other, and sometimes one or the other be be blank, etc. The fact that the monitor configuration tool included in Ubuntu these days is so simplistic gives me limited options of trying different things.

So, 2 questions:

1) Does anyone have any suggestions?

2) Are there any more advanced monitor configuration tools that I could download that will let me fiddle around more?

Much appreciated,
Aztek

---

### Post by Aztek on 2010-09-26
Bump.

Does anyone at least know of a tool I can use to get more configuration options to play with for the monitors/resolutions?

---

### Post by mwildam on 2010-09-27
[http://it-tactics.blogspot.com/2010/08/ubuntu-1004-with-docking-station.html](http://it-tactics.blogspot.com/2010/08/ubuntu-1004-with-docking-station.html)

arandr is a tool you can use to change monitor settings.
or
xrandr to do it via commandline.

---

### Post by Aztek on 2010-10-15
Thank you for your reply. I tried arandr and it wouldn't work. The built-in ubuntu configurator works better. I'm still having problems in 10.10. It started working fine in 10.04. The only configuration that seems to display both monitors at the correct resolutions is to tell it that the laptop screen is positioned beneath the external monitor. Obviously this isn't ideal for usage. What would have changed between 10.04 and 10.10 that would hose this?

One thing I noticed is that visual effects didn't used to work in 10.04, but now they do. Could it be that 10.10 is recognizing the graphics chip more correctly but in the process broke something else?

Any ideas?

---

### Post by huzzak on 2010-10-16
Hello!

I think your problem may be related to [mine]("http://ubuntuforums.org/showthread.php?t=1595620").  I've posted more information [here]("http://ubuntuforums.org/showthread.php?p=9980414#post9980414") as well.

I think we need to figure out how to resize the virtual space on which the monitors are overlain.  Any ideas on how to do that?

---

### Post by huzzak on 2010-10-20
If you are indeed having the same problem as me, salvation is nigh!  [Click here!]("http://ubuntuforums.org/showthread.php?t=1595620")

---

### Post by Aztek on 2010-10-22
I could kiss you right now. This has been driving me nuts but is now fixed. One more question: Is there a way to update just the libdrm package? I toyed with the idea of using the force version feature in the package menu but decided against it since I didn't know what it might do. I ended up just doing all of the available proposed updates. Was this a bad idea?

---

### Post by huzzak on 2010-10-22
I don't think it is an awful idea since, as I understand it, the proposed are set to become regular updates.

I went into Synaptic and enabled the proposed repository and then only selected the libdrm packages to be upgraded and then disabled the proposed repository after they had been upgraded.  I'm not sure about undoing the changes, but I would guess that you should be fine.  You might want to disable the proposed repository now though, just to be a little bit safer!

---

