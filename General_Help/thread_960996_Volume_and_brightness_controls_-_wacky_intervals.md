---
title: "Volume and brightness controls - wacky intervals?"
date: 2008-10-27
forum: General Help
---

### Post by dt_ on 2008-10-27
Hi everyone,

I just installed Ubuntu and given that I'm a total linux noob I have a couple of questions that may or may not be fixable lol .. hopefully you might be able to help me solve these problems.

I am using a Dell XPS m1530 laptop.

Firstly, I've noticed that the volume controls in Ubuntu - whether I use the touch volume controls on the laptop itself or the software controls in the OS - offer a very small amount of variance in volume levels. Anything below 60 volume is hardly audible; 60-75 is very quiet, and from 75-100 -ish it gets very loud. I want something medium.. is there something I can do to make it more like in Windows (Vista)? :/   (BTW, initially, I had to raise volume in alsamixer for the "Front" setting so that when the volume was turned up all the way it would be as loud as it would be in Vista.)

Second, by using the Fn+Up/Down arrows on my keyboard I can change the brightness of my LCD just like in Windows. However, I only have something like 4 or 5 brightness levels / intervals to choose from; in Windows I had probably around 10. How can I get more intermediates? BTW, my max brightness in Ubuntu is definitely brighter than in Windows -- is that dangerous to the LCD or is it just gonna use more power (less battery life)?

Oh and one more thing -- is there any way to get fonts looking as sharp as they do in Windows? even if I use the "subpixel smoothing" option the text still looks blurry even with the MS fonts (Verdana). :/ I am using the LCD at its native resolution 1440x900 with 50Hz setting.

Thanks everyone! BTW how is Ubuntu vs. Vista in terms of power consumption? ATM I'm using the "extra" interface which has those fancy animations. :)

---

### Post by dt_ on 2008-10-28
Anyone? :(

---

### Post by sdennie on 2008-10-28
That's a lot of questions...

> **dt_ said:**
> 
Firstly, I've noticed that the volume controls in Ubuntu - whether I use the touch volume controls on the laptop itself or the software controls in the OS - offer a very small amount of variance in volume levels. Anything below 60 volume is hardly audible; 60-75 is very quiet, and from 75-100 -ish it gets very loud. I want something medium.. is there something I can do to make it more like in Windows (Vista)? :/   (BTW, initially, I had to raise volume in alsamixer for the "Front" setting so that when the volume was turned up all the way it would be as loud as it would be in Vista.)


I'm not an ALSA expert but, I have it on good authority that when the PCM channel is set to higher than 74% ALSA boosts the volume via software.  Maybe try setting the PCM lower and seeing if your volume controls are smoother.

> 
Second, by using the Fn+Up/Down arrows on my keyboard I can change the brightness of my LCD just like in Windows. However, I only have something like 4 or 5 brightness levels / intervals to choose from; in Windows I had probably around 10. How can I get more intermediates? BTW, my max brightness in Ubuntu is definitely brighter than in Windows -- is that dangerous to the LCD or is it just gonna use more power (less battery life)?


My XPS M1330 does brightness at the hardware level and there is a kernel module that can be loaded that duplicates this effort (which would effectively reduce your brightness levels by half).  See if this post helps at all: [http://ubuntuforums.org/showpost.php?p=5009164&postcount=3](http://ubuntuforums.org/showpost.php?p=5009164&postcount=3).  The maximum brightness is a function of the hardware and so I don't think it's possible for linux to set it "too high".

> 
Oh and one more thing -- is there any way to get fonts looking as sharp as they do in Windows? even if I use the "subpixel smoothing" option the text still looks blurry even with the MS fonts (Verdana). :/ I am using the LCD at its native resolution 1440x900 with 50Hz setting.


It seems unlikely that 50Hz is the native refresh rate for your LCD.  However, that's not likely to be the problem with your fonts.  Can you post a screenshot of the fonts?  It's possible that it's just your eyes are accustomed to fonts looking a certain way and so different automatically equals worse.

> 
Thanks everyone! BTW how is Ubuntu vs. Vista in terms of power consumption? ATM I'm using the "extra" interface which has those fancy animations. :)

Laptop power savings is very good on linux but, it's not enabled by default and it's a bit cumbersome to get working well.  Though aimed at the M1330, you may find this link useful: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by dt_ on 2008-10-28
Thanks for the quick and helpful response :)

Unfortunately lowering pcm to below 74 didn't change anything other than making my maximum volume much quieter.

As for power consumption and brightness I will look into those guides -- thank you!

Here's a screenshot pertaining to fonts..: [http://i35.tinypic.com/15clix1.jpg](http://i35.tinypic.com/15clix1.jpg)

---

