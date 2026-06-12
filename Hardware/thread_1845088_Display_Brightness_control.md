---
title: "Display Brightness control"
date: 2011-09-16
forum: Hardware
---

### Post by cosmicgr on 2011-09-16
Hi,
I have a HP dv7 laptop, with switchable graphics (Intel HD and ATI Radeon 6770m).
Due to issues with switchable graphics, and to save battery, I have disabled the Radeon driver by changing the kernel argument line in GRUB. 
My laptop now runs just Intel card, and everything's fine, except for brightness control. I'm not able to control brightness of the display. When I press the function key and brightness +/- keys, I can see Gnome icon which shows that brightness is being adjusted, but there is no effect on the screen. 
This problem was there even in Radeon card driver too. 
I have also tried to change the values of brightness (on a scale of 10) by manually editing the appropriate files, but no effect. The brightness remains at 100%
I have Fedora 15 on a separate partition and that too has the same problem!
Can anybody trace the cause?

---

### Post by casualdodo on 2011-10-02
I was looking for a solution to a similar problem when I came across your post...

The fact that you can't control the brightness for either graphics card suggests that the problem might be something else.

> I have also tried to change the values of brightness (on a scale of 10)  by manually editing the appropriate files, but no effect.
What files did you edit? For example, this worked fine for me with an Intel card:

```
# Assume you want brightness set to 5 on a scale of 1-10
# Replace acpi_video0 with the appropriate device
echo 5 > /sys/class/backlight/acpi_video0/brightness
```I would also look to confirm that the driver being used is the expected one, and that you are not accidentally using the other graphics card.

---

