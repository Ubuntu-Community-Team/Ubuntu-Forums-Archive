---
title: "Averatec 3700 Wireless Problem"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-05-10
Hello,

I'm running Ubuntu 6.06 live install cd and my wirless Internet works.

After I install Ubuntu to the hardrive, my wireless card shows up as ra0 but does not detect my wireless router.

I'm wondering which steps would be recommended to diagnose this problem.

Thanks,

Mathieu

---

### Post by muadib on 2006-05-10
I tried booting the installed system with the kernel on the live cd, version 2.6.15-19-i386 whith the appropriate initrd with the same problem.

When I run iwconfig from the live cd ra0 is recognised and finds my wireless router but when I run the system from the hardrive ra0 is recognised but the router is not found.

I'm wondering if anyone else has had similar problems and I'm wondering what might be the cause.

Thanks,

Mathieu

---

### Post by muadib on 2006-05-11
I have more information.

When I try and bring up the interface with dhclient ra0, the kernel crashes and I get a message that includes : soft lockup on cpu#0

Thanks,

Mathieu

---

### Post by muadib on 2006-05-11
I have more information on this problem.

It seems that the kernel only crashes when Xorg is running with the via module.

If I make sure that Xorg is not running, then the wireless card driver can be used without a problem.

Does anyone have any thoughts at what the problem could be ? 

Mathieu

---

### Post by muadib on 2006-05-11
Hello,

More information once again that I hope can diagnose my problem.

Once Xorg is loaded using the via module, it does not matter if I kill X, the wireless card is still unusable.

Does this suggest that the video driver is the problem and not the rt2500 driver ?

Thanks again,

Mathieu

---

### Post by thedward on 2006-05-12
Add the DisableIRQ option to your /etc/X11/xorg.conf

```

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
EndSection

```

Also, add noapic to the line starting with "# kopt=" in your /boot/grub/menu.lst, then do update-grub

I'm not sure if both of those steps are necessary, but after that my wireless worked fine.

---

### Post by muadib on 2006-05-12
Hello,
Thank you once again for your help with this problem.
Adding
Option          "DisableIRQ"
To xorg.conf in the video driver section was all that was needed.
Regards,
Mathieu

---

### Post by sebastianariher on 2008-03-31
hi i have same problems you had but I dont know how to enable the option disableIRQ OPTION  can you please help me because I dont have wirless at all and I need it urgently please helpp me thankk youu

---

