---
title: "Radeon card issues."
date: 2009-06-07
forum: Hardware
---

### Post by Hobbyist on 2009-06-07
I've been looking for an answer on this for quite some time. About a year and a half trying to install Ubuntu on a Dell Dimension 2350.I have a ATI Radeon 9200 I upgraded the ram and had just reinstalled xp. I run two moniters on Windows all is well with it blah blah, so I try to install Ubuntu again and picked up a tip to try and change my primary VGA card to the integrated one. Well it worked. Every other time I would try the status bar for the live installer would load to about 10% and freeze. My problem now is this. I want to use my video card I kinda bought it for a reason but I don't want to have to change over in the bios every time I switch OSes. How do I get Ubuntu to work with this radeon card? I tryed updating everything and then trying to load into the recovery console but I can even get that. My monitor just shuts off. Is there a command line thing I have to do? If there is, could you explain what it is I'm doing I completely new to this type of system. Thanks in advance.

---

### Post by khelben1979 on 2009-06-07
Are you able to get to a text console with that graphics card installed? ```
ctrl + alt + f1
```

---

### Post by Hobbyist on 2009-06-07
I did but I left the computer and came back it was no longer offering a terminal ctrl alt F1 doesn't do anything either

---

### Post by khelben1979 on 2009-06-07
> **Hobbyist said:**
> I did but I left the computer and came back it was no longer offering a terminal ctrl alt F1 doesn't do anything either

Sounds like that computer is not working as it should. Have you looked inside to see if it needs some cleaning? The fans may be filled with dusts and that the cooler of the cpu may not be cooling as much as it should. Have you checked the temperatures? Have you checked all the cables so that they sit correctly?

Once you get some stability on that computer (hopefully), you can download the ATi drivers from the ATi homepage, follow all the instructions, reboot and then you should have working drivers for your x-server.

---

### Post by Hobbyist on 2009-06-07
The computer has been cleaned, I switched back to old settings so I could try and download the file but it's in rpm format and alien can't properly convert it. Where do I get a stable driver for it?

---

### Post by khelben1979 on 2009-06-07
Get them [here]("http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx").

[Installer instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html").

---

