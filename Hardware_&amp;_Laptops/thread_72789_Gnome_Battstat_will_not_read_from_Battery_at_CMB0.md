---
title: "Gnome Battstat will not read from Battery at CMB0"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by stonhaus on 2005-10-07
I have a Compaq 1711cl laptop which has always had problems with the gnome battstat-applet. It will not read the values of the battery and only show that it is plugged in at all times. ACPI is reading the battery status just fine, but it appears that the gnome applet cant read from CMB0.

I found someone who has the same problem and fixed it, but his fix doesnt seem to work for me.

The link to his site is here: [http://www.ttwhy.org/home/blog/2005/09/09/battstat-ubuntu-and-you/]("http://www.ttwhy.org/home/blog/2005/09/09/battstat-ubuntu-and-you/")

I install his recompiled battstat-applet-2 file and chmod it to 755 and it all appears to be setup correctly. When I then try to add the applet to the panel it will just look like something is loading for an instant, but the battstat-applet will never appear.

Any help would be awesome, this is my last major bug with Ubuntu.

Thanks.

---

### Post by dakira on 2005-10-17
Hi,

You have a broken hardware description table (DSDT) in your bios. This is not Ubuntus fault. In most cases this happens because your vendor compiled the DSDT with a microsoft compiler which produces broken code. Windows works with the broken code. Linux doesn't. You can fix your DSDT using the guide in the wiki:
[https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery)

BUT: The DSDT on my laptop is okay and everything worked perfectly in Hoary for me. I wrote the above guide after I fixed the ACPI problems on a friends laptop. NOW that I updated to Breezy it doesn't work anymore and I can't find a fix. I am sure my DSDT is okay so this can't be the problem. I also tried the fix in the blog entry and it doesn't help.

Nonetheless you should fix your broken DSDT using the above guide since it is always good to have a correct DSDT.

---

