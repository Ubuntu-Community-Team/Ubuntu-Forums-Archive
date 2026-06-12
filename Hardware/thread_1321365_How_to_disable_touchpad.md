---
title: "How to disable touchpad"
date: 2009-11-10
forum: Hardware
---

### Post by ledererster on 2009-11-10
I'm using Ubuntu 9.10 on a laptop. How do you disable the touchpad completely? I've been to the mouse options and saw the disable while typing and so forth. I have a mouse I use and hate the touchpad. How can I turn it off completely?

---

### Post by suibhne on 2009-11-10
try these instructions (good for netbook). 

Create a new plain text file, with the following content:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="info.product" string="SynPS/2 Synaptics TouchPad">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
<merge key="input.x11_driver" type="string">synaptics</merge>
</match>
</device>
<device>
<match key="info.linux.driver" string="psmouse">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>

and save it as /etc/hal/fdi/policy/shmconfig.fdi.

Then reboot, or restart X (right-alt - SysRq - k), and the touhpad will now be addressable. When you type, it will briefly disable to prevent accidental mousing.




Thats it

Courtesy of [here]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/")

---

### Post by chontler on 2009-11-10
The Software Center has an application called Touchpad with an option to disable

---

### Post by Dan Again on 2009-11-11
Okay, this worked great...however, I have a question. How does one enable the touchpad without a mouse? I used to use Alt+F2 to open a terminal and run gnome-mouse-properties, then use the arrow keys to enable touchpad. I cannot figure out how to do that with Touchpad.

---

### Post by Dan Again on 2009-11-11
Figured it out. Run gsynaptics.

---

### Post by Dan Again on 2009-11-11
Okay, so the touchpad keeps turning itself back on. Any ideas how to fix this?

---

