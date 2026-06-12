---
title: "Lenovo Notebook Issues: Touchpad (no 2-finger/Edge Scroll) &amp; Mouse (dies after 5 sec)"
date: 2015-04-12
forum: Hardware
---

### Post by stefan_03 on 2015-04-12
Hello,

I've got two issues concerning my input deivces:

1) mouse: after 5 seconds of inactivity it dies. I've tried those solutions [http://askubuntu.com/questions/141832/usb-mouse-sleeping-after-5-seconds-when-on-battery](http://askubuntu.com/questions/141832/usb-mouse-sleeping-after-5-seconds-when-on-battery) none of them worked. It may be a powertop issue, but it seems deactivated in the powertop options

2) touchpad: even severe, because I mostly use the touchpad. The touchpad options are gone in the system settings. I can only see the common mouse options. Two finger scrolling does not work at all. No idea how I can get it back. I've tried to remove and install the synaptics software, no success. The touchpad settings (two finger scrolling etc) are still there, when I look through the dconf editor... it seems like my touchpad isn't recognized as a touchpad anymore, just as an ordinary mouse :/

This is how it should look like, but the whole "touchpad" part is missing

[Click here to get the image]("http://ubuntuhandbook.org/wp-content/uploads/2013/07/touchpad-tapping.jpg")

BTW: I can see this in my cat /proc/bus/input/devices output

```
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input83
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3
```

But entering synclient VertEdgeScroll=1 shows me:

```
$ synclient VertEdgeScroll=1
Couldn't find synaptics properties. No synaptics driver loaded?
```

Any solutions?

Thanks!!

Stefan

---

### Post by stefan_03 on 2015-04-14
No ideas, how the synaptics driver can be loaded? :( 

I did purge and install the synaptics package multiple times, no changes yet!

---

