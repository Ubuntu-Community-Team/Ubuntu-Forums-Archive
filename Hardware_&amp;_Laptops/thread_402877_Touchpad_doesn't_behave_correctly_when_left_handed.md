---
title: "Touchpad doesn't behave correctly when left handed"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by amitst on 2007-04-06
Hi,

I am using Ubuntu 6.10 on my laptop. The touchpad works correctly if the mouse is configured right handed. If I switch it to left handed, then the tap on the touch pad simulates a right click (actually a left click in case of a left handed mouse). Do I have to do any additional settings to make it behave correctly?

Thanks,
Amit

---

### Post by strabes on 2007-04-06
Here's a howto for synaptics touchpads. [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

I believe the options you would be interested in are 

Option "TapButton1"     "1"
Option "TapButton2"     "2"

---

### Post by amitst on 2007-07-27
Hi, 

I finally dared to change my xorgs.conf file (I was afraid my system would crash)

The following options are partially working (which is reverse of you had suggested),
Option "TapButton1" "2"
Option "TapButton2" "1"

However, tapping is working only in the client area of a window. It doesn't work on the toolbar and also not on the Ubuntu dropdown menus. Works properly on the desktop icons.

With the default setting, tapping operation works perfectly (though with right handed mouse)

Any suggestions?

---

