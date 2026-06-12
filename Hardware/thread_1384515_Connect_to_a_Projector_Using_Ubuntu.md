---
title: "Connect to a Projector Using Ubuntu"
date: 2010-01-18
forum: Hardware
---

### Post by dmchugh on 2010-01-18
I have a Toshiba Satellite a215-S7437 that has an s-video connection that I use to connect to my tv.  I am wondering how I can connect to my tv using that with Ubuntu 9.1.  My computer has a ATI Radeon X1200 graphics card I believe.

---

### Post by ubudog on 2010-01-18
> **dmchugh said:**
> I have a Toshiba Satellite a215-S7437 that has an s-video connection that I use to connect to my tv.  I am wondering how I can connect to my tv using that with Ubuntu 9.1.  My computer has a ATI Radeon X1200 graphics card I believe.

Just plug the s-video cable into your computer on one end and your tv on the other.  Then hit the FN key and another key on the top of your keyboard that has a picture of a monitor.  That should do it. ;)

---

### Post by dmchugh on 2010-01-18
I tried that but it did not work.  Is there a way that I can manually do it myself through a certain program rather than a shortcut like that?

---

### Post by Cuco3 on 2010-01-18
> **dmchugh said:**
> I tried that but it did not work.  Is there a way that I can manually do it myself through a certain program rather than a shortcut like that?You mean configure your display settings?

You can configure that here through:
System > Administration > (videocard maker) ...

To configure display settings, click on "X Server Display Configuration" when you reach this window:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144081&d=1263852349[/IMG]

If you think this is a bit of a hassle to switch your monitor configurations, go here and click on the up arrow. It's an idea for the implementation of quicker display setting configurations in Ubuntu.

[http://brainstorm.ubuntu.com/idea/23071/](http://brainstorm.ubuntu.com/idea/23071/)

---

### Post by ubudog on 2010-01-18
For ATI graphics it would be in Applications>Other>ATI Catalyst Control Center.  There should also be an Administrative option too.

---

### Post by blackened on 2010-01-18
You can always use xrandr from the commandline. Just plug the svideo cable into both devices and issue the command
```
xrandr --prop
```

to see the available display options.

---

### Post by dmchugh on 2010-01-18
I tried everything you guys have been telling me but it does not work.  I downloaded the ATI Catalyst Control Center but it will not let me run it.  It says i have no ATI drivers, which I do.

The other thing where you go to terminal and type in the command.
This came up.  I was hooked up to the tv through the s-video slot and nothing happened.

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
	load_detection: 1 (0x00000001)	range:  (0,1)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
	scaler: full
   1280x800       59.9*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4

---

### Post by blackened on 2010-01-18
For the drivers: it might be necessary to install the ATI drivers from the repos before upgrading to the catalyst drivers. At least that's what I've gleaned from the small amount of reading I've done. I don't own any ATI hardware, so YMMV.

The xrandr command wasn't supposed to do anything but provide some information, which it did.

Best I can tell, the driver you're using doesn't enable the s-video output. Work on first getting the latest Catalyst driver going.

---

### Post by dmchugh on 2010-01-18
How am I able to get the catalyst driver going?  And this has worked with windows many times. It works as duplicate, extend, laptop monitor, and s-video only.  I just do not know how to use it with ubuntu.

---

### Post by blackened on 2010-01-18
Just because something works on Windows doesn't, by any stretch of the imagination, mean that it will work in another operating system.

Microsoft has the ability, through its monopoly, to apply leverage to hardware manufacturers so that their products are guaranteed to work on Windows. This can sometimes have the converse effect that those same manufacturers, because of market political alliances, license conflicts, etc., refuse to release working drivers (or source code) for other operating systems.

This whole fiasco often leads to drivers that have been reverse engineered or cobbled together. Sometimes they work flawlessly, sometimes not so much. Yours falls into the not so much category.

I already suggested how to get the official driver going. Because I don't own, and am not familiar with, this particular hardware, that's all the help I can give. You'll have to rely on google and the forums for the rest. Good luck.

---

### Post by dmchugh on 2010-01-18
Thank you for all your help now I know what I am actually even trying to do!

---

### Post by blackened on 2010-01-18
No worries. Post back if you come up with anything so that others may benefit from what you find.

---

### Post by ogoforth on 2012-09-15
One more reason I can't simply dump M$.  What good is a notebook if I can't use it for presentations?  I shouldn't have to arrive and hour early to figure out how to connect to a projector.

---

