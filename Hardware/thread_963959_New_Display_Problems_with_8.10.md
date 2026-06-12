---
title: "New Display Problems with 8.10"
date: 2008-10-30
forum: Hardware
---

### Post by sparrowkc on 2008-10-30
I have a 5 year old laptop that I want to update to 8.10.  I booted from the live cd, an I noticed that text and window borders have a fairly severe flicker problem.  I booted back off the hard drive to 8.04 and the problem went away.  I never changed anything related to the display in my old xorg.conf.  This computer has basic sis video, with no acceleration.  Whats happening?

Edit:
LSPCI
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by elwillow on 2008-10-30
I have the same issue.

I just did a clean install on my Acer laptop with a sis card (no acceleration)

lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

I can reload with the vesa driver by creating a simple xorg.conf and everything works fine except the 800x600 max resolution, otherwise there is no xorg.conf.

For more explaination, I've attached a screen shot, it's pretty bad (I think I'm going to have a seizure :(

---

### Post by sparrowkc on 2008-10-30
The problem doesn't seem to appear in screenshots.:lolflag:

---

### Post by lophie on 2008-10-30
what a coincidence? I was reading the same thing minutes ago and boom I see this topic.

the solution I found is for KUBUNTU but I thought mentioning the solution here may be in use for GNOME users.

the solution is simple. I just had to turn the RANDR monitor autochecking service. I dunno what is it in GNOME. but I doubt it is gonna be way different. Hope I helped.

---

### Post by sparrowkc on 2008-10-30
This makes me sad...  I was all excited for an upgrade!

---

### Post by sparrowkc on 2008-10-30
doublepost

---

### Post by sparrowkc on 2008-10-30
Found the fix!

Try 
```
sudo modprobe sisfb
```
in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.  

If that worked, then you can add sisfb to /etc/modules so that it will be loaded at startup.


:D:D:D:D:D:D

---

### Post by elwillow on 2008-10-30
> **sparrowkc said:**
> The problem doesn't seem to appear in screenshots.:lolflag:

thinking about it.... it can't... :roll:

anyway just to say that it's fine with a light theme. It will still be weird for every dark color, it adds some moving blue pixel.

---

### Post by elwillow on 2008-10-30
yep... I confirm the fix.
I had to reboot (ctrl+alt+backspace wasn't enough) but my glitches are gone!
thanks!

---

### Post by errummm on 2008-10-31
I've been having the same problem and raised it at [http://ubuntuforums.org/showthread.php?t=962308](http://ubuntuforums.org/showthread.php?t=962308), but I'm still a bit crap with the system maintenance stuff.

My attempt is CTRL-ALT-F1
log in
sudo modprobe sisfb
CTRL-ALT-F9
which doesn't work.

I'm not sure what to do next.

Could someone further newbify things for me?

---

### Post by Cristina Precioso on 2008-11-01
> **sparrowkc said:**
> Found the fix!

Try 
```
sudo modprobe sisfb
```
in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.  

If that worked, then you can add sisfb to /etc/modules so that it will be loaded at startup.


:D:D:D:D:D:D

Thank you! It worked here!

---

### Post by mgol on 2008-11-01
> **sparrowkc said:**
> 
Try 
```
sudo modprobe sisfb
```
in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.  


Unfortunately, it didn't help. I added sisfb to /etc/modules, restarted my computer and NOTHING changed. Still these screen problems make me crazy...

Can anybody help?

---

### Post by VicAlpha on 2008-11-02
> **mgol said:**
> Unfortunately, it didn't help. I added sisfb to /etc/modules, restarted my computer and NOTHING changed. Still these screen problems make me crazy...

Can anybody help?
i've added modprobe sisfb to both /etc/modules and /etc/rc.local just to be sure and it works for me.

---

### Post by mgol on 2008-11-02
> **VicAlpha said:**
> i've added modprobe sisfb to both /etc/modules and /etc/rc.local just to be sure and it works for me.

Now I did it also, I also added to my xorg.conf a
```

Section "Device"
	...
	Option "UseFBDev" "true"
EndSection

```
line, and still nothing changed. Switching back to vesa... :/

---

### Post by tuneable on 2008-11-02
Too bad! I can confirm it does **not** work for a d201GLY2 motherboard with sis662. The search for a solution [continues]("http://ubuntuforums.org/showthread.php?t=966450")

---

### Post by VicAlpha on 2008-11-02
> **mgol said:**
> Now I did it also, I also added to my xorg.conf a
```

Section "Device"
	...
	Option "UseFBDev" "true"
EndSection

```
line, and still nothing changed. Switching back to vesa... :/

Had the same problem yesterday night and solved it. edit the /etc/X11/xorg.conf with so that the driver is "sis"

example: 
> Section "Device"
Identifier "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
Driver "sis"
BusID "PCI:1:0:0"
EndSection

then I added and edited the Screen section with my laptop's resolution which is 1280x800:
> Section "Screen"
Identifier "Default Screen"
Device "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
Monitor "Belinea10170"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

I'm not done yet with configuring xorg.conf since there "flicker" when I scroll & other screen intensive apps.

---

### Post by woosie on 2008-11-02
Ignore this - I've sorted it.

The sisfb fix worked.

---

### Post by sparrowkc on 2008-11-03
Erum-
After you get back to your desktop, restart x with ctrl-alt-bkspc and log back in from the gdm. You can't just restart the whole computer, because that would unload the module.

---

### Post by cool_penguin on 2008-11-08
Worked great for me on my Acer Travelmate 2310 notebook which comes with a crappy SiS integrated graphics card. 

Now even the text that appears at shutdown seems to be high in resolution and sharp and the system now shuts down a lot faster.

sudo modprobe sisfb works great. 

I also added it to /etc/modules and I no longer get a blank GMD login screen. 

UBUNTU is great. 

Cheers,
Harry

---

### Post by StuartCarter on 2008-11-09
I am having this problem. When I run sudo modprobe sisfb I get the error message 

sisfb: Fatal error: Unable to reserve 128MB framebuffer memory
sisfb: Is there another framebuffer driver active?

My configuration is the same as VicAlpha.

---

### Post by Max Roswell on 2008-12-27
sudo modprobe sisfb doesn't seem to work for me.

Weirdly, though, if I open a virtual terminal, then hit ctrl+alt+del and reboot that way, my machine restarts with the display working properly (most times, not all).

This whole issue is easily the most frustrating thing I've encountered since I adopted *buntu.

---

### Post by greatst on 2008-12-31
unfortunately the

```
sudo modprobe sisfb
```

will NOT work for my case: I restart-X (Ctrl+Alt+Backspace) and ... I get a blank screen! :-(

Same think happens if I enter the sisfb module in the /etc/modules file and restart my computer! :-(

**_edit:_**
after a little bit more search I found that my laptop actualy uses SiS [M]760[GX] with a setup that does NOT support sisfb :-(

Good news: I used sisctrl utility that allows me to make better setups to my display :-)

All these thanks to info retrieved at: [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)

---

### Post by stotheg on 2009-02-21
> **sparrowkc said:**
> Found the fix!

Try 
```
sudo modprobe sisfb
```
in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.  

If that worked, then you can add sisfb to /etc/modules so that it will be loaded at startup.


:D:D:D:D:D:D

HI!

This is the first thing I have seen close to a fix for this issue.  Could you explain in detail how to do this?  (IE:  How to get a virtual terminal window, adding sisfb to /etc/modules, etc) I'm a rookie...

---

### Post by mgol on 2009-02-21
> **stotheg said:**
> HI!

This is the first thing I have seen close to a fix for this issue.  Could you explain in detail how to do this?  (IE:  How to get a virtual terminal window, adding sisfb to /etc/modules, etc) I'm a rookie...

Don't bother with that. It's hard and functions only till restart. The actual fix (that helped me) is very simple. Edit /etc/modules file:
```
gksu gedit /etc/modules
```
Add a line containing only sisfb in the new, last line. Then reboot (the whole computer, restarting just X server won't work). That's all.

---

### Post by Max Roswell on 2009-02-28
I'm still getting no joy on this issue.  sudo modprobe sisfb doesn't work, and neither does adding sisfb to /etc/modules.  Sometimes after about 3 cycles of sudo modprobe sisfb and restarting X and/or rebooting, it works, but most times not.

I realize that this SiS is a crappy video card, but it worked fine under 8.04, 7.10, 7.04 and so on.  What changed, why can't it be fixed, and what in the world can I do to, you know, actually be able to use this GD computer?

Hate to ask this...but is it likely that another distro avoids this problem?  I want to keep using Linux, but this is an absolutely unacceptable way to have to live.  I just want to get my work done and enjoy my Saturday, not reboot my computer a million times to try to get something to work that USED TO WORK on this same machine.

---

### Post by mgol on 2009-02-28
@ Max Roswell
If it's acceptable to You, You can return to Ubuntu 8.04. It's an LTS and will be supported till April 2011, far longer than Ubuntu 8.10. I use 8.04 and it works ok. I suppose I'll upgrade my computer till 2011, as in this year it would be 6 years old...

---

### Post by mluffman on 2009-03-03
Wow! After weeks of searching for an answer, I find this and it works! I have an Acer 3004WLMi with the SiS M760GX and this fix has solved the problem. Working with the Jaunty Alpha 5 Desktop CD.

---

### Post by GizmoTheGreen on 2009-03-04
Hi!
I also have this problem on a laptop with SiS graphics card, its an Acer, Aspire 5000.

ive tried sisfb in the /etc/modules
it wont help, it did once though! but it appears it was random luck becouse after a reboot it went back to glitchy colors :(

there has to be a better fix! :(

---

### Post by Max Roswell on 2009-03-08
Gizmo...I have the exact same machine.  If I find something that works, I'll let you know.

---

### Post by Max Roswell on 2009-03-10
Well, I now can say that the same problem exists under Fedora 10 (the new KDE 4 RC flavor).  I'm now wondering if this is being caused by KDE 4...that would seem to be to be the obvious similarity between this version of Fedora and the Kubuntu 8.10 that's screwed up for me, too.  I'm going to get my hands on a Kubuntu 8.04 CD and see if stepping back like that helps at all.

Just adding details as I find them in case they help someone figure out their own issues.

---

### Post by mgol on 2009-03-10
Beware that Kubuntu 8.04 is not LTS, which means its support ends in October 2009.

Kubuntu 8.10 uses KDE 4.1 and it seems that KDE only from 4.2 is really usable.

---

### Post by Max Roswell on 2009-03-10
I don't care when the support ends as long as the version actually WORKS!  My machine ran Kubuntu 8.04 just fine, so I think going back and standing pat will be OK.

---

### Post by mgol on 2009-03-10
You would probably care about it if support was supposed to be ended within, let's say, a month. ;)

I only wrote it to make sure You're aware about it. If You're OK about that, it's fine. :)

---

### Post by damien82 on 2009-07-27
well, just thought i'd mention that this worked on my aspire 5002 with jaunty installed, been putting off using ubuntu since 7.10 because of this problem but now it's gone, thank you so much OP

---

