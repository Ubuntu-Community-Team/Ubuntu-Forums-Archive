---
title: "External beamer on laptop"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by Toufik on 2007-04-17
I have a laptop and needed to make a presentation. I spend a lot of time to find the solution to my problem:

**How to connect a beamer to a laptop?**

_The solution depends on your graphic card_

**_Intel cards (i810 driver)_**

[LIST=1]
[*]**modify you xorg.conf**
Maybe it is a good advice to make a backup before
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.beamer # Backup
sudo cp /etc/X11/xorg.conf.beamer /etc/X11/xorg.conf # Restore

```

```
sudo gedit /etc/X11/xorg.conf
```
find this part and add the three red lines
```

Section "Device"
        Identifier      "Intel"
        Driver          "i810"
[COLOR="Red"]        Option    "MonitorLayout" "CRT,LFP"
        Option    "Clone" "true"
        Option    "DevicePresence" "true"[/COLOR]
        BusID           "PCI:0:2:0"
EndSection

```
[*]**switch display**
Even if the beamer may work now, I recommend to install a program to easily switch from one display to another
```
sudo apt-get install i810switch
```
Now you can use
```
i810switch crt on
```
or
```
i810switch crt off
```
or to rotate between the different displays (useful for linking to a hotkey):
```
i810rotate
```
[*]**change resolution (optional)**
At this stage, the image may be awful (especially if you have a widescreen laptop). Try to change your resolution to something your beamer likes, for instance 1024x768 (or 800x600)
**System > Preferences > Screen resolution**

If you have no other resolution available, modify your xorg.conf in order to have something like this (my default resolution is 1280x800 **Use your own values !!!!**)
```

Section "Screen"
...
SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600"
        EndSubSection
EndSection

```
[/LIST]

**_Nvidia_**
nvidia with official nvidia drivers (thanks to Spartan.II.117)
Same as above but you have to add these lines to your xorg.conf
```

[COLOR="Red"]Option "TwinView" "1"
Option "UseDisplayDevice" "DFP, CRT"
Option "TwinViewOrientation" "Clone"
Option "UseEdidFreqs" "1"
Option "Metamodes" "DFP: 1024x768, CRT: 1024x768"   #edit these values to be the resolution for each screen
Option "SecondMonitorHorizSync" "31-82"                        #check your projector manual to see what frequencys it uses, these are the values from my CRT
Option "SecondMonitorVertRefresh" "56-76"[/COLOR] 
```

the i810switch command wil obviously not work!

**_ATI_**
No idea :)
If you know tell me!!

---

### Post by Spartan.II.117 on 2007-04-17
nvidia- with official nvidia drivers add 

```
Option "TwinView" "1"
Option "UseDisplayDevice" "DFP, CRT"
Option "TwinViewOrientation" "Clone"
Option "UseEdidFreqs" "1"
Option "Metamodes" "DFP: 1024x768, CRT: 1024x768" #edit these values to be the resolution for each screen
Option "SecondMonitorHorizSync" "31-82" #check your projector manual to cee what frequencys it uses, these are the values from my CRT
Option "SecondMonitorVertRefresh" "56-76"
```
to your xorg.conf (you can leave my notes out)

note: crt is any monitor/projector connected over a vga port DFP is anything conected over a dvi-i(i believe)

---

### Post by gdi2k on 2007-04-24
Toufik, 

I am looking to achieve this too. I followed your instructions, but i810rotate just returns: 
```
~$ i810rotate 
PCI id of i810 is not recognized.
PCI id of i810 is not recognized.
```

The relevant portion of my xorg.conf looks like this: 
```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
        Option    	"MonitorLayout" "CRT,LFP"
        Option    	"Clone" "true"
        Option    	"DevicePresence" "true"
	BusID		"PCI:0:2:0"
