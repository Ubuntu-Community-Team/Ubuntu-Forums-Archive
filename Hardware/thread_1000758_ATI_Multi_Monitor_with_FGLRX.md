---
title: "ATI Multi Monitor with FGLRX"
date: 2008-12-03
forum: Hardware
---

### Post by sowelie on 2008-12-03
I went through a whole lot of crap yesterday trying to get dual monitors to work properly with my work machine, so I'm posting here to hopefully save people some trouble.  Unfortunately I wasn't allowed to build my machine from scratch (like I requested).  I was stuck with a dell with an ATI x1300.  I recently got a second monitor and it just didn't want to work properly.  First of all, if you use the open source driver, the screen resolution utility built into Ubuntu works great.  My problem was for some reason when I use the open source driver, whenever I reset, X won't start.  So, I was stuck with the proprietary drivers.  The problem with the proprietary driver is that I couldn't get dual monitors to work the way I wanted using the aticonfig command.  I could set up two separate X screens, but not two monitors sharing the same X screen.  If I used the ati catalyst control center, it would work (once I added Virtual 3280 1200 to the Screen section in my xorg.conf).  However, whenever I restarted X I would have to reconfigure the dual monitors through the catalyst control center.  I found a trick mentioned here in the forums, go to System -> Preferences -> Sessions and click "Remember currently running program" under the options tab.  Now I have dual monitors working as I want.  

To recap, if you have the same problem as I do:

1. Add the virtual option to your xorg.conf under the screen section:

```

Section "Screen"
...
[INDENT]SubSection "Display"
	Virtual	3280 1200
EndSubSection[/INDENT]

```

2. Restart X.

3. Set up your screens with the catalyst control center.  Just go to the Display Manager, click Multi Display, then click Big screen to the left or right or top or bottom (however you have it configured).

4. Hit okay.

5. Go to System -> Preferences -> Sessions, click the options tab and click "Remember currently running application".

Now when you restart you should still have your dual monitors set up properly.  My only issue is I can't run compiz (I get the screen resolution is too large for the max texture size error), which doesn't bother me much.  I have written this off to the fact that my video card is pretty awful.

My simple xorg.conf is listed below:

```

ection "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	3280 1200
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusId		"PCI:3:0:0"
	Driver	"fglrx"
EndSection

```

---

### Post by Jindro on 2008-12-03
Hi,

have you tried aticonfig?

$aticonfig :
 1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.

---

### Post by sowelie on 2008-12-03
Yeah, I tried that multiple times.  The only result I was able to produce was having two separate X screens, which is not what I wanted.

---

### Post by funkyjansson on 2008-12-04
> **sowelie said:**
> Yeah, I tried that multiple times.  The only result I was able to produce was having two separate X screens, which is not what I wanted.

I want to have two separate X screens (I have one 16:9 TV and a 4:3 monitor) but I cant get it to do that. How do I fix that?

I could do it with my cheap nvidia-card, but I want to use my slightly better ATI-card, but i dont know how to.

Pleas help me, I've been trying so hard to get this to work.

I have a ATI x600 if that matters.

And oh yeah, I currently use the proprietary driver. I havent realy tryed the open scource one, when I changed the card from nvidia to ati Ubuntu told me I needed the prorpetiery one, so I installed it, first the one from the repo then the one from the ati-homepage.

---

