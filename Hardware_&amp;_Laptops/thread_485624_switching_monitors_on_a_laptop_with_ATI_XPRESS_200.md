---
title: "switching monitors on a laptop with ATI XPRESS 200"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by andrky on 2007-06-27
Hello,

I have a Fujitsu-Siemens S2110 laptop with
> 
~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

on board.

I have a dock-statition and a LG L1971HR Flat Panel attached to it.
Finally I have the Ubuntu 7.04 fresh install (everything set to default)

So I have an internal display with maximum (default) resolution of 1024x768@60Hz and an external display with maximum(default) of 1280x1024@75

I've been struggling for a couple of days to make my dual monitor conf work as I wish it to.

And I don't wish for anything extraordinary, just a _default_ **WinXP behaivor**, namely: after I press the [Fn]+F10 combination, output should be switched from internal to external screen and the resolution would be changed to match that of the external screen. When I press the [Fn]+F10 again the ouput should be switched back to the internal screen and the resolution to match the one being default there.

As simple as that! 

Now the story.

Right after installing the ubuntu I have a "vesa" dirver in the "Device" section in xorg.conf

> Section "Device"
	Identifier	"ATI Xpress 200"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection


And at this point the [Fn]+F10 **does switch the monitors**. But  as I understand it is impossible to set the resolution to 1280x1024 after I switch to the external screen.

> ~$ xrandr 
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 382mm x 300mm )  *75  
 1    800 x 600    ( 382mm x 300mm )   73  
 2    640 x 480    ( 382mm x 300mm )   73  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none


Ok so I've installed the fglrx driver (xorg-driver-fglrx). But right after I installed it, the [Fn]+F10 stopped working!! From now on I can only enable-disable monitors by 
aticonfig --enable-monitor crt1 or lvds (or something...)  And I believe X must be restarted after this setting's changed to take effect.

And this is not so handy, as I have to dock/undock my laptop at least twice a day. And I would really like it to switch the easy way.

Can anyone advise a good solution to this? Maybe the ati driver could be configured to support this but just I couldn't figure out how exactly.

ps. as a windows user I am totally frustrated  by the way the display setup is done in linux... :)

---

### Post by nphx on 2007-07-02
A number of function keys stop working with the fglrx drivers. It's just a buggy driver, I'm still waiting for ATI to release their new open source drivers I'm hearing about.

---

