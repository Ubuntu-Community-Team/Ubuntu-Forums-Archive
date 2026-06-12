---
title: "Multiple monitor setup bw a Thinkpad and a Thinkvision"
date: 2009-03-04
forum: Hardware
---

### Post by gourabbaksi on 2009-03-04
My office provides me with a Lenovo Thinkpad T400 and a 22" Thinkvision monitor. I have windows xp and ubunutu 8.10 configured for dual boot on the Thinkpad. Whenever I boot into Ubuntu, the desktop however does not get redirected to the Thinkvision monitor after attaching the Thinkpad to the docking station - which is not case when I use windows xp. It manages to detect the 22" display though but just wont shift. 

Do I need to make changes to the x-server config?
Could this be a gnome issue, since thats what I use?

Any help all ye Ubuntu Gods :)?

Thanks in advance..

---

### Post by gourabbaksi on 2009-03-04
Some info that might help..

This is the controller I have:
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller

aslan@narnia:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1152 x 1728
VGA connected (normal left inverted right x axis y axis)
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.0     60.0     59.9  
   720x400        70.1  
LVDS connected 1152x864+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-2 disconnected (normal left inverted right x axis y axis)

cat /etc/X11/xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1152 1728 
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

