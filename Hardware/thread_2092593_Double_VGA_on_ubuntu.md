---
title: "Double VGA on ubuntu"
date: 2012-12-08
forum: Hardware
---

### Post by khaj_vah on 2012-12-08
Hello guys,

I have a laptop dell inspiron 17r (5720), which has double video card (intel, nvidia GT 630M, as i remember). First of all, when i bought this laptop, it had ubuntu installed and everything worked fine (nvidia driver were installed and detected in "additional drivers" and the power options were working (brightness decreased when unplugged)). At that time i installed windows then again changed to ubuntu, but this time, it does not work. They say that double video cards are not working on linux but how were they working when i first got this laptop? Currently i am using my nvidia VGA with "optirun" but i still need those power options to work (brightness decrease when i unplug).
Help please.

---

### Post by Isamu715 on 2012-12-08
> First of all, when i bought this laptop, it had ubuntu installed and everything worked fineDo you mean that the laptop was preloaded with Ubuntu? If that's so then it's possible the manufacturer made some modifications to the default Ubuntu setup which made it work with the hardware.

When you installed Ubuntu later, did you use the same version that was installed before? If not, try installing that version. Adding the following to GRUB_CMDLINE_LINUX in */etc/default/grub* may solve the brightness issue:
```
acpi_osi=Linux acpi_backlight=vendor
```

---

