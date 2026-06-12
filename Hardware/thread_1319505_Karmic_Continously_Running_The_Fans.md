---
title: "Karmic Continously Running The Fans"
date: 2009-11-08
forum: Hardware
---

### Post by KoffeeKup on 2009-11-08
Hey guys,

I'm here again with one of my noob questions. I'm into Karmic and what I've released is that on my laptop, the fans will kick in and run continuously. On Jaunty, all I had to do was just put the laptop into Suspend Mode, and then power it back on in order for it to function normally. On Karmic, the fans will spin regardless if the system was suspended before.

I know that some Dell laptops have this problem, but I have a Toshiba so I wouldn't know if the same tools could be used. Any insight on this?

Thanks,
KK

---

### Post by steve161 on 2009-11-08
I have a Toshiba Satellite L305 and to get the fan working properly, I had to add  "acpi_osi="Linux"" to the kernel line in grub2.  However, I also had to do this in Jaunty and other distros, so I do not know if it is the same issue.
In Karmic, you have to open, as root,  /etc/default/ grub and add the line after "quiet splash".  Here is mine:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

(the ///'s are needed because grub2 does not recognize "")

Then run "sudo update-grub"

Without it, my fan would either run constantly, or not go on at all (coin flip).  Now, it kicks in at 56C and turns off at 42C, which is how my particular laptop is meant to do with windows.

If this does not work, just remove the line, and run update-grub again.

---

### Post by KoffeeKup on 2009-11-08
I have the L305D. Tried your fix and it's working normal. Thanks for your help.

---

