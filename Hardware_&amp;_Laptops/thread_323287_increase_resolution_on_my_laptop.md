---
title: "increase resolution on my laptop?"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by tortus on 2006-12-21
I have searched around these forums and Google but have not been able to figure this out.

I have an hp pavilion dv6000 laptop with the Intel i810 graphics chipset. xorg.conf only includes one resolution for all depths: 1280x800.  

        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection

24bit is the default depth. 

But the screen resolution preferences applet claims I am running at 1024x768. I think this is correct, as this monitor is pretty darn low res right now.

I attempted to make the default depth 16 and add "1440x900"

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

which didn't work (didn't think it would). But it didn't do anything at all. No noticable difference. I was expecting the screen resolution preferences applet to include the new resolution option, but it still just has 1024x768. Not sure why I expected that, it doesn't even have 1280x800 as an option.

Do I have to give this graphics chip more memory? How can I do that? I don't care that much about color depth, 16 is fine, I just want a higher resolution.

---

### Post by Ashrael on 2006-12-22
reconfigure your x (dpkg-reconfigure xserver-xorg) and tell it what your max resolution and depth is... fiddle around with it a bit, i did and got it to work,,,,

HTH!

---

### Post by tortus on 2006-12-25
I can't get it to work. No matter what i tell xserver-xorg or manual edits to xorg.conf, my machine insists on running at 1024x768. I confirmed that's what I'm really running at by taking  a screenshot and checking its size in GIMP.

I've told the xserver-xorg conf program that I want to user 64 megs of main memory for video memory, that I want a minimum of 1280x1024, and to default to 16bit color. The only change I get in the screen resolution pref applet is I can now set it to 800x600 and 640x480. Joy.

---

### Post by Ashrael on 2006-12-27
Sorry for keeping you waiting...but it was christmass you know.. ;)
Show us whats in xorg.conf please...must be more specific...I am guessing that you haven't installed your screentype well enough yet....so get your xorg.conf up here, and we'll see..

Merry christmass y'all...

---

### Post by tortus on 2006-12-28
cool, thanks for the help. Hmmm, how can I post my xorg.conf without making  a gigantic post? :) let's see, I'll try an attachment...

---

### Post by Ashrael on 2006-12-31
Hi! So I found some time on this last day of the year to try and help you out... I found this post : [http://www.ubuntuforums.org/showthread.php?t=259437&highlight=i810](http://www.ubuntuforums.org/showthread.php?t=259437&highlight=i810)  ,....Which seems to yield succes for this guy, so give it a try, also found other posts hinting at this sollution....So it just might work...

keep us posted on any progress...

Wishing everyone a happy new year....

And make sure ya don't loose ya fingers tonite! (damn hard typing without)

Ashrael

---

### Post by tortus on 2007-01-02
Thanks for the help. I actually just figured it out through some lucky googling.

I found this page

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

which pointed me to the 855resolution utility. I installed it (sudo apt-get install 855resolution) and it actually installed the 915resolution utility. During the install process there was some output indicating 1280x800 modes were being added to something or other. I rebooted and bam! came back in 1280x800. So much better than 1024x768!! I can actually do my work now, modern IDEs demand a lot of screen real estate :)

---

### Post by dmartinsca on 2007-01-03
To clarify this problem: the intel graphics card drivers (mainly known as i810 as called in your xorg.conf file) only displays resolutions which are included in the video BIOS of the graphics card. By default intel only includes VESA (a type of graphics standard for computers) which doesn't include widescreen resolutions like 1280x800. Ideally the company who sells computers with this graphics chip would re-write the BIOS to include the resolution the attached screen was meant to run at, but I don't think i've come across one that does yet.

So, the 915resolution program writes over some of the resolutions included in the video BIOS on every boot of the computer. It has to happen at every boot because it is only overwritten in RAM. This way no harm can come to the video card.

Hopefully this isn't too technical! This question comes up a lot, maybe a moderator could make one of the better explanations of this a sticky?

---

### Post by Ashrael on 2007-01-03
So another one bites the dust... Ubuntu does look so much better in widescreen ;)

---

