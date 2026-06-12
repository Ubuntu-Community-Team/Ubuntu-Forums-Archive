---
title: "Logitech LX3 Tilt Wheel Issues"
date: 2008-11-25
forum: Hardware
---

### Post by BrantlyMedders on 2008-11-25
So after upgrading to Intrepid, I noticed that my tilt wheel was behaving a little oddly.

Simply put, the tilt functions appear to be reversed (i.e. tilting to the right moves you back one page in a web browser, and vise versa for tilting left).

Using xev, it appears that a right tilt registers as button 6 while a left tilt registers as button 7.

Is it possible for me to re-map these button events through an fdi file?  Has anyone had any similar experience?

---

### Post by my_key on 2009-01-06
Heh. I have the same thing. Never noticed it since I don't use the tilt wheel. I don't think it's very handy.

If you mind though, you can fix it. In cat /etc/hal/fdi/policy/ create a file called mouse.fdi (sudo!).

It should be something like:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_driver" type="string">mouse</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">no</merge>
<merge key="input.x11_options.Buttons" type="integer">7</merge>
<merge key="input.x11_options.ButtonMapping" type="integer">1 2 3 4 5 7 6</merge>
</match>
</device>
</deviceinfo>
```

I have NOT tested this, but change the order of the numbers in the last line that starts with merge so that it works. Use the xev program to determine what each buttun is. Scroll up/down is 4 and 5 and tilt is 7 and 6 on my system.

---

