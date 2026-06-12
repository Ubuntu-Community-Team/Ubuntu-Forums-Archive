---
title: "new DIY pc using AMD 200ge APU using the wrong graphics drivers after bios update"
date: 2019-02-14
forum: Hardware
---

### Post by doctadrea on 2019-02-14
Hey buddies,

I was running this AMD 200ge setup with no problems, but I wanted to overclock the cpu a bit.  I updated the bios, and now I just get a blank screen when I try to boot into ubuntu.  If I go into recovery mode first and boot from there, it loads but with limited graphics support.

I tried booting from usb, but that isn't working either.  

$ lspci -nn | grep VGA
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Vega [Radeon Vega 8 Mobile] [1002:15dd] (rev cb)

And it should be Vega 3... not mobile.

Is this something I can fix in Ubuntu with drivers, or is the bios just not playing well with the APU?

Thanks in advance for the help.

---

### Post by him610 on 2019-02-14
>  I updated the bios
Maybe you downloaded and installed the incorrect bios firmware. Can you reinstall the original bios firmware from the backup you made? You did backup up the original firmware, didn't you?

---

### Post by Yellow Pasque on 2019-02-16
Did SecureBoot get turned on when you updated the BIOS?

---

