---
title: "Correct dirver for intel mobile 915 and Gutsy?"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by silvari on 2008-01-13
I have a Toshiba laptop with an Intel Mobile 915GM/GMS/910GML video adapter. I'm running Gutsy (7.10).

Having the following problems:

1. I have a Gateway FPD2275 TFT LCD display hooked up via VGA cable. The optimal resolution for this display is 1680x1050. But the best resolution that Gnome with do, is 1440x900 at 60Mhz. Funny thing is, I have xorg.conf set up to use 1680x1050 at 75 , but in Gnome's 'Screen Resolution' app, neither '1680x1050' nor '75' are options.

2. I have done so much futzing around with this, at this point, I have no idea what driver I should be using. At one point (when I was at Feisty?) xorg.conf was using the 'i810' driver, and I also installed the i915resolution package (but I don't know if I ever got it doing anything useful). Since upgrading to Gutsy, xorg.conf is now using the 'intel' driver. And if I run

> dpkg-reconfigure xserver-xorg

... the 'i810 driver isn't even an option anymore

3. When I try to play DVD's, downloaded video, etc. things look pretty nasty Colors are all off. Yes, xorg.conf is set to 24-bit .

SO: My questions are:
1. What driver is the recommended driver, for an Intel Mobile 915GM/GMS/910GML, under Gutsy? And, what's the best way to get / install this?
2. Is the use of '915resolution' needed or recommended, with the recommended driver?
3. Thoughts on why Gnome seems incapable of seeing and using all the resolutions / modes supported by the card, especially the 1680x1050 ?

Thanks VERY MUCH in advance for any assistance you can give. I have spent a ridiculous amount of time trying to get my (rather awesome) external display to work under Linux. I don't want to have to keep rebooting into Windows just to watch DVD's.

---

### Post by silvari on 2008-01-14
After hours of surfing, reading a  billion other posts / articles that sortof touch on this, I'm posting on my progress, hoping to save some other poor S.O.B from the trouble I've had with this.

First thing I've learned: if you're using the newer 'intel' driver (aka "Experimental Modesetting Driver") that comes with (?) Gutsy, then you do NOT need to install/use '915resolution'. That is only needed when you're using the older 'i810' driver.

So: it's either:
- you're using the 'intel' driver, OR;
- you're using the 'i810' driver + '915resolution' package

There's some information on this here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Second thing I've learned: trying to get a good working configuration for an external high-res display connected to your laptop's VGA port, SUCKS. You would think that Gutsy's "Screens and Graphics" utility could/would accommodate this, but in my experience, it does not. When Gnome loads it seems to get a bit confused about which screen you're trying to configure for. In my case, it wasn't able to autodetect the settings for my external LCD, probably because the 'internal' LCD was still on, and its settings are much lesser than the external's.  I ended up using the Screens and Graphics utility go ahead and slice and dice the xorg.conf, then went into it manually and added the settings for my monitor (that I'd learned via 'ddcprobe') and the resolution I wanted, then rebooted.

So, now, I'm happily viewing Gutsy via my awesome external LCD at 1680x1050@75hz, and things look pretty good. But, since the settings that are powering this are definitely NOT supported by my laptop's LCD (max res is 1280x768, I think), I have a feeling that when I try to log in to Gnome without the external LCD attached, I'm gonna be SOL. So, the next challenge will be: how to toggle between one set of video settings, and another; or set up an xorg.conf file that has "both" in it; which, the 'Settings and Graphics' utility seems to do, but I'm not sure HOW; especially, how it designates which group of settings pertain to the internal LCD, vs. which set pertains to the External; and , how it chooses between the two (i.e. how does it know, when the External LCD is not attached, how to use the internal LCD settings?). There was a 'i810switch' utility that could be used with the old driver, but....

More to come. If anyone has any ideas on this, please post. Thanks.

---

### Post by silvari on 2008-01-14
Looks like I chirped too soon. I just through a DVD in....

- totem launched, started playing.
- tried to go to Full Screen, and Gnome automagically changed its resolution to "1680x1050@60hz" from "same@75hz", which left a two-inch black border to the left of the screen
- quality of DVD playback was pretty bad. Very choppy.

---

### Post by schaumkeks on 2008-01-18
I have a Fujitsu-Siemens Amilo M 1450G with internal 15,4'' Widescreen display and also wanted to find a solution to this problem.

Haven't used the new "intel" driver until now but I'm surprised how well things work.
With the old i810 driver I used to clone a screen but because my two displays have a different native resolution, Internal 1280x800 and external Acer AL2216Wd 1680x1050, I wanted to setup a dual head configuration like described in ["How to setup Dual Head for Intel Graphics with RandR 1.2"]("http://www.intellinuxgraphics.org/dualhead.html") Section 2.2. (Cloning works out-of-the-box)
So the relevant part of my xorg.conf now is as simple as:
```
Section "Device"
	Identifier	"Intel i915GM"
	Driver		"intel"
	Option		"monitor-LVDS" "Default Monitor"
	Option		"monitor-VGA" "Acer AL2216Wd"
	#Option"monitor-TMDS-1" "dvi"
EndSection

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
	#Option		"PreferredMode" "1280x800"
	#Option		"Enable" "false"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216Wd"
	Option		"DPMS"
	#Option		"PreferredMode" "1680x1050"
	#Option		"Position" "1280 0"
	Option		"Below" "Default Monitor"
	#Option		"Enable" "false"
	#Option		"Rotate" "left"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i915GM"
	Monitor		"Default Monitor"
	DefaultDepth	24
	#SubSection "Display"
		#Modes		"1280x800" "1024x768"
		#Virtual	1680 1850
	#EndSubSection
EndSection
```

This puts the external screen right below the internal and results in a virtual 1680x1850 desktop. The guide says "There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048." so better do not create a virtual desktop with a side larger than 2048.
Thanks to DDC the resolutions are detected so I didn't even provide a "Modes" line. If the external display is not attached only the internal is used as before without changing anything.

While X-Server is running you can even plugin the external display and achieve the same with the command:
```
xrandr --output VGA --below LVDS
```
and afterwards unplug and reset with
```
xrandr --auto
```

The problem with DVD Playback:
First, totem is not the best app to playback DVDs. It refused here completely (plugins missing, although I had them all installed) and switching to FullScreen lead to a full lockup of my notebook. Better not use it.

I prefer VLC or mplayer (although I can't use dvd menus with mplayer atm.). If you run one of these players you should be able to move it to the big screen and then hit "F" or double click to go to fullscreen. Awesome!

Thanks silvari for inspiration :)
Bye, Sven

---

