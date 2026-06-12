---
title: "Preferred Display Resolution"
date: 2004-10-17
forum: Hardware &amp; Laptops
---

### Post by mark on 2004-10-17
This is somewhat similar to [http://ubuntuforums.org/viewtopic.php?t=558](http://ubuntuforums.org/viewtopic.php?t=558) - but my quest is for a preferred resolution setting.  

Being an old f**t, my eyes seem most comfortable with 1152x864 on my 19" MAG 986FS monitor.  I have made repeated passes with the command:```
sudo dpkg-reconfigure xserver-xfree86
``` but I still haven't discovered how to enable this setting.  Here are the pertinent portions of my *XF86Config-4* file:

```
Section &quot;Device&quot;
	Identifier	&quot;Intel Corporation 82865G Integrated Graphics Device&quot;
	Driver		&quot;i810&quot;
	BusID		&quot;PCI&#58;0&#58;2&#58;0&quot;
	VideoRam	65536
	Option		&quot;UseFBDev&quot;		&quot;true&quot;
EndSection

Section &quot;Monitor&quot;
	Identifier	&quot;986FS&quot;
	HorizSync	30-86
	VertRefresh	50-160
	Option		&quot;DPMS&quot;
EndSection

Section &quot;Screen&quot;
	Identifier	&quot;Default Screen&quot;
	Device		&quot;Intel Corporation 82865G Integrated Graphics Device&quot;
	Monitor		&quot;986FS&quot;
	DefaultDepth	24
	SubSection &quot;Display&quot;
		Depth		1
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		4
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		8
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		15
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		16
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		24
		Modes		&quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1200x800&quot; &quot;1152x864&quot; &quot;1024x768&quot;
	EndSubSection
EndSection

``` However, when I run *Computer-&gt;System Configuration-&gt;Screen Resolution*, my only choices are 1600x1200, 1280x1024, 1024x768, etc.  How do I get 1152x864 as an option?

*Thanks!*

Mark

---

### Post by ubuntu-geek on 2004-10-17
Hey Mark.

Change the following line:
Modes      "1600x1200" "1280x1024" "1200x800" "1152x864" "1024x768" 

To read like this:
Modes      "1152x864" "1600x1200" "1280x1024" "1200x800" "1024x768" 

That will make the "1152x864" resolution default. Hope that helps.

---

### Post by mark on 2004-10-17
[quote=ubuntu-geek]Hey Mark.

Change the following line:
Modes      "1600x1200" "1280x1024" "1200x800" "1152x864" "1024x768" 

To read like this:
Modes      "1152x864" "1600x1200" "1280x1024" "1200x800" "1024x768" 

That will make the "1152x864" resolution default. Hope that helps.[/quote] Unfortunately, it didn't - 1152x864 still doesn't show up as an option.  Is there perhaps some other config file I need to manually edit? And, BYW, I think you're doing a great job here with the forum.

*Thanks!*

Mark

---

### Post by ubuntu-geek on 2004-10-17
Thanks for the kind words.

When you change that line did you make changes to each one or just one them?

---

### Post by mark on 2004-10-17
[quote=ubuntu-geek]Thanks for the kind words.

When you change that line did you make changes to each one or just one them?[/quote]You're more than welcome - you deserve it.

And I did a global replacement of all affected lines.  Note that I am currently using the 1280x1024 resolution and getting by with "tweaking" various font sizes.  But, you know how it is - we get set in our ways &amp; want what we want...&lt;g&gt;

Mark

---

### Post by jahLux on 2004-10-21
Like you Mark, I'm anxiously awaiting UBUNTU's resolution (sic) of this Display problem.   8)

---

### Post by jahLux on 2004-11-15
Hey Folks,
Someone fixed this one AUTOMAGICALLY - I took a look at System Configuration> Screen Resolution - just for the hell of it and there it was - a new resolution choice table, which included the long sought after 1152x768 that I never could attain otherwise.
I'm not even going to try figuring it out - THANKS TEAM UBUNTU!

---

### Post by FLeiXiuS on 2004-11-16
I doubt this is a problem with ubuntu.  Please check to see whether or not your card is ATI or NVIDIA.  If not any then, it may be ubuntu or conceivibly my next point.  

A ModeLine. 

Here's a free tool to calculate your modeline.
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

