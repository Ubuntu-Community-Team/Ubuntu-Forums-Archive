---
title: "Screen resolutin - monitor settings"
date: 2008-11-28
forum: General Help
---

### Post by syd2o2 on 2008-11-28
I've just installed 8.10 and so far not good. I've been stopped at the first hurdle: the famous screen resolution problem. 
When I first started my system, the highest option was 800x600. After going to system-administration-hardware drivers and activating nvidia driver, I got the fabulous 640x480 resolution as my top choice.
My hardware is Geforce nvidia 5900 and monitor is Eizo T563-T. It's a crt monitor.
I use to able to set my monitor parameters in the xorg.conf file. But that file is pretty much empty now, this is all that's in there:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I don't have the screen and graphics option anywhere in the menus, nor can I find it in the main menu settings. So I have no clue how to get to my monitor and set it's properties (vertical and horizontal settings and such) to correct values.

Just some of the things I've tried:

dpkg-reconfigure xserver-xorg - after running through it, nothing changed,

Adding this into my xorg.conf
SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768"
    EndSubSection
Result:xserver won't start

result of xrandr:
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0*    51.0     52.0  
   320x240        51.0  

I tried to generate a modeline for 1024x768@85Hz with cvt and add it with xrandr -new mode, but then don't know how to add it.
1.cvt 1024 768 85
# 1024x768 84.89 Hz (CVT 0.79M3) hsync: 68.68 kHz; pclk: 94.50 MHz
Modeline "1024x768_85.00"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
2. xrandr --newmode "1024x768_85.00"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
3.xrandr --addmode VGA 1024x768_85.00
xrandr: cannot find output "VGA"

Don't know what to put into the output.


I've looked around, there's a about a billion resolution problem threads. You'd think it would be fixed by now, but no, the same problem (or variation of it) since the 5.10 (the first version I used).
Can anyone help me in setting (detecting) my monitor properly?

---

### Post by ajgreeny on 2008-11-28
My xorg.conf got things wrong as well, in fact it was almost empty and I added the content of an older config file, from Dapper I think, with the following content:-

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    [B]DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection[/B]
EndSection

I merely added the lines in bold to the section of other existing lines at the bottom of the xorg.conf file and "Bingo!"  Resolution of 1280x1024 as I wanted.  Give it a try with your own required resolution and it may work for you too.

---

### Post by gettinoriginal on 2008-11-28
In System > Admin there should be a Nvidia X server settings, I can select my monitor and settings there.  I just had to reset it after updating to 8.10

---

### Post by syd2o2 on 2008-11-29
@ ajgreeny
Nope, as stated in the first post, tried that already, didn't get any extra resolutions.

@gettinoriginal
Nope, tried that too. Don't have any other resolutions available to select in nvidia settings.

---

### Post by gettinoriginal on 2008-11-29
Wow, that's wierd, under X Server Display Configuration, advanced, it lets me set the resolution manually.

---

### Post by blackened on 2008-11-29
Had some trouble finding the appropriate information on this monitor as it's pretty old.

Edit xorg.conf's monitor section to look like this:
```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync          30-86
	VertRefresh        55-160
EndSection
```

Then restart X. Should give you some more resolution options.

---

### Post by syd2o2 on 2008-11-30
Thanks, that was it. 
I remember using something like this in 7.10 and earlier )8.04 got it right on it's own). I just thought it wouldn't work anymore since xorg.conf  was practically empty.

---

### Post by blackened on 2008-11-30
Glad you got it working. Please mark this thread as solved.

---

### Post by jivabill on 2008-12-01
There is one problem left however.

As you will note if you read the xorg.conf file from the top that disables automatic updating of that file.  Not sure how big a problem that could be.
b

---

### Post by blackened on 2008-12-01
> **jivabill said:**
> There is one problem left however.

As you will note if you read the xorg.conf file from the top that disables automatic updating of that file.  Not sure how big a problem that could be.
b

Considering the pre-edited version of the file is essentially blank, it should only be a problem if they decide to rescind bulletproof-x, which is something I don't see happening in the near future, but hey anything's possible.

Mine has looked this way since installing 8.10 in September and I've experienced no problems, but, as always, YMMV.

---

### Post by jivabill on 2008-12-02
Hi Blackened, I have been stuck on the screen resolution thing on 8.04 for some weeks.  Even started a thread about my troubles.  No dice.  BUT I just tried the fix you suggest, putting the monitor Horiz and Vert frequency ranges in the Monitor section in xorg.cong.

VOILA !! Now I have a big long list of possible resolution settings in the System>Preferences>Screen Resolution tool.  Before all I had was 800 x 600 and 640 x 480.

THANK YOU THANK YOU you are indeed a wizard!

Regards
bill

---

### Post by jivabill on 2008-12-02
OOPS one thing I miss spelled xorg.conf.

The other thing I wanted to say, I got this Sylvania F70 brand new in a never opened box about 2 years ago.  Someone had it since the 90's and never used it and I got it free in a swap deal for a win98se tower desktop.

So I looked on my bookshelf and there was the user manual.  Duck soup after that.
bill

---

### Post by blackened on 2008-12-03
> **jivabill said:**
> Hi Blackened, I have been stuck on the screen resolution thing on 8.04 for some weeks.  Even started a thread about my troubles.  No dice.  BUT I just tried the fix you suggest, putting the monitor Horiz and Vert frequency ranges in the Monitor section in xorg.cong.

VOILA !! Now I have a big long list of possible resolution settings in the System>Preferences>Screen Resolution tool.  Before all I had was 800 x 600 and 640 x 480.

THANK YOU THANK YOU you are indeed a wizard!

Regards
bill

I'm glad it worked for you. It grieves me that simple problems like these often prove to be deal-breakers for new users. Hopefully they will get some attention in the next release. Unfortunately the problem of supporting such a huge array of hardware is, I'm sure, very daunting to the developers, but it is better to be supportive of their efforts than complain that they are neither omniscient nor omnipotent. They are only human like the rest of us and, that said, their work is simply amazing and well appreciated.

---

### Post by jivabill on 2008-12-03
Hi Blackened, Bill here.  Yes, we should appreciate what the developer team is trying to do.  It is a big and complicated job.  

BUT, problem is, there has been a huge amount of PR about Ubuntu from Canonical.  All claiming it is ready for the masses. And claiming that it is kind to older hardware. (Not my experience). Unfortunately problems like the display resolution one that have not been addressed for many versions of the OS do not make a good ad for Ubuntu and do not make the claims look valid.

When M$OFT can get it right most of the time in their releases it does not look good when these problems show up in Ubuntu.  For example, my monitor is fully supported in Win XP, I was running that previously.  Same goes for the Grub Error 18 problem that has little or no solution available.  Don't happen in XP or Win 98se for that matter.

So the basic issue here is, IF you are going to have Ubuntu and its derivate versions make some headway in the marketplace IT HAS TO WORK.  If M$ can do it then it can not be that difficult.  With all M$'s exasperating faults it DOES work most of the time.

When I am confronted with a problem on installation like the display resolution thing the very first thought I have is Ubuntu is not ready for prime time yet.

Anyway, my thoughts, I have a lot of company too.  I do appreciate all the help I get on the forums, and I feel that as nice as the help is all those issues should not be and therefore help should not be needed.  The OS should work for both old and new hardware out of the box.

My two cents
Bill

---

