---
title: "HDMI TV output"
date: 2011-11-13
forum: Hardware
---

### Post by smidge on 2011-11-13
I have a HP laptop with intel integrated graphics. I've recently switched to ubuntu from windows and love it but whenever i attempt to connect to my tv via hdmi i get two separate issues.

1. sound doesn't come through the HDMI and instead continues to play through the laptop, in fact the HDMI output does not even appear in the sound settings.

2. although the display works fine as the secondary monitor when i turn off the laptop screen in the settings the TV displays "incompatible signal" even though the output is set to 1080p.

I am running ubuntu 11.10

---

### Post by BillyBoa on 2011-11-13
Looks like your problem has to do with the video drivers.

Did you try to install the proprietary drivers?

---

### Post by smidge on 2011-11-13
No, like i said i am new to ubuntu. I haven't tried adding drivers... I don't even know how.

---

### Post by BillyBoa on 2011-11-13
Go to upper left corner the Dash push it and on the search string right "jockey".

It appears the icon of additional drivers. Push it and follow the instructions. 

If you use ATI drivers, you have 2 selections, so choose the option without post release updates, cause it's not working. 

If you use NVIDIA just choose on option.

Then restart the computer to take effect and check your options in Sound Settings to see if HDMI is appeared.

---

### Post by SeijiSensei on 2011-11-13
> **smidge said:**
> 1. sound doesn't come through the HDMI and instead continues to play through the laptop, in fact the HDMI output does not even appear in the sound settings.

HDMI connections on computers rarely include the audio channel.  Some third-party add-on cards provide this, but they're designed for desktop machines.  If the computer has an optical (SP/DIF) jack, you can try using that.  Otherwise you can run an adapter cable from the headphone jack to the TV (mini headphone to RCA plugs), but you'll still be getting analog audio.

@BillyBoa
He has Intel integrated graphics, not an ATI or NVIDIA adapter.

---

### Post by smidge on 2011-11-13
I dont have a graphics card but the intel 1000 intergrated graphics. Also the HDMI port carries sound and video just fine in windows, even with the laptop screen off. Also I hated Unity and have GNOME now, if that helps.

Also Jockey shows that no proprietary drivers are in use on my computer.

---

### Post by BillyBoa on 2011-11-13
> **smidge said:**
> I dont have a graphics card but the intel 1000 intergrated graphics. Also the HDMI port carries sound and video just fine in windows, even with the laptop screen off. Also I hated Unity and have GNOME now, if that helps.

Also Jockey shows that no proprietary drivers are in use on my computer.

In that case look here but I think there is no solution to your problem.

[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

---

### Post by smidge on 2011-11-13
The wiki includes a link 

[http://lists.freedesktop.org/archives/xorg/2008-November/040034.html](http://lists.freedesktop.org/archives/xorg/2008-November/040034.html) 

to patch sound through HDMI on intel chipsets but i have no idea how to patch this. anyone got a clue?

---

