---
title: "Help needed getting monitor information"
date: 2018-09-30
forum: Hardware
---

### Post by tomdkat on 2018-09-30
Hi!  I'm in the process of setting up a PC upgrade for myself and I now have a 24" Viewsonic monitor connected via HDMI.  I'm running Ubuntu 18.04.1 (64-bit).   I think I have an overscan problem and I was looking through Ubuntu settings to find the *model* number of the monitor.   The "Displays" section shows 'Viewsonic Corporation 23"' but I can't find the actual monitor model information anywhere.

How can I get the monitor model number from Ubuntu?

Thanks!

Peace...

---

### Post by Autodave on 2018-09-30
You need the model # off of that monitor: there are several Viewsonic 24" monitors.  Check the back or possibly under the stand.  Any numbers will / could be useful in identifying it.  Also, what video card are you running? Did you install a driver for it? If so, what one and where did you get it from?

---

### Post by oldfred on 2018-10-01
Does this show more info? You may have to install read-edid first.
sudo apt install read-edid
       Monitor EDID
sudo get-edid | parse-edid
[http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor) 
    
Mine just shows model, but lots of technical details.

---

### Post by tomdkat on 2018-10-01
> **Autodave said:**
> You need the model # off of that monitor: there are several Viewsonic 24" monitors.  Check the back or possibly under the stand.  Any numbers will / could be useful in identifying it.  Also, what video card are you running? Did you install a driver for it? If so, what one and where did you get it from?

Thanks for the reply!  Yes, I know I could look at the back of the monitor but I was looking for a way to get that information from within Ubuntu itself.   :)    I'm using a  RS880 [Radeon HD 4200] video adapter and I'm using the Ubuntu supplied driver.

Thanks!

Peace...

---

### Post by tomdkat on 2018-10-01
> **oldfred said:**
> Does this show more info? You may have to install read-edid first.
sudo apt install read-edid
       Monitor EDID
sudo get-edid | parse-edid
[http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor) 
    
Mine just shows model, but lots of technical details.

Thanks for the reply!  read-edid did the trick.   :)

> Section "Monitor"
	Identifier "VX2433wm"
	ModelName "VX2433wm"
	VendorName "VSC"
	# Monitor Manufactured week 32 of 2009
	# EDID version 1.3
	# Digital Display


With regard to the overscan issue, I found an article on another website that provided information on correcting the issue.  The monitor was set to "HDMI AV" mode, which applies overscan for some A/V video sources.  Switching to "HDMI PC" eliminated the overscan and I'm now in business.  :)

Peace...

---

