---
title: "HP Pavilion dv2000 (dv2404ca) Brightness Control"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by panicb on 2007-07-09
I am unable to control the brightness properly.
The function key + f7, f8 combination does not work properly,
and the brightness control app says "Cannot get laptop panel brightness".

When I plug in power or unplug, the brightness changes, so something is going on.
In Vista, the function key combination changes the brightness properly.

Funny thing I found is that if I keep pressing function key, f7 and f8 together repeatedly, it sometimes goes to darker screen (probably the darkest setting) and sometimes to the brightest.

I have googled and searched on this forum.. thing I tried:
Downgrading the BIOS> Does not work, my model only supports the most recent one only.

Can I get some help? I got my sound card, graphic card, and wireless working but not this.

---

### Post by panicb on 2007-07-11
I tested the fn + f7, f8 keys in BIOS, and it works.. so not hardware problem.

sudo chown system_username /proc/acpi/video/VGA/LCD/brightness 
echo "n" > /proc/acpi/video/VGA/LCD/brightness


this does work, but of course, it's not a permanent solution: reboot and it goes away.

i tried nvclock, which says my Geforce Go 6150 isn't supported.

I also tried smartdimmer, which seems to work but fails to actually change the brightness of the lcd backlight.

What can I do?? This is the only compatibility issue I'm having with ubuntu.. =(

---

### Post by jiasheng on 2007-07-14
I suffered from the same problem.  I hope the howto I just posted can help you out.

---

### Post by tjduavis on 2007-09-16
> **panicb said:**
> I am unable to control the brightness properly.
The function key + f7, f8 combination does not work properly,
and the brightness control app says "Cannot get laptop panel brightness".

When I plug in power or unplug, the brightness changes, so something is going on.
In Vista, the function key combination changes the brightness properly.

Funny thing I found is that if I keep pressing function key, f7 and f8 together repeatedly, it sometimes goes to darker screen (probably the darkest setting) and sometimes to the brightest.

I have googled and searched on this forum.. thing I tried:
Downgrading the BIOS> Does not work, my model only supports the most recent one only.

Can I get some help? I got my sound card, graphic card, and wireless working but not this.

Could you please assist me in setting up the wireless? I also purchased a hp pavilion dv2404ca laptop and so far the only imperative component I need at this moment is the wireless.

---

### Post by panicb on 2007-10-22
The issue is fixed in Gutsy... like magic.

Although, the brightness applet is known to be incompatible with the corresponding acpi.

Great job, and thanks to the contributers.

---

