---
title: "More touchpad issues"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by employeeno5 on 2007-11-12
I've thoroughly read a variety of touchpad problem threads  that have not helped so please hear me out.

First off, I'm running Gutsy 7.10 on a Dell Inspiron Laptop E1505.
My touch pad functions correctly.
It is far too sensitive though. The slightest brush of anything near it while typing causes a cursor jump. If I'm using it (instead on a USB mouse) it clicks constantly when I'm not really tapping.
I would like to adjust the sensitivity, or at least be able to turn it on and off reasonably easily.

I downloaded the "Touchpad" program that comes up if you do a search in the add/remove program section. It installed correctly to my preferences. It will not run however. It gives the following error message:

 > "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Ok. so. I went to me xorg.conf file and added an option and value to placate the error message. My file looks like this now:


```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option          "SHMConfig"             "true"
EndSection
```

When I try to run the program I get the same error.
So I decided to see what this XF86Config is. I'm not sure what it is, but when I did a search in the synaptic package manager it brought up dozens of files prefixed with xf86 and every single one of them was already installed.

I'm not sure where to go from here to make the touchpad preferences application work.

So, I installed the program QSynaptics to see if I would have better luck.
This also will not run. Again I am told that I need XF86Config. It also tells me that I need to install the synaptics driver which I don't quite understand because I thought it was installed and was what currently controlled my trackpad.

Any advice or ideas would be great. And again, I ultimately don't even need to get one of these two programs to work, I'll take almost any kind of fix to reduce the sensitivity of this thing.

Many many thanks for any help.

---

