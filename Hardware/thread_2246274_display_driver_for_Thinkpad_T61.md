---
title: "display driver for Thinkpad T61"
date: 2014-09-29
forum: Hardware
---

### Post by Ron_Callison on 2014-09-29
I just read an old article concerning installing Ubuntu on a Thinkpad T61 concerning the display driver that stated:  **"...running at 1680×1050. I wondered what driver it was using. In other words, was it the Intel driver or the generic Vesa driver."  **Somewhere in the system he found that the driver was:**  "[COLOR=#666666][FONT=Lucida Grande]The driver listed as being used was labeled as “intel – Experimental”.[/FONT][/COLOR]**  

I ran inxi on my T61 and got the following info: ** "Graphics:  Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary) bus-ID: 00:02.0     X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1280x800@60.2hz      ****GLX Renderer: Mesa DRI Intel 965GM GLX Version: 2.1 Mesa 10.1.3 Direct Rendering: Yes"**.

The article states that he got a 1680X1050 resolution and mine is only a 1280X800.  Where can I get the driver he was using to get this 1680X1050 resolution and how do I install it please.

---

### Post by ajgreeny on 2014-09-29
Difficult to know eactly what the other person has done but he could be using the xorg-edgers ppa from [URL="https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+index?field.series_filter="]https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+index?field.series_filter=
[/URL]
However, proceed with caution if you are not able to deal with the command line, as you could end up with no GUI at all after using a ppa for graphics, as happened to me once.

---

### Post by Ron_Callison on 2014-09-29
Thanks for the info but that is way above my knowledge base.  I think I'll live with the current resolution.

---

### Post by tgalati4 on 2014-09-29
I have a T43p--The "p" model has a higher-end graphics card (ATI in this case) that allows 1400 by 1050 resolution.  It's possible that your T61 has the lower-end Intel graphics that only support 1280 by 800.  What specific model of the T61 do you have?  Do you have standard graphics or enhanced graphics?

[http://www.thinkwiki.org/wiki/Installing_Debian_Wheezy_on_a_ThinkPad_T61#Intel_965GM](http://www.thinkwiki.org/wiki/Installing_Debian_Wheezy_on_a_ThinkPad_T61#Intel_965GM)

[http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

---

### Post by Ron_Callison on 2014-09-30
Does "Intel 965 GM" mean any thing?  How about "Lenova 6379-A13 T61"  Does that help?

---

### Post by Vladlenin5000 on 2014-09-30
Ok, before any further good intentioned attempts to help you, please check which model you really have. The maximum resolution depends as much on the graphics card/chip as on the LCD panel you have.
Thinkpads T61 were sold in many different configurations, with two different integrated Intel graphics chips and two other discrete ones from nVidia - there's already a world of difference here - and several different monitor options:

Display14.1-inch XGA (1024 x 768 resolution) TFT display
14.1-inch SXGA+ (1400x1050 resolution) TFT display
**14.1-inch WXGA (1280 x 800 resolution) TFT display**
14.1-inch WXGA+ (1440 x 900 resolution) TFT display
**15.4-inch WXGA (1280 x 800 resolution) TFT display**
15.4-inch WUXGA (1920 x 1200 resolution) TFT display

Isn't yours one of the bold ones above? If so, there's your maximum resolution. Nothing else you can do to improve it. Everything else is a ridiculous exercise.

---

### Post by tgalati4 on 2014-09-30
Intel 965GM is normally associated with "standard" graphics and thus lower resolution.  The nVidia chips are generally "higher-end" graphics and have higher resolution.  You can put in the model number at the Lenovo website and get the build-sheet printed out.  This should include the graphics option for your particular machine.  If the text that you are viewing in this forum looks crisp and clear, then you are running at the native resolution.  If the text looks fuzzy, they you might be at the wrong resolution.

---

### Post by Ron_Callison on 2014-09-30
Thanks all for the help.  Yes, it's the low resolution card.

---

### Post by tgalati4 on 2014-09-30
Don't dispair.  The higher-end video chips tend to get hot and delaminate--trashing the entire machine.  At least your graphics will last a long, long time.

---

### Post by Vladlenin5000 on 2014-09-30
> **Ron_Callison said:**
> Thanks all for the help.  Yes, it's the low resolution card.

Again, that really isn't the issue. Even the weakest integrated Intel graphics in the cheapest Thinkpad T61 configuration at the time is _capable of much higher resolutions for external monitors._ The limitation concerns your _internal monitor_. If it is a 1280x800 panel it won't do higher than that no matter what. It's physics, you can't change it, not in this universe anyway.

Once and for all, please get your specs right: [http://support.lenovo.com/us/en/documents/pd008989](http://support.lenovo.com/us/en/documents/pd008989)
(There are a a few different T61's out there and you need to know which one is yours; in the long run it'll save you lots of time, headaches and anxiety).

---

### Post by tgalati4 on 2014-09-30
Yes, with a DVI cable you can probably get 1920 x 1080 on a decent external monitor.  Sometimes you have to change the shared video RAM setting in BIOS, as Intel graphics chips tend to use regular RAM for video RAM.

---

