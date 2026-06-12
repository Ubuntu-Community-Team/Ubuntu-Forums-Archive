---
title: "Generic touch screen driver?"
date: 2009-01-23
forum: Hardware
---

### Post by gnugu on 2009-01-23
Hi,
I have Xplore iX104 tablet ([http://www.xploretech.com/index.pl?id=2931&isa=Category&op=show](http://www.xploretech.com/index.pl?id=2931&isa=Category&op=show)) which I managed to boot to live XUbuntu USB.

Seems to work and I can use a built in nipple joystick but the touch screen doesn't work at all.

Is there some sort of generic touch screen driver? I see all these posts about specific tablet PC's. I doubt that there will be anything specific for iX104.

Any suggestion is welcome.

Thanks.

---

### Post by Favux on 2009-01-23
Hi gnugu,

There is a generic touch screen driver called evtouch in Synaptic Package Manager.  There are some evtouch threads with HOW TO's and I think a Ubuntu Community wiki.  You probably need to modify your xorg.conf too.

You're sure it's a touch screen an not a digitizer?  Your link really didn't give specifics.  What features do you have.  Stylus, eraser, side-switch, touch?

Hope this helps.

---

### Post by gnugu on 2009-01-23
Hi Favux,
thanks for your response. I'll give it a try later tonight.

Yes, I'm sure it is a touch screen with pen that moves your cursor around as you hower (is that what digitazer is?). It has both. How do I know? The thing has an XP tablet edition installed. I'm trying to get rid of it in favour of Ubuntu. Ubuntu doesn't work on it, so I'm going for XUbuntu.

Laugh or not, I want this beast for my kids to draw on with teir fingers.

---

### Post by Favux on 2009-01-23
Hi gnugu,

You can't really tell the difference just by looking.  XP tablet did support touch screens.  A digitizer might have a super fine grid worked into the screen if you look real close.  A touch screen generally has less features, a stylus and of course touch.  A digitizer would be more accurate with the stylus.

Evtouch doesn't support all hardware, that's why I thought it would be useful to know.  Sounds perfect for the kids.  Inkscape might work.  Edubuntu might have drawing programs for kids.

Good luck and have fun!

---

### Post by gnugu on 2009-01-23
Favux,
I don't know what exact hardware the screen is.

When I boot to XP I can swith between touch screen mode and digitizer and both work. When in touch mode I can use fingers, when in other mode I can only use attached sylus.

Would evtouch support touch screen as well as digitizer?

Thanks.

---

### Post by Favux on 2009-01-23
Hey gnugu,

Evtouch is for touch screens.  If you determine you have a Wacom digitizer, or one of the other manufacturer's digitizers that can emulate a Wacom then evtouch won't do.  You'd want the linuxwacom drivers.  Links for several ways to install them and a HOW TO about compiling the kernel driver at:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

If you determine you need linuxwacom, then probably best to start with Loic2's wiki's.  He has instructions for the prepackaged drivers from the repositories there.  I'm just not sure that toggling from fingers to stylus in XP really tells you much.  How recently did this model come out?

Hope this is helpful.

---

### Post by gnugu on 2009-01-23
The model is about 5-6 years old.

If I use Wacom, will I be able to use the fingers?

---

### Post by Favux on 2009-01-23
Sure, some of the more recent models like mine have integrated digitizers and touchscreens.  And of course now multitouch is becoming the rage, thanks to Apple.

Given the age, you probably have a touch screen.  So let's hope evtouch supports it.

---

### Post by mcin8130 on 2009-01-23
Hi gnugu,
I too have a iX104, but I'm having problems getting Ubuntu to load from USB. Do I need to use Xubuntu? Any secrets?
Someone at a conference was using an iX104 and they mentioned Evtouch so if I can get past the USB loading I'll give it a try.

---

### Post by gnugu on 2009-01-25
mcin8130,
here is how I have managed to load XUbuntu on it [http://ubuntuforums.org/showpost.php?p=6591618&postcount=7](http://ubuntuforums.org/showpost.php?p=6591618&postcount=7). (here is the whole thread [http://ubuntuforums.org/showthread.php?t=1045341](http://ubuntuforums.org/showthread.php?t=1045341))

The post is about booting from USB. I too was unsuccessful loading Ubuntu. I guess that's because of the lack of memory. So I'm now playing with XUbuntu.

Good luck! Let me know if you have more questions - either here or there, based on what the question is related to.

---

