---
title: "[SOLVED] X doesn't keep WSXGA+ resolution when restarting (8800GT+Samsung 2232BW)"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by phan on 2008-02-07
I just made a clean install of Ubuntu Gubsy Gibbon (7.10) with the alternate CD and followed the instructions found on another thread to install the last NVidia drivers for my 8800GT.

It works ok.
I get into GNOME and see that X use the Plug'n'Play monitor driver in 1600x1024.

Native resolution of the 2232BX is 1680x1050 so I go into Gnome's menu for display driver and videocard driver, checks the widescreen option in the Plug'n'Play driver window and selects 1680x1050 resolution.
Screen turns black then image comes back and I confirm that I really want to keep this resolution.
At this point, everything's ok, I'm in 1680x1050 and the image is much better.

The problem is : if I restart X (because I unlog or reboot the computer or explicitly restarts it with CTRL+ALT+BACKSPACE), the 1680x1050 resolution is gone and I'm back in 1600x1024.

I checked Xorg's log /var/lov/Xorg.0.log, it says 
```
(WW) NVIDIA(0): No valide mode for "1680x1050@60"; removing.
```

I tried with monitor driver "LCD flatpanel 1680x1050", it is the same.
I edited xorg.conf and commented every ModeLine but 1680x1050 for both drivers, it has no effect. The mode is rejected, X switches to mode "nvidia-auto-select" (that what the log says) and I get back to 1600x1024.

I'm pretty sure I can get the 1680x1050 resolution to work since I can switch to it in Gnome.
I think the problem is the ModeLine for 1680x1050 which is not exactly what fits the 2232BW.

Does anyone know the correct modeline ?

I googled a little and found out in Xorg's documentation that one can found out the correct modeline from the EDDI informations log in Xorg.0.log. Unfortunatly, I don't have any EDDI information in the log.

So, here's where I am.
The problem is not solved but I'll try the following:
[LIST]
[*]find a tool to get the EDDI information from my monitor
[*]see if I can find some log for the NVidia driver which obviously knows how to correctly get into 1680x1050
[/LIST]

Thanks to anyone who can help.

I'll keep you guys posted if I solves the problem.

---

### Post by phan on 2008-02-08
First of all, I talked of EDDI in my previous post. I really meant EDID.

So, I installed read-edid package with synaptic and tried both get-edid and parse-edid commands.
The first command says the "VBE call failed" so retrieved EDID information are not to be trusted (actually they are unreadable crap) and the second command just hangs. Maybe I don't know how to use it.
Conclusion, this leads nowhere.

I googled a little more and found [The XFree86 Modeline Generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl"). I used it to generate a few modelines at various refresh rates in 1680x1050.
I also found the specific Horisync and vertrefresh of the 2232BW (I think) in the user manual on the driver CD. So I wrote a new section "monitor" specific to the 2232BW.

```
Section "Monitor"
	Identifier	"Samsung"
	Vendorname	"Samsung"
	Modelname	"2232BW"
	Horizsync	31-81
	Vertrefresh	56.0 - 75.0
  modeline "1680x1050@50" 121.68 1680 1712 2168 2200 1050 1072 1081 1103 -hsync +vsync
  modeline "1680x1050@51" 124.78 1680 1712 2184 2216 1050 1072 1081 1103 -hsync +vsync
  modeline "1680x1050@56" 140.76 1680 1712 2240 2272 1050 1071 1081 1103 -hsync +vsync
  modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -hsync +vsync
	Gamma	1.0
EndSection
```

I checked Xorg.0.log, only mode "1680x1050@56" is validated (which is an improvement):
```

(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050@56"
(**) NVIDIA(0): Virtual screen size configured to be 1680 x 1050
```
and a few lines below (after some unreadable resource range listing):
```
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1680x1050@56"
```
but at the end of the log, there is :
```
(II) NVIDIA(0): Setting mode "1600x1024"
```

I'm quite lost here. It looks like somehow X gets back (or is sent back) to 1600x1024 at the end. Maybe gnome is switching back to lower resolution... any idea ?

---

### Post by phan on 2008-02-08
> **phan said:**
> 
but at the end of the log, there is :
```
(II) NVIDIA(0): Setting mode "1600x1024"
```

I've just checked.
When I'm on the login screen, the log does not yet contain the line. So that confirms what I was seeing, the login screen is actually in 1680x1050.

---

### Post by phan on 2008-02-08
> **phan said:**
> 
but at the end of the log, there is :
```
(II) NVIDIA(0): Setting mode "1600x1024"
```

I've just checked.
When I'm on the login screen, the log does not yet contain the line. So that confirms what I was seeing, the login screen is actually in 1680x1050.

This confirms also what I suspected. The fact I log in makes X switch back to 1600x1024.
I checked Gnome manual a little, I didn't see where the resolution can be specified for the session, if it can be.

Any insight ?

Thanks in advance to anyone who read the thread but me and who can help.

---

### Post by phan on 2008-02-08
Just when I was about to post ni the Display Manager forum, I found this [thread]("http://ubuntuforums.org/showthread.php?p=1048370#post1048370") (the feature presenting thread after you've typed the title of the message is very cool and useful !).

I just says there is a config file where gnome stores the screen resolution to use during the session (just what I was looking for !).
The path to the config file is not correct but It showed me the way.
The correct path is:
```
~/.gconf/desktop/gnome/screen/default/0/%gconf.xml
```

I edited it and changed the information to the right resolution and refresh rate, saved, restarted X and logged in. WSXGA+ baby !

Here is the content of the new %gconf.xml :
```
<?xml version="1.0"?>
<gconf>
        <entry name="rate" mtime="1202330703" type="int" value="56">
        </entry>
        <entry name="resolution" mtime="1202330703" type="string">
                <stringvalue>1680x1050</stringvalue>
        </entry>
</gconf>
```

I hope this thread will be helpfull to someone as other threads in ubuntu forums helped me.

---

