---
title: "Howto enable S-Video"
date: 2004-12-24
forum: Hardware &amp; Laptops
---

### Post by goran on 2004-12-24
Hi everybody,
How can I enable S-Video Out on DELL Latitude d505 (Intel 82852/855GM).
It's working on XP.
I want to watch DIVX on my TV.

---

### Post by [S2] on 2005-03-02
[QUOTE=goran]Hi everybody,
How can I enable S-Video Out on DELL Latitude d505 (Intel 82852/855GM).
It's working on XP.
I want to watch DIVX on my TV.[/QUOTE]

i'm interested in this as well. Did someone manage to get it to work?

---

### Post by hedu on 2005-03-03
Yeah me, too
Also I have an output for another monitor on my laptop. I'd like to get this working too

---

### Post by rep on 2005-03-03
Hehe, me too, i'm interested,
i have a toshiba a10 with the same graphic chip, and no way to get tvout (and also second vga out) working...

---

### Post by dodok1 on 2005-03-03
[QUOTE=hedu]Yeah me, too
Also I have an output for another monitor on my laptop. I'd like to get this working too[/QUOTE]

I have Intel 855GM on my Toshiba A50 and using both displays. I've tried also the TV Out and it works also (but with wide black border around and I haven't played with it anymore).
You need to be carefull what display is active at the boot: I have to switch to Primary display during boot...

To be exact I am using Debian/testing with XOrg 6.8.1 packages from Ubuntu.

This is may setup for dualhead in /etc/X11/xorg.conf :

```

Section "Device"
    Identifier  "I855GM-0"
    Driver      "i810"
    BusID       "PCI:0:2:0"
    Screen      0
    Option      "MonitorLayout" "CRT,LFP"
EndSection
Section "Device"
    Identifier  "I855GM-1"
    Driver      "i810"
    BusID       "PCI:0:2:0"
    Option      "MonitorLayout" "CRT,LFP"
    Screen      1
EndSection
Section "Device"
    Identifier  "I855GM-1.TV"
    Driver      "i810"
    BusID       "PCI:0:2:0"
    Option      "MonitorLayout" "TV,LFP"
    Screen      1
EndSection

Section "Monitor"
    Identifier  "Default"
    HorizSync   56-65
    Option      "DPMS"
EndSection
Section "Monitor"
    Identifier  "Internal"
    HorizSync   56-65
    Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796
    DisplaySize 305 227
    Option      "DPMS"
EndSection
Section "Monitor"
    Identifier  "L1710B"
    HorizSync   56-69
    Modeline    "1280x1024@69" 140.00 1280 1312 1840 1872 1024 1044 1056 1076
    Option      "DPMS"
EndSection
Section "Monitor"
    Identifier  "TV"
    Modeline "800x600"   50.00   800  800  800  800   600  600  600  600
EndSection
Section "Screen"
    Identifier  "Primary Screen"
    Device      "I855GM-0"
    Monitor     "Internal"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1024x768"
    EndSubSection
EndSection
Section "Screen"
    Identifier  "Other Screen"
    Device      "I855GM-1"
    Monitor     "L1710B"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1280x1024"
    EndSubSection
EndSection
Section "Screen"
    Identifier  "TV Screen"
    Device      "I855GM-1.TV"
    Monitor     "TV"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "800x600"
    EndSubSection
EndSection
Section "ServerLayout"
    Identifier  "Work"
    InputDevice "Generic Keyboard"
    InputDevice "Touchpad" "CorePointer"
    InputDevice "USB-Mouse" "SendCoreEvents"

    Screen      "Primary Screen"
    Screen      "Other Screen" Above "Primary Screen"
    Option      "Clone" "off"
    Option      "Xinerama" "on"
EndSection

```

For usage of TV output I've changed the "Other Screen" in ServerLayout to "TV Screen"

---

### Post by André on 2005-03-08
Hi guys,

could someone please report if the settings worked for you?

Greetz and thanks
André

---

### Post by [S2] on 2005-03-13
[QUOTE=dodok1]I have Intel 855GM on my Toshiba A50 and using both displays. I've tried also the TV Out and it works also (but with wide black border around and I haven't played with it anymore).[/QUOTE]


Lucky you. I still get a black screen on the TV, and X fails complaining that no Screen is found if I switch to TV-OUT.

---

### Post by siDDis on 2005-03-16
Im also interested in this since Im using same videocard

---

### Post by thread on 2005-05-09
Yep, mine is an "Intel Extreme Graphics" using the i810 driver as well. It seems to think it's working. My virtual desktop is obviously larger as I can drag windows to the other screen (should be the tv over s video).

BUT, the TV is black, and according to the logs, it's only trying to be 640x480 when it should be 800x600. My x log and xorg.conf are available here:

