---
title: "Help - New User - Resolution Problem - Ready To Ditch Ubuntu Already"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by forrestgump on 2007-02-03
Hi,

I am brand new to ubuntu/linux - I really want to give it a go, but I am having real problems fixing the resolution. I am reasonably competnent on computers, but linux is a bit daunting, with the terminal/commands and all.

PC
Sony Vaio Laptop VGN-FS115B
X Black 1280 800 LCD Screen

PROBLEM
Cannot get ubuntu to change the resolution to 1280 800

TRIED
Have had a go using 915resolution, but cannot get it to work, so maybe we should start from scratch?

NOW
Could someone please guide me through this problem!

Please help, As I said, I really want to give ubuntu a go but if I can't even change the bloody resolution I will have to go back to Windows XP

---

### Post by forrestgump on 2007-02-03
anyone?

---

### Post by FastZ on 2007-02-03
When you go to System>Preferences>Screen Resolution, what resolutions are shown to choose from?

---

### Post by Mr. Eddy on 2007-02-03
1) type in console

```
sudo gedit /etc/X11/xorg.conf
```

give your password if promted

2) search in the file for 

```
Section "Screen"
```

3) add your resolution after the modes so it looks like this example here

```

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "MD32119PR"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

### Post by forrestgump on 2007-02-03
Hi

Resolutions to choose from are:
1024 768
800 600
640 480
1024 600

I also tried the solution above and the resolution and those to choose from remain the same.

pls help!!

I have been reading about it and can't get it to work!

---

### Post by forrestgump on 2007-02-03
Have tried this fix [http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)

1280 800 is listed in the last three modes, but resolution remains the same.

---

### Post by forrestgump on 2007-02-03
some help, pleeeeeeeeeeeeeeeeeeease

---

### Post by forrestgump on 2007-02-03
help?

---

### Post by drpaul on 2007-02-03
Have you tried this?

[http://www.ubuntuforums.org/showthread.php?t=351647](http://www.ubuntuforums.org/showthread.php?t=351647)

Paul

---

### Post by RandomJoe on 2007-02-03
The previous post's link says just what I was going to - I had an issue with my Dell D610's screen resolution and found I just had to use one of the earlier modes in the list in 915resolution to get it working proplerly.  In my case using a different mode didn't cause X to break, it just didn't do anything.  (In fact, the proper resolution was _already_ listed toward the bottom, and didn't get picked up.)

---

### Post by forrestgump on 2007-02-03
> **drpaul said:**
> Have you tried this?

[http://www.ubuntuforums.org/showthread.php?t=351647](http://www.ubuntuforums.org/showthread.php?t=351647)

Paul

PRAISE THE LORD

Paul I will gladly have your babies! Thanks a million, I was getting so mad.

I have read loads of threads and solutions - ANYONE having resolution problems on ubuntu try this solution FIRST!

[http://www.ubuntuforums.org/showthread.php?t=351647](http://www.ubuntuforums.org/showthread.php?t=351647)

---

### Post by indiver on 2007-02-03
This worked for me.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Hardware#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Hardware#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Although I had to reboot to get the new resolution to show up. 

But now it works nicely.

---

### Post by ognjen on 2007-05-08
Hi everyone,

I had the same issue - this was really frustrating :)
the way it worked for me is the following: when I replaced the first mode (640x480 i presume) and restarted X  i got that I could only chose between 800x600 and 1024x768 (which I had)...now, I did the same thing for those two modes (i.e. I deleted them basically) and was left only with the 1280x800...when I restarted X, voila, it worked! :)

the problem is that I can't choose 1024x768 now (in fact I can't choose at all) but that doesn't bother me at all :)

let me know if this works out for you

btw. you can always go to [www.whatismyscreenresolution.com](www.whatismyscreenresolution.com) to check it :)

---

### Post by ramjet_1953 on 2007-05-08
If you are running Feisty 7.04, and have Intel graphics, there is now a better solution to what I originally posted.

If you have previously installed[COLOR="Blue"] 915resolution[/COLOR] , it is probably best to uninstall that first.

Next, in a terminal type in the following code:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

This loads-up the new Intel driver

It is then a no-brainer. Just re-boot and it will auto-detect your optimum video settings and place all of the other options in the resolution menu.

Regards,
Roger :cool:

---