EndSection
```

And the relevant portion of lspci shows: 
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

Any ideas?

---

### Post by Toufik on 2007-05-02
It seems your graphic card (i945) is not recognised by i810switch: see the home page 
[http://www16.plala.or.jp/mano-a-mano/i810switch.html](http://www16.plala.or.jp/mano-a-mano/i810switch.html)

Contact that guy or you may also want to try to try his advice:
> If your chipset is not supported, it's not entirely hopeless. To test these chipsets, a couple of code modifications are necessary:

    * add a #define for the chipset's PCI ID (i810switch.c:64 or so)
    * add a line for the chip in the i810_chip function (new chips should probably be of type I830) (i810switch.c:97 or so)
    * recompile and try it out 

Nevertheless, the beamer should work even without i810switch! This program only allows for easy switching. If the beamer doesn't work, try to restart the graphic session (first logout then CTRL+ALT+BACKSPACE) or to boot with the beamer plugged.

---

### Post by jjordan on 2007-05-03
For the Americans in the audience:

Beamer = projector (not BMW)

-j

---

### Post by bimmerd00d on 2007-05-15
> **jjordan said:**
> For the Americans in the audience:

Beamer = projector (not BMW)

-j

I was sitting here saying "why would he want to connect his laptop to his car????  Until i read the thread, then i picked up on it..."ohhhh a projector!"

---

### Post by soro2005 on 2007-06-06
Now, the real stunner for the Windows and Mac audiences will be if you set it up not for clone mode, but for dualhead or big desktop. Then have some visual fireworks on the big screen, while you read from your own display. :-)

People with an Omnibook (is that what it's called?) or Toshiba laptop may want to look into this here: [http://omnibook.sourceforge.net/doku.php](http://omnibook.sourceforge.net/doku.php). On my Toshiba, I can use that to activate the Fn key shortcuts to switch monitors. I think that goes directly through Bios and hardware and does away with the need to edit xorg.conf. Of course, if you have your wide screen and want the external display to pick up a decent aspect ratio, you'll still have to configure the X-server. Plus, you might get a nasty flicker.

---

### Post by syko21 on 2007-06-06
I've found that if i hook up my laptop to any external monitor and restart X (ctrl+alt+bkspc) the new monitor works fine. Sloppy solution but it works.

PS> Using an Nvidia card and proprietary drivers.

---

### Post by wieman01 on 2007-07-25
Man, worked perfectly for me. Thanks for this howto, took me 10 minutes to get my projector working (800x600). Good job!

I am on Feisty.

---

### Post by Peacepunk on 2007-09-03
Hi community !

Indeed L can do better than W - My sub-vaio VGN-T17GP running U 6.06 will have a wide-across-all single display rather than the factory-defined clone mode. 

For people like me that doesn't feel like changing their OS every six months, refer to this thread:
[http://ubuntuforums.org/showthread.php?p=3088479#post3088479](http://ubuntuforums.org/showthread.php?p=3088479#post3088479)
if you are not running feisty. It's not much harder, uses Xinerama and is proven-tested under Enlightenment DR16 on 6.06. Eye-candy on a lightfoot.

I just built a new desktop with a nvidia 8600gts (twin DVI outputs) - 'guess I'll test & report to see if the method is applicable for desktops as well.

Thanks community !

---

### Post by wildpatel on 2007-09-08
Im also getting the 

PCI id of i810 is not recognized.

THey say to add a few new lines of code...where do i insert this and how do i go around doing thing..im really new to ubuntu..please help.

---

### Post by disposition on 2007-10-21
> **wildpatel said:**
> Im also getting the 

PCI id of i810 is not recognized.

THey say to add a few new lines of code...where do i insert this and how do i go around doing thing..im really new to ubuntu..please help.

Bump, same issue. i seem to remember getting it easily installed on Feisty, but with Gutsy I can't get it working.

---

### Post by timjohn7 on 2008-04-08
Thanks x 1000!  This ended an entire night of searching!  Can you elaborate on how to add this i810switch to a hotkey?

---

### Post by wieman01 on 2008-04-09
> **timjohn7 said:**
> Thanks x 1000!  This ended an entire night of searching!  Can you elaborate on how to add this i810switch to a hotkey?
You can't. Just connect the projector to your device and reboot should that be required. The hotkeys don't work.

---

