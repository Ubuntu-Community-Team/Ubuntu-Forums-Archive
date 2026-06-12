---
title: "ATI Mobility Radeon X1600 under Karmic !!!"
date: 2009-12-05
forum: Hardware
---

### Post by wahid on 2009-12-05
Hey everyone,

I have a Toshiba Satellite A100-153 Notebook with an ATI Mobility Radeon X1600 graphic card. Since I've made a clean installation of Karmic, my laptop can no more restore a session back from standby or hibernate, and I get a black screen, then I have to hard-poweroff my notebook in order to get it to work again!!!

I know that this ATI modell have compatibility problem with the XServer since Jaunty, but although under Jaunty and with the opensource driver "radeon" was not really critical like now! (hibernate worked out-of-the-box, and standby often). Here's my xorg.conf on Karmic, maybe it will have any indication:

```
Section "Monitor" 
	Identifier "Configured Monitor"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
#either XAA or EXA. "XAA" is the default and safe choice.
#The newer "EXA" should be faster than the default
	Option          "AccelMethod"		"XAA"	
#"EnablePageFlip" only works with accelmethod "XAA".It can give a performance boost though,
#if experiencing instabilities disable this option
        Option          "EnablePageFlip" "false"
#must match your lspci output
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"		"on"
	Option		"BusType" "PCI"
EndSection

Section "Screen" 
	Identifier	"Default Screen"
        Monitor		"Configured Monitor"
        Device		"Configured Video Device"
EndSection
```

I'm not sure if the malfunctioning of the stanby/hibernate related to the graphic  card, but anyway I'll be so glad if someone help me to detect the problem!

Thanks in Advance

---