[http://lynnode.ath.cx/~thread/files/Xorg.0.log](http://lynnode.ath.cx/~thread/files/Xorg.0.log)
[http://lynnode.ath.cx/~thread/files/xorg.conf](http://lynnode.ath.cx/~thread/files/xorg.conf)

---

### Post by dgray on 2006-08-29
I know this is a long time ago but did you get an answer?  I have a D505 notebook and want to use S-video lead to show slideshow on TV.  Any luck?

---

### Post by freddan on 2006-09-03
I'm afraid that I haven't got any solution on this. I have been searching all over to find a solution but without success... :(   Please let me know if you find anything...

rgds.
/Freddan

---

### Post by raintheory on 2006-09-13
I have a Toshiba Satellite P15 S420, and the S-Video doesn't work in Ubuntu...  Works in XP just fine, been having to dual-boot to watch movies over S-Video..

---

### Post by motin on 2006-09-17
Have you tried [http://sourceforge.net/projects/i855crt](http://sourceforge.net/projects/i855crt) ? it may or not be useful...

---

### Post by daniel2501 on 2006-12-24
Try adding these two lines two your Device section:
[I]        Option      "MonitorLayout" "TV,LFP"
        Option      "Clone" "true"
[/I]

You'll likely need to temporarily change your screen resolution to 1024x768 so that the display with fit on the TV screen. I use krandrtray to do that.

---

### Post by Jroller90 on 2007-02-06
I believe all you have to do is: go to your control panel, open your graphics properties, and you might see something along the lines of display devices, and if your computer is plugged into the the output source it should be in the list.

---

### Post by flygin on 2007-04-03
Xorg.0.log.old:(II) I810(0): Display Presence: TV: attached: FALSE, encoder: TRUE



I tried to make TV out work ( on  a laser ovil @!) with a intel 855 card. Xorg works but it says that the ext. monitor is not attached. 

There is a cable that changes ** Svideo out ** to **composite.** 

tried plenty of different settings  (w/ plenty of crashes)


what to do?? cable broken??

---

### Post by has981 on 2007-04-30
I also need to do the same to capture video on a camcorder... anybody got it working yet!!
Thnx

---

### Post by derekguy on 2007-05-13
Has anyone had any insight as to S-Video? I am using an 915GM/GMS/910GML Express Graphics Controller and am having issues enabling video out.

I have tried several threads on this forum so any extra help would be great (to avoid those dreaded X crashes)

---

### Post by Tethtibis on 2007-06-27
yeah, press FN and F8.

---

### Post by otakuj462 on 2007-06-27
I recently asked about this for my Toshiba Satellite 1130 on the Xorg list. Here's what they said:

> 
> Hello, I was wondering if anyone could provide me with information on
> enabling the S-Video out port on my Toshiba Satellite 1130. It has
> the Intel 852GSM graphics chipset, and I believe it currently uses
> the i810 driver. It is currently running Ubuntu 7.04.
> If anyone can offer any guidance, I would greatly appreciate it if
> you would let me know.
> Thanks.

TV-out is currently not supported on pre-i915 chips, although the Intel
folks say that this is something that someone with the skill and time
could fix, as most of the TV-out chips paired with i830-generation
graphics hardware have publicly-available data sheets.

Andrew


It would therefore be *very* interesting if someone managed to get this to work.

Jake

---

### Post by hmsf on 2007-09-03
I was having problems enabling S-video out on my Satellite A45 (i855), with no success. But I just changed the display resolution from 1024x768 to 800x600, then hit Fn+F5, and it worked! Of course it's not the perfect situation (having to manually change the resolution), but at least it's working now...

---

### Post by wieman01 on 2007-09-04
I found a nice & easy solution here:

[http://ubuntuforums.org/showthread.php?t=411674]("http://ubuntuforums.org/showthread.php?t=411674")

When I connect an external device the PC detects it immediately and shows the screen in the right resolution and color. There is no need to temper with any text files, etc. Just follow the HOWTO and you are ready to go.

---

### Post by airtonix on 2007-11-23
every laptop that i've used ubuntu with has had the [function-key + f8] as an  hardware-output-selector-switch  for the video card.

each of em also ran compiz by default after a fresh live cd install.
whereupon i press fn+f8 and voila, laptop screen turns off, and tv screen turns on.

helps that my tv is lcd, with vga input. aswell as the rest, hdmi, scart, coaxial, rca, component.

---

### Post by kpkeerthi on 2007-11-23
I just wire-up my laptop and TV and Applications -> System Tools -> Nvidia Settings -> Detect Displays. Have not made any changes to xorg.conf but you need nvidia for this to work.

---

### Post by nacho-wan on 2008-04-07
HI there. I have been playing around with this issue for a couple of hours and I think I gotten it nailed down.

First let me tell you that I'm running Gutsy Gibbon on a Dell Inspiron 1525 with Intel X3100 Graphic accelerator chip running the intel driver. After several hours of crashing down xorg.conf and crawling around xrandr I managed to get s-video working.

Open xorg.conf with Gedit and sudo privileges (at terminal type sudo gedit /etc/X11/xorg.conf) and look for the device stanza. Add the following lines at the end:

	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"

So your device stanza should look like this:

```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection
```

Restart your system (or if you are of the bold ones, log out of your session and press ctrl+alt+bcksp to kill X) and log back again. If your tv-set is plugged via S-vdeo you should see your desktop on the tv screen.

Hope this helps somebody.

Best regards,

-Ignacio

---

### Post by BUGabundo on 2008-04-07
Thanks.

Just yesterday I did a few test on my intel 855 on hardy and couldnt make it work.

I'll try again with your tip, and report back.

---

### Post by BUGabundo on 2008-04-11
> **nacho-wan said:**
> HI there. I have been playing around with this issue for a couple of hours and I think I gotten it nailed down.

First let me tell you that I'm running Gutsy Gibbon on a Dell Inspiron 1525 with Intel X3100 Graphic accelerator chip running the intel driver. After several hours of crashing down xorg.conf and crawling around xrandr I managed to get s-video working.

Open xorg.conf with Gedit and sudo privileges (at terminal type sudo gedit /etc/X11/xorg.conf) and look for the device stanza. Add the following lines at the end:

	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"

So your device stanza should look like this:

```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection
```

Restart your system (or if you are of the bold ones, log out of your session and press ctrl+alt+bcksp to kill X) and log back again. If your tv-set is plugged via S-vdeo you should see your desktop on the tv screen.

Hope this helps somebody.

Best regards,

-Ignacio

Tried it, and it didnt work on my intel 855

It did work quite well on Windows and Intel drivers.
But I no longer have windows on it.

---

### Post by flightless bird on 2008-04-15
> **nacho-wan said:**
> HI there. I have been playing around with this issue for a couple of hours and I think I gotten it nailed down.

First let me tell you that I'm running Gutsy Gibbon on a Dell Inspiron 1525 with Intel X3100 Graphic accelerator chip running the intel driver. After several hours of crashing down xorg.conf and crawling around xrandr I managed to get s-video working.

Open xorg.conf with Gedit and sudo privileges (at terminal type sudo gedit /etc/X11/xorg.conf) and look for the device stanza. Add the following lines at the end:

	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"

So your device stanza should look like this:

```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection
```

Restart your system (or if you are of the bold ones, log out of your session and press ctrl+alt+bcksp to kill X) and log back again. If your tv-set is plugged via S-vdeo you should see your desktop on the tv screen.

Hope this helps somebody.

Best regards,

-Ignacio

I tried this and while I finally got something to show on the tv but there were two side effects:
1) The main screen (laptop) was oddly deformed, as though parts of the desktop believed the resolution was maybe 2/3 of its proper size while the rest (compiz, window management, mouse cursor) was able to use the whole screen area. This was corrected on restart with the svideo cable unplugged
2) the tv display was terrible - the colours were off and the refresh rate seemed wrong

any ideas on how to correct this would be appreciated

output of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

relevant section of xorg.conf
```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

```

Cheers

---

### Post by lbig on 2008-04-28
> **flightless bird said:**
> I tried this and while I finally got something to show on the tv but there were two side effects:
1) The main screen (laptop) was oddly deformed, as though parts of the desktop believed the resolution was maybe 2/3 of its proper size while the rest (compiz, window management, mouse cursor) was able to use the whole screen area. This was corrected on restart with the svideo cable unplugged
2) the tv display was terrible - the colours were off and the refresh rate seemed wrong

any ideas on how to correct this would be appreciated

output of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

relevant section of xorg.conf
```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

```

Cheers

The same thing happened to me. I'm also in a Dell ispiron 1525

---

### Post by kaziklcd on 2008-04-30
Same problem with Acer Extensa 5220. View of tv is black and white. I think its matter of TV format (PAL or NTSC), should be set in Xorg but i don't know where?

---

### Post by wieman01 on 2008-05-01
I find this thread quite useful:

[http://ubuntuforums.org/showthread.php?t=411674]("http://ubuntuforums.org/showthread.php?t=411674")

---

### Post by flightless bird on 2008-05-01
> **kaziklcd said:**
> Same problem with Acer Extensa 5220. View of tv is black and white. I think its matter of TV format (PAL or NTSC), should be set in Xorg but i don't know where?
I think that makes sense - it certainly looks like a PAL issue.

---

### Post by kaziklcd on 2008-05-04
That is what I thud [http://www.intel.com/support/graphics/sb/CS-006338.htm](http://www.intel.com/support/graphics/sb/CS-006338.htm) but no idea how to set up in xorg.conf :(

Waiting for help :D

---

### Post by Valir on 2008-05-06
"Howto enable S-Video
Hi everybody,
How can I enable S-Video Out on DELL Latitude d505 (Intel 82852/855GM).
It's working on XP.
I want to watch DIVX on my TV."

Hi, I have the same comp Latitude and chipset as Goran in the initial post. I have tried to enable the crt and using i810switch as in a post here, but it does not work. Anyone any luck or ideas?

best regards

---

### Post by kaziklcd on 2008-05-07
Got it!!!

```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "true"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
        Option "TV_FORMAT" "PAL"

EndSection
```

Available tv formats follow ```
man intel
``` is ```
 TV_FORMAT - output standard

       This property allows you to control the output standard used on your TV
       output  port.   You can select between NTSC-M, NTSC-443, NTSC-J, PAL-M,
       PAL-N, and PAL.

```

---

### Post by mindracer on 2008-05-10
I have the same problem with i965GM X3100 intel, will the solution in the last post work with it?

---

### Post by mindracer on 2008-05-11
I submitted a bug report to ubuntu about this, if you have anything to contribute please do, you can use my bug report as a reference.  Here's the link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/229157](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/229157)

---

### Post by kaziklcd on 2008-05-20
> **mindracer said:**
> I have the same problem with i965GM X3100 intel, will the solution in the last post work with it?

Yes :D:KS

---

### Post by RamR on 2008-05-26
kaziklcd, can you please walk me through what you did to get this working?  This has been the only thing I have had trouble with.  Had it working for a bit but no luck now.  If you could help I would owe you.

---

### Post by Valir on 2008-05-29
Hi, 

I tried Kaziklcd's advice with no luck. There is simply nothing on the TV screen as if no signal. I have actually not tested the s-video in xp environment so I don't know where the problem is, is there a way of knowing whether there is coming any signal? 

Are there any typos or uppercases in Kaziklcd's advice that might not be working. 

By the way I am in the US so I used TV_FORMAT "NTSC-M"

best of luck, 



"Howto enable S-Video
Hi everybody,
How can I enable S-Video Out on DELL Latitude d505 (Intel 82852/855GM).
It's working on XP.
I want to watch DIVX on my TV."

Hi, I have the same comp Latitude and chipset as Goran in the initial post. I have tried to enable the crt and using i810switch as in a post here, but it does not work. Anyone any luck or ideas?

best regards

---

### Post by kaziklcd on 2008-06-08
RamR and Valir. First of all You should properly configure Your card with proper driver. I'm using intel driver so everything is in ```
man intel
```. TV section of manual said:
```
"TV
       Integrated TV output.  Available properties include:

       BOTTOM, RIGHT, TOP, LEFT - margins

       Adjusting these properties allows you to control the placement of  your
       TV output buffer on the screen.

       TV_FORMAT - output standard

       This property allows you to control the output standard used on your TV
       output  port.   You can select between NTSC-M, NTSC-443, NTSC-J, PAL-M,
       PAL-N, and PAL."
```
Btw, im using S-video to euro cable. What is Yours?[HTML][/HTML]

---

### Post by Valir on 2008-06-09
Hi Kaziklcd (and others), 

I added the 

```
Option "TV_FORMAT" "NTSC-M" 
``` to the xorg

I am using the same driver as you so man intel says the same. I am using NTSC because I am in the US, and even if I would use PAL there would be something coming on the tv but in a distorted fashion. I am getting nothing.

My cable? I am not sure what a euro cable is. I am using a cable that comes with two audio rca plugs and one svideo plug (it has four pins). Should there be a specific cable?

best,

---

### Post by ResumeMan on 2008-06-28
I'm struggling with this as well. I have a Toshiba A45 laptop, and have been trying to figure out how to use the S-video. I dual boot, and it works fine in XP, but pushing the usual fn-F5 just makes the TV flicker a little.

I tried the xorg edits specified by Kaziklcd, changing the format to the American standard. Still no luck.

I'm wondering about this from upthread:

> > Hello, I was wondering if anyone could provide me with information on
> enabling the S-Video out port on my Toshiba Satellite 1130. It has
> the Intel 852GSM graphics chipset, and I believe it currently uses
> the i810 driver. It is currently running Ubuntu 7.04.
> If anyone can offer any guidance, I would greatly appreciate it if
> you would let me know.
> Thanks

TV-out is currently not supported on pre-i915 chips, although the Intel
folks say that this is something that someone with the skill and time
could fix, as most of the TV-out chips paired with i830-generation
graphics hardware have publicly-available data sheets.

My display is 82852/855GM. Does anyone know if this is supported now? That could be the problem right there.

In other details, I'm running Gutsy and I think the driver is just called "intel."

Any help appreciated...!

---

