---
title: "ThinkPad TrackPoint scrolling -- Success!"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by BarryTice on 2006-12-05
Here's a success story that might help someone else.

I just installed Edgy on an IBM ThinkPad 390E the other night, and I have been thrilled with the update from Hoary, which I've been running on this laptop for about a year and a half.

For example, in Hoary, I could never get the USB port to work right, which is an issue specific to the 390E. (It didn't work right under Fedora Core 1, either, though at one point I had had it working under Red Hat 9. If only I had remembered what I had done....) In Edgy, I plugged a USB flash drive in and it instantly recognized it and mounted the drive. Excellent!

So I thought I'd ask for the sky and get the scrolling function in the ThinkPad's TrackPoint to work -- where you hold down the third (blue) button while moving the TrackPoint nubby and it scrolls, the way a scroll wheel would.

I eventually found this Web site: [http://thinkwiki.org/wiki/Installing_Ubuntu_6.04_on_a_ThinkPad_X41](http://thinkwiki.org/wiki/Installing_Ubuntu_6.04_on_a_ThinkPad_X41)

It gives instructions for enabling it on an X41. I added two simple lines to my xorg.conf file, restarted my GUI, and it worked perfectly.

Ubuntu rocks! Edgy even more so! I hope this helps somebody out there.

-- b.r.t.

---

### Post by krazyman on 2007-05-13
Thanks for posting, Barry, works great for me on my R30!

---

### Post by Morfeas76 on 2007-06-02
|Thanks!!!!! You are great.... I have a IBM T40 and it is work great :D You are life saver

---

### Post by djennewe on 2007-09-20
Worked on my T42 as well.  Terrific!

---

### Post by sunsetgun78 on 2007-09-21
Awesome -- thanks!

---

### Post by kaptengu on 2007-10-30
Works on my X41. Thanks.

---

### Post by bacspasm on 2007-11-03
yup, works fine on my T30 too!  

Thanks a lot!

---

### Post by Campbellsssource on 2007-11-10
Same working on my x60s

Thanks.

---

### Post by seul on 2007-12-13
T60 Gutsy Gibbon -- success! Ah, life's easy.

---

### Post by htns on 2008-01-27
T42 Ubuntu 7.10

It works! ^_^

---

### Post by upforthedownstroke on 2008-03-02
not quite on r60e... hmm.

---

### Post by blue212 on 2008-03-20
works for me! Ubuntu 7.10 -> Thinkpad T23 

and just in case the link gets broken... [http://thinkwiki.org]("http://thinkwiki.org/wiki/Installing_Ubuntu_6.04_on_a_ThinkPad_X41")

```
To use the blue middle TrackPoint button as a scroll wheel (using the red TrackPoint itself to scroll up and down), do the following. In a terminal, enter these commands:

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original

$ sudo gedit /etc/X11/xorg.conf

In the editor, find the section headed Section "InputDevice" / Identifier "Configured Mouse" and add the following lines above the "EndSection" line:

Option "EmulateWheel" "true"

Option "EmulateWheelButton" "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again. Source for this item: Many ThinkPad-related sites, confirmed by experiment. 
```

---

### Post by MountainX on 2008-03-24
T61p Gutsy - why won't it work for me???? :confused:

What should I check?

---

### Post by blue212 on 2008-03-25
> **MountainX said:**
> What should I check?

The only thing I changed on my system was my xorg.conf file then restarted X

here is the part of my xorg.conf that I changed

```
Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" 		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
[COLOR="Red"]	Option 		"EmulateWheel" 		"true"
	Option 		"EmulateWheelButton" 	"2" [/COLOR]
EndSection
```

The lines in red are what I added.

---

### Post by x300 on 2008-03-25
> **MountainX said:**
> T61p Gutsy - why won't it work for me???? :confused:

What should I check?

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Trackpad_scrolling](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Trackpad_scrolling)

That is what I used for my T61p

---

### Post by Whiffle on 2008-03-25
Actually MountainX got this solved in another thread :)

---

### Post by MountainX on 2008-03-25
Yes, thanks to help from Whiffle, I got it solved. I love Ubuntu on my Thinkpad now!!!! :)

Here is the thread: [http://ubuntuforums.org/showthread.php?t=730045](http://ubuntuforums.org/showthread.php?t=730045)

The only thing I can figure is that I previously had some corrupt or non-printing characters in my xorg.conf file. I think I had the correct info in the file -- at least I couldn't find the mistake/problem. I pasted my xorg.conf file at this thread: [http://ubuntuforums.org/showthread.php?t=734358](http://ubuntuforums.org/showthread.php?t=734358)

If anyone sees where I went wrong, please let me know (for future reference). Once I learned to look at Xorg.0.log, I saw that I did have some other problems in my xorg.conf file. As a result of this, I think I will be able to get suspend/resume working now :)

---

### Post by emil_p8 on 2008-05-13
It doesn't!!! On my Lenovo R61 with 8.04 i have some weird problem with trackpoint scrolling. It worked for a few hours when i modified xorg.conf but on the next day it was gone, without touching xorg.conf anymore. 
However, when i plug in my external mouse, in addition to its own scroll wheel I can scroll exactly as i would like with the trackpoint, i.e. by pressing the MMB and moving the mouse up and down.
I tried dozens of combinations in my xorg.conf to no good. xev is also unable to detect the scrolling as separate buttons (however, it detects them on the external mouse, as buttons 4 and 5).
Any suggestions are welcome.

---

