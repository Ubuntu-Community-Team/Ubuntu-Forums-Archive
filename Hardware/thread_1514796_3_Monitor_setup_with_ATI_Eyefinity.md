---
title: "3 Monitor setup with ATI Eyefinity?"
date: 2010-06-21
forum: Hardware
---

### Post by Excizted on 2010-06-21
Hello,

I've used dual monitor setup for many years now, but I'm just about to invest in an extra monitor, to increase my productivity - I just feel two monitors is too little space now - even with important Workspace functionality Ubuntu has.

As a sidenote, I have to buy a new graphics card, and I'm planning to get ATI Radeon 5870.

I heard some people are **having troubles** with ATI Eyefinity, somehow only able to use two monitors because of the *drivers*?

Not much information available, so I'd like to know if I'm going to be _able to use the three monitors at all_?
 - Could someone point me in the right direction, on what (if any) I have to do, to get this setup going?

Ps. I'm not looking for comments on which monitors nor graphics card to use, exclusively the support in Ubuntu.

Thank you very much! :)

---

### Post by ogomoe on 2010-06-23
Hello Excizted,

I don't have a solution to running 3 monitors  from a 5870, but I might be able to pass on to you some more  information.  My setup is a 2GB Diamond Radeon HD 5970.  The 5970 has 2  DVI and 1 Mini Display Port connections.

I've only begun looking  for a solution, but before I knew  anything, I purchased Apple's MDP to DVI & MDP to VGA adapters.   In Windows 7, I was able to intermittently run 3 displays from the Apple  VGA adapter, but it would fail more times than for which I had patience.   Sometimes I had all three identical displays running, sometimes only the 2  DVI's, or 1 DVI and the MDP.  The MDP to DVI would only give me a  combination of any two monitors.  The same is true for Ubuntu Lucid and  Karmic.  I didn't bother trying with any older Ubuntu's.

From  what I've read, the ATI 5xxx series can't run 3 digital displays  without an "active" Mini Display Port adapter.

Please read this  from AMD: ```
[http://sites.amd.com/us/game/technology/eyefinity/Pages/faq.aspx](http://sites.amd.com/us/game/technology/eyefinity/Pages/faq.aspx)
```> **What  Operating Systems does ATI Eyefinity technology work with?**

 At present Windows® Vista and Windows® 7 support ATI Eyefinity  technology. There are plans for Linux support in an upcoming update to  ATI Catalyst&#8482; software. There is no support for Windows® XP.
