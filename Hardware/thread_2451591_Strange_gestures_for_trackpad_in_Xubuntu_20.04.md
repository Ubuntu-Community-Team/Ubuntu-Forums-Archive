---
title: "Strange gestures for trackpad in Xubuntu 20.04"
date: 2020-10-07
forum: Hardware
---

### Post by keyopen on 2020-10-07
Hello, in June I  installed Xubuntu 20.04 on a laptop and the trackpad works in a strange  way: it is as if it were divided in half and the **left** part works  correctly, while the **right** part works as if it were a large scroll bar  with other gestures  , such as opening links on other browser panels by clicking on them.
 Is it possible to **reduce** or eliminate the right part?  Has anyone encountered the same problem?

---

### Post by Holger_Gehrke on 2020-10-07
Not exactly that problem, but a recent update to my XUbuntu 18.04 switched my trackpad from the (old) synaptic-driver to libinput and I lost the ability to click by tapping on the pad (and the mouse setting applet lost all mention of various settings I could previously make for the pad). That's how I got more closely acquainted with the 'xinput' command. Use 'xinput -list' to get a list of devices, then 'xinput -list-props "device name or number"' (replacing "device name or number" with the name or number the previous command gave for your trackpad) to get a list of all properties for the device. With 'xinput -set-prop "device name or number" "property name or number" "property value" you can set things. For example 'xinput -set-prop 'ETPS/2 Elantech Touchpad' 'libinput Scroll Method Enabled' 0, 1, 0' will set my trackpad to use two-finger scrolling, while ''xinput -set-prop 'ETPS/2 Elantech Touchpad' 'libinput Scroll Method Enabled' 1, 0, 0' gives me side-scrolling. Your pad might have a setting for the width of the scroll-zone, or you could set it to a different scrolling method. Once you've found settings you like, you can put the call(s) to xinput into a shell script and set that to run at session start.

Holger

---

### Post by keyopen on 2020-10-09
> **Holger_Gehrke said:**
> Not exactly that problem, but a recent update to my XUbuntu 18.04 switched my trackpad from the (old) synaptic-driver to libinput and I lost the ability to click by tapping on the pad (and the mouse setting applet lost all mention of various settings I could previously make for the pad). That's how I got more closely acquainted with the 'xinput' command. Use 'xinput -list' to get a list of devices, then 'xinput -list-props "device name or number"' (replacing "device name or number" with the name or number the previous command gave for your trackpad) to get a list of all properties for the device. With 'xinput -set-prop "device name or number" "property name or number" "property value" you can set things. For example 'xinput -set-prop 'ETPS/2 Elantech Touchpad' 'libinput Scroll Method Enabled' 0, 1, 0' will set my trackpad to use two-finger scrolling, while ''xinput -set-prop 'ETPS/2 Elantech Touchpad' 'libinput Scroll Method Enabled' 1, 0, 0' gives me side-scrolling. Your pad might have a setting for the width of the scroll-zone, or you could set it to a different scrolling method. Once you've found settings you like, you can put the call(s) to xinput into a shell script and set that to run at session start.

Holger

Thank you for your suggestion. After red it I searched on the internet and I found this guide: [https://linuxhint.com/change_mouse_touchpad_settings_xinput_linux/](https://linuxhint.com/change_mouse_touchpad_settings_xinput_linux/) and the next references:
[https://www.mankier.com/4/libinput#Configuration_Details](https://www.mankier.com/4/libinput#Configuration_Details)
[http://manpages.ubuntu.com/manpages/focal/en/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/focal/en/man4/synaptics.4.html)

Now I'm trying to adjust my touchpad's edges but I think this configurations should be available in control panel / mouse options in a grapchic window so avery one can correct this strange, or new input mode, in simple way.

---

