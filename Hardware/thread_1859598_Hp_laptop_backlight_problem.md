---
title: "Hp laptop backlight problem"
date: 2011-10-14
forum: Hardware
---

### Post by donovan6000 on 2011-10-14
The backlight on my HP Dv7t-4100 doesn't work like it should in Ubuntu. I've had this problem for a couple years now, but I decided to wait until 11.10 was released to see if it was fixed, but it wasn't. The brightness control keys can adjust the backlight, but the backlight is always either at 0% or 100%. I cant get it to adjust to any values i between 0% and 100%.

I tried looking this up on the Internet, but I couldn't really find anything.

Is there any way to fix this?

thanks

---

### Post by hsoulen on 2011-10-14
> **donovan6000 said:**
> The backlight on my HP Dv7t-4100 doesn't work like it should in Ubuntu. I've had this problem for a couple years now, but I decided to wait until 11.10 was released to see if it was fixed, but it wasn't. The brightness control keys can adjust the backlight, but the backlight is always either at 0% or 100%. I cant get it to adjust to any values i between 0% and 100%.

I tried looking this up on the Internet, but I couldn't really find anything.

Is there any way to fix this?

thanks

This looks like a similar issue with an HP laptop:

[http://ubuntucomputing.blogspot.com/2011/10/how-to-fix-adjust-screen-backlight-of.html]("http://ubuntucomputing.blogspot.com/2011/10/how-to-fix-adjust-screen-backlight-of.html")

Fix is for Mint but since Mint is based on Ubuntu it might be worth a shot!

The most important part is this:

```
Edit the GRUB2 boot parameters in /etc/default/grub to add acpi_vendor=backlight , as follows:

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

You can add the "acpi_backlight=vendor" entry after any other options you may have listed such as "quiet splash" just remember to include them all within one set of double-quotes e.g.:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Cheers,

Hank

---

### Post by rainy03 on 2011-10-14
:p&#65292;hello.i am new here.Just want to say hello to everyone

---

### Post by donovan6000 on 2011-10-14
Unfortunatley, adding that stuff to my /etc/default/grub file didn't help. It only made it so that my backlight is always at 100%. The backlight control keys dont do anything. Maybe I have to re-assign the backlight control keys. Is there anyway to that that straight from Ubuntu, or do i have to use a 3rd party tool.

---