> **What&#8217;s the difference between active DisplayPort dongles and passive  DisplayPort dongles?**

 Passive dongles use the DisplayPort connection to receive non-DP  signaling from the connector and they 'passively' adjust the signals to  be compliant with the connected monitor. Passive dongles are considered  legacy connections, not DisplayPort connections, therefore they do not  fulfill the DisplayPort connection requirement mentioned previously and  cannot be used to enable 3 or more displays. However, they offer an  affordable solution to connect legacy displays onto DisplayPort  connections. 
 Active dongles use true DisplayPort signaling to &#8216;actively&#8217; translate  and re-transmit the signals as the required outputs. Because they use  the true DisplayPort signaling, they are considered a DisplayPort  connection and meet the requirements to enable 3 or more displays.
 DisplayPort to DL-DVI dongles require an external power supply which  is usually through a separate USB connection (the USB connection must  meet the USB &#8216;high power&#8217; specification).
> **Where can I purchase the various active and passive DisplayPort  dongles and mini to standard DisplayPort adaptors and how much do they  cost?**

 With our ATI Eyefinity validation program, we have been able to  validate and list a number of business partners currently shipping  adaptors. This list will continue to be updated. Please see [www.amd.com/eyefinity]("http://www.amd.com/eyefinity") for more  information.The Diamond 5970 includes a Mini Display Port to HDMI adapter but that gave me the same result as the Apple adapters.  I haven't tried any other combinations of plugs or bought any active adapters.  As a work-around, I installed an extra 256MB Diamond Radeon HD 2400 Pro to get 4 screens in Windows 7, with the 5970 as my primary adapter.  But that brings about a whole new can of worms in Ubuntu as I can only get a 2-monitor spanned-desktop from the 5970 with a 2-monitor cloned TTY on the 2400.  When I switch with Ctrl-Alt-F1 (F2,F3,etc.), the Gnome desktop on the 5970 goes black and then I can enter text on the 2400's cloned TTY screens.  The 2400's screen is always displayed, but the cursor blinks only when I'm in the TTY.

---

### Post by Gtaylor on 2010-07-14
I've got an EyeFinity 6 5870, which is different from the EyeFinity 5870. 6 displayport ports instead of the mixture of DP, HDMI, etc.

I've not been able to find anything on what to expect from this card in Linux, but this might be better than the original EyeFinity 5870, assuming you're going to buy three displayport-capable monitors.

---

### Post by sirkuttin on 2010-07-22
> **ogomoe said:**
> Hello Excizted,

From  what I've read, the ATI 5xxx series can't run 3 digital displays  without an "active" Mini Display Port adapter.



This actually is dependent upon the resolution you are running on your displays. I have 3 monitors running albeit in windows 7 with a passive dongle.

You can passively send signals up to single link dvi resolution. I am running 3 19 inch monitors at 1920X1200 a piece. The passive dongle handles it just fine. 

Though I know most people will have 3 23 or 24 inch monitors so the point may be moot however still worth noting for the low medium budget oriented like myself.

I haven't tried this setup in linux yet. I am going to soon and i will let you know the results.

---

### Post by Gtaylor on 2010-07-22
Looks like the 5870 EyeFinity 6 is a no-go with 3xDisplayport monitors. A new driver should be out this monday which addresses this problem for good.

---

### Post by 0004tom on 2010-07-22
> **Gtaylor said:**
> Looks like the 5870 EyeFinity 6 is a no-go with 3xDisplayport monitors. A new driver should be out this monday which addresses this problem for good.

Nothing set in stone as of yet, as ATi are not releasing any news on fixes and features, other then the VLC GPU acceleration. Only rumours.

---

### Post by c360 on 2010-08-26
> **sirkuttin said:**
> This actually is dependent upon the resolution you are running on your displays. I have 3 monitors running albeit in windows 7 with a passive dongle.

You can passively send signals up to single link dvi resolution. I am running 3 19 inch monitors at 1920X1200 a piece. The passive dongle handles it just fine. 

Though I know most people will have 3 23 or 24 inch monitors so the point may be moot however still worth noting for the low medium budget oriented like myself.

I haven't tried this setup in linux yet. I am going to soon and i will let you know the results.

 I have tried this on Linux and Windows 7 x64  with driver release 10.8 with no results.  CCC continues to disable one of the displays.  From what I understand from ATI is that version 10.7+ is supposed to have EyeFinity enabled.  Did you have any success with your linux test?  Thanks!

---

### Post by Excizted on 2010-08-27
> **c360 said:**
> I have tried this on Linux and Windows 7 x64  with driver release 10.8 with no results.  CCC continues to disable one of the displays.  From what I understand from ATI is that version 10.7+ is supposed to have EyeFinity enabled.  Did you have any success with your linux test?  Thanks!

I gave up and am now running dual x screen each on an Nvidia graphics card.

---

### Post by 0004tom on 2010-08-27
Eyefinity with the 10.7 and 10.8 propriety drivers working here. Been using for the last month. Altho it isn't true eyefinity, only able to get it going with on main monitor and the other 2 monitors extending the desktop.

[http://i37.tinypic.com/vrd8xx.jpg](http://i37.tinypic.com/vrd8xx.jpg) <-- Expo

[http://www.youtube.com/watch?v=ha1j0iLpAjU](http://www.youtube.com/watch?v=ha1j0iLpAjU) <-- To show off the 3D Gaming.. Alpha 3 of 0ad

---

### Post by ogomoe on 2010-08-27
I'd also like to say that I've been able to use my third monitor with the 10.8 proprietary driver and an active mini display port to DVI adapter.  Two screens are on each of the 5970's DVI ports.  The third screen runs off an Accell B087B-003J on the mini display port.

It's not 'eyefinity', but I can stretch program windows across displays.

An annoyance is that most of the windows open on the left monitor.

---

### Post by 0004tom on 2010-08-28
> **ogomoe said:**
> An annoyance is that most of the windows open on the left monitor.

This was troubling me also, I just use the compiz Place Windows plugin to have it open windows where I want. 

This also happens with flash video, say i'm watching a youtube video on the middle screen, I click fullscreen it goes full screen on the left monitor.

---

### Post by javahollic on 2010-09-24
I have the 10.9 x86_64 driver in place, it wont work with 3 displays in 'extending the desktop' mode.  I have 2 DVI's and one central HDMI, can only get one of the DVI's to kick in, the second is always disabled. Grrrr.

---

### Post by 0004tom on 2010-09-24
> **javahollic said:**
>   I have 2 DVI's and one central HDMI, can only get one of the DVI's to kick in, the second is always disabled. Grrrr.

Your ports are the problem, one of the screens has to be connected by display port.

---

### Post by KaDeeKe on 2010-10-12
Well, I'm using Ubuntu 10.04, two 19" DVI monitors and one DELL 22" DP monitor and CC driver10.9 (have tried every version since 10.3), but one monitor is always disabled :(. Can you share your X configuration with us? I'll post mine later when I'm back at my PC at home.

3 monitors work fine in Win 7 ...

---

### Post by 0004tom on 2010-10-12
> **0004tom said:**
> Eyefinity with the 10.7 and 10.8 propriety drivers working here. Been using for the last month. Altho it isn't true eyefinity, only able to get it going with on main monitor and the other 2 monitors extending the desktop.

[http://i37.tinypic.com/vrd8xx.jpg](http://i37.tinypic.com/vrd8xx.jpg) <-- Expo

[http://www.youtube.com/watch?v=ha1j0iLpAjU](http://www.youtube.com/watch?v=ha1j0iLpAjU) <-- To show off the 3D Gaming.. Alpha 3 of 0ad

The comment abuot not being true eyefinity is down to the gnone panels, I get full eyefinity with lubuntu, using LXDE. 

My xorg config @ KaDeeKe

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "2560 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 1280
		Depth     24
	EndSubSection
EndSection
```

eyefinity has worked for me since ATi annouced support for it with ubuntu since 10.7. It's also working fine with the 10.10 beta drivers in meerkat's repos.

---

### Post by ogomoe on 2010-10-13
@KaDeeKe

I have three 1920x1080 Samsung LCD monitors connected to an ATI Radeon HD 5970.  Two monitors are connected to the DVI ports and the third monitor is connected to the mini display port, using the Accel *active* mini display port adapter.  I believe I'm still using the 10.8 proprietary AMD/ATI driver.    I'm using Ubuntu Lucid Lynx 10.04 AMD64.

Here is my xorg.conf:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 11"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 11"
    Option        "Rotate" "normal"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "3840 0"
    Option        "Rotate" "normal"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-DFP3" "0-DFP3"
    BusID       "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   5760 1920
        Depth     24
    EndSubSection
EndSection

```

---

### Post by Zavior on 2010-11-06
> **0004tom said:**
> The comment abuot not being true eyefinity is down to the gnone panels, I get full eyefinity with lubuntu, using LXDE. 

So when you say full eyefinity do you mean fullscreen applications automatically span all three monitors? That is the main thing I'm having difficulty with at the moment. If anyone has any pointers on how to get fullscreen things to span all three monitors the help would be much appreciated

I've had my Eyefinity setup for about 4 months now and have been using Windows because of the lack of support in linux. Now that it's semi supported I'm happily back in Ubuntu. Just for anyone's reference who might be looking for information this is my setup:
Two 5770s in CrossfireX
3 23" monitors: 2 DVI, 1 Sapphire DisplayPort to VGA adapter
ATI CCC 10.10 - Each monitor set to "multi-display." CrossfireX enabled for center monitor
Ubuntu 10.10

---

### Post by 0004tom on 2010-11-06
Sadly no, what I meant with "true eyefinity" was that the LXDE taskbar spanned all 3 monitors, unlike the gnome-panels, that only span 1.

---

### Post by ogomoe on 2010-11-07
For what it's worth...

The first image is a screenshot from fullscreen Hedgewars across three monitors.

The second image is a screenshot of my desktop.  In the desktop image, the gnome taskbars are on the center monitor.

---

### Post by 0004tom on 2010-11-07
Yes some apps will go fullscreen, but i believe it's only a hand full. Games like 0 A.D for example span all 3 screens. 

(some selfless promoting lol)

A little video I made on 0 A.D

[http://www.youtube.com/watch?v=ha1j0iLpAjU](http://www.youtube.com/watch?v=ha1j0iLpAjU)

---

### Post by Zavior on 2010-11-09
> Yes some apps will go fullscreen, but i believe it's only a hand full. Games like 0 A.D for example span all 3 screens.

Yes, it appears MPlayer will fullscreen to whatever monitor you have it on, whereas flash player defaults to the left on my setup :/. It's definitely usable and I'm glad I can use my monitors, but I really hope that one day the ATI drivers for linux are up to par with the Windows ones in this area. 

There are some advantages to the current implementation though. Like Compiz-Fusion desktop cube can do one cube per monitor which is nice. Also, you can easily full screen a window to a single monitor by hitting the maximize button or double clicking on the title bar. If you did that in a normal Eyefinity setup it would fill all three monitors (which is pretty useless for most windows like file or internet browsers).

---

### Post by 448191 on 2010-11-27
Hi,

This sounds a lot more promising than other threads on this subject.

Basically I now have 3 monitors on two Nvidia cards with Xinerama support. It works half decently (sometimes Xinerama messes up which monitor my mouse is clicking on, but that doesn't happen too often).

I would like to get go to a single card setup, and get rid of Xinerama (though with the same behaviour), EyeFinity seems the way to do that.

Some questions, requests for confirmation:

 - Which cards support EyeFinity and the needed driver, which card would you recommend?
 - Do you get three desktops with their own panels and do windows maximize to the screen their on only (not that a window will expand to all monitors that would be useless)?
 - I understand most applications will fullscreen to the monitor they're on only, correct?
 - Dragging windows to another monitor works?
 - What exactly is the Flash issue? Will it only play on a single monitor?

Thank you very much. If this works I will be very happy. :D

---

### Post by 448191 on 2010-11-27
Also, asuming this works like I hope it will, am I forced to get an expensive Dual-Link adapter like this: [http://kabeltje.com/accell-displayport-naar-dvid-dual-link-actieve-adapter-25cm-p-1628.html](http://kabeltje.com/accell-displayport-naar-dvid-dual-link-actieve-adapter-25cm-p-1628.html)

or is that just a waste of my money and will a single link like this work fine: [http://kabeltje.com/ultraav-mini-displayport-dvid-singlelink-actieve-adapter-p-2521.html](http://kabeltje.com/ultraav-mini-displayport-dvid-singlelink-actieve-adapter-p-2521.html)

My monitors are 2048x1152. Going by wikipedia, the max supported resolution by single link at 60Hz is 2.75, which is less than my 2.36, but the single link adapter description says it supports up to 1920x1200, which is 2.30, just a little less than I need. Hence my dilemma. Also the monitors appear to have come with Dual Link cables.

---

### Post by 0004tom on 2010-11-27
> **448191 said:**
> Which cards support EyeFinity and the needed driver, which card would you recommend?

Any of the 5xxx/6xxx series card that have a Displayport output. Support was introduced with the 10.7 catalsty driver, so any driver after this.

> **448191 said:**
> Do you get three desktops with their own panels and do windows maximize to the screen their on only (not that a window will expand to all monitors that would be useless)?

No. It is all one desktop, and the gnome panels will sit on the screen you set as the main monitor. This is down to a limitation in how xorg draws the screen? In LXDE the taskbar will span all 3 monitors, like how it would with a windows eyefinity setup.

> **448191 said:**
> I understand most applications will fullscreen to the monitor they're on only, correct?

Yes, but there are the odd application that will fullscreen all 3 monitors. for example A 0.D.

> **448191 said:**
> Dragging windows to another monitor works?

Yes.

> **448191 said:**
> What exactly is the Flash issue? Will it only play on a single monitor?

The problem with flash videos, like youtube, if you fullscreen the video it will always sit go fullscreen to the monitor on the far left. Again this is how xorg draws the "windows". Easy why to put it is like, you have 3 pieces of cloth, and you stitch them together to make one big piece. screen one would start at 0, 0 screen 2 starts for me at 1280, 0 and so forth.

Regards to the DP-DVI adaptors I can't really help on this, as all my monitors are VGA, and the VGA adapters are alot cheaper.

---

### Post by 448191 on 2010-11-27
> **0004tom said:**
> 
No. It is all one desktop, and the gnome panels will sit on the screen you set as the main monitor. This is down to a limitation in how xorg draws the screen? In LXDE the taskbar will span all 3 monitors, like how it would with a windows eyefinity setup.


Are you absolutely sure about this? It sound like other than this, the behaviour would be almost identical to using Xinerama.

Using Xinerama, it too will not stretch the panels to the other panels, but that is actually desired behaviour: you can right click on a panel on your main monitor to add a new panel, untick "expand" in the panel's props, drag it to the desired screen, tick "expand", voila, a panel on another screen. You can then do "Add to Panel", select "Window List". After you're finished every screen has it's own Window List that only shows the windows on the screen the panel is on.

You're saying that doesn't work when using Eyefinity?

Thanks so far btw.

---

### Post by 0004tom on 2010-11-27
Oh I misunderstood what you was asking I think, Yes you can add other panels to the other screens, but the default 2 will sit on the you main screen. If you see the attactment I've just added a panel to the screen on the right.

Sorry about the size, but 3 screens give a large screen space lol

---

### Post by 448191 on 2010-11-27
> **0004tom said:**
> Oh I misunderstood what you was asking I think, Yes you can add other panels to the other screens, but the default 2 will sit on the you main screen. If you see the attactment I've just added a panel to the screen on the right.

Sorry about the size, but 3 screens give a large screen space lol

Could you try adding a Window List and see if it jumps from the Window List on the middle screen to the one on the right screen when you drag a window?

Also, maximizing a window maximizes to the current screen only, right?

I expect it does, seems like this is standard X11 or Gnome behaviour when dealing with multiple screen, but just to make sure.

Thanks again.

---

### Post by 0004tom on 2010-11-27
Can answer yes to both of your questions. In the screen shot i attached in the last post chromium is maximized to the central screen and altho you can't see it real well, I have a maximized xchat on the left screen just rolled up.

---

### Post by 448191 on 2010-11-27
In that case, guess I'm off to buy an ATI card :)

Thanks.

---

### Post by tep200377 on 2010-12-21
Just wanted to say that Eyefinity worked out of the box when installing 10.10 (64) .. yay ;)

---

### Post by 448191 on 2011-04-13
Just wanted to give some feedback on this.

I have an ATI card with eyefinity for a while now, but to my disappointment 3 monitors STILL only works in combination with Xinerama. I was hoping to eliminate it because it eats processing power.

Also it has its own quirks. With the nvidia cards I sometimes had issues with window selection, that problem is gone. But the ATI card has issues with video display: a movie can suddenly go green and then only work on a single monitor. Also right now, the cursor is distorted on the middle screen. In addition an issue with the whole system hanging if your mouse hangs around the screen borders, did not go away. This is an issue with Xinerama on both setups.

---

### Post by 448191 on 2011-06-11
I am baffled. System was getting quirky so I did a fresh install.

To my astonishment I was able to set up 3 monitors WITHOUT Xinerama this time. I just selected "multi-monitor with x, x" for two monitors and it worked. I bought a card that supports 3x DVI monitors without an adapter, and it works flawlessly now (so far). If only I had found out sooner.

This is the generated xorg.conf, as you can see, NO Xinerama :):)

EDIT: Compiz works as well, not that I care much, but still.


```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "4096 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP5"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "2048 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP3" "0-DFP3"
	Option	    "Monitor-DFP5" "0-DFP5"
	Option	    "Monitor-DFP4" "0-DFP4"
	BusID       "PCI:4:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   6144 2048
		Depth     24
	EndSubSection
EndSection
```

---

### Post by b1oh4zard on 2011-09-07
Hi, Just wanted to ask wich card u used to get it working. 
This would help me a lot.

---

### Post by fcomstoc on 2011-09-10
Hey I saw this thread and had a question 

I have 2 ATI hd 6770 in CrossfireX and in 3 display Eyefinity 3 monitor setup in horizontal span (not 3 individual screens). I have the i5 2500k and a motherboard that supports all this stuff. I am currently running windows 7 which crashes when playing WOW (which is annoying considering all the money i spent on this system) I am thinking of switching to ubuntu instead of windows on this system but I am looking for information on running crossfireX and eyefinity ( 3840x1024 between 3 monitors with WOW)

thanks 

Frank

---

