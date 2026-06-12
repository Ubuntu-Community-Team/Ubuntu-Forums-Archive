---
title: "touchpad tap click re-enabled after hibernate"
date: 2009-04-15
forum: Hardware
---

### Post by wakeboarder1335 on 2009-04-15
This is my hal: /etc/hal/fdi/policy/shmconfig.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>	
   <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
  </match>
 </device>
</deviceinfo>
```

I recently upgraded to 9.04 on my eee pc. This works fine, but for some reason after waking from hibernate, the tap to click is once again enabled. Any ideas on why this is happening. It's really annoying.

thanks

---

