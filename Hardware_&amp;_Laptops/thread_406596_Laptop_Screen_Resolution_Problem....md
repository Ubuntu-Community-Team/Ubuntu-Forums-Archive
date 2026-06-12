---
title: "Laptop Screen Resolution Problem..."
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by RetepNamenots on 2007-04-11
Hey there,

I'm trying to install Ubuntu on a Fujitsu Siemens laptop - I've convinced my dad that it's much better than XP :) 

The only problem is that the screen is being detected as the wrong resolution. It's coming up at 640x480, and sits in the middle of the screen with black, inaccessible bars around the sides.

The regular resolution for the screen is 1024x768.

I've had a look at changing the resolution through the settings in Ubuntu, however there are no options other than 640x480!

Please help!

Cheers.

---

### Post by heimo on 2007-04-11
Check this first:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by RetepNamenots on 2007-04-11
Thanks.

The Laptop is a Fujitsu-Siemens Amilo L 6825. I've found a specific page on the Ubuntu website about it:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL6825](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL6825)

But it says that the resolution is fine???

I will try editing the xorg.conf file, and use these variables:

HorizSync 30-61
VertRefresh 56-76

Do these look about right?

Please help...

---

### Post by heimo on 2007-04-11
Yeah, looks like something that could be right for 1024x768 LCD.

---

