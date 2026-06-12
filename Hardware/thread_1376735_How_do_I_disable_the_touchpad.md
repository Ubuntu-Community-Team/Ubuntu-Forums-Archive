---
title: "How do I disable the touchpad?"
date: 2010-01-09
forum: Hardware
---

### Post by mgw2008 on 2010-01-09
I tried to 
[code]
synclient TouchpadOff=1
[\code]
but that doesn't work for me. 

My shmconfig.fdi looks like this:
[code]
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
[\code]

As several laptops have "trackpoints" and "touchpads" installed I would have expected an option under the mouse settings...

---

### Post by sgosnell on 2010-01-09
I'm not sure about 8.10, but in 9.04 you can use Start/Preferences/Mouse, then the touchpad tab, and uncheck the box for "enable touchpad".

---

### Post by derekmbarnes on 2010-01-09
What model is your laptop? Is there anything on the keyboard to turn the touchpad off manually?

---

