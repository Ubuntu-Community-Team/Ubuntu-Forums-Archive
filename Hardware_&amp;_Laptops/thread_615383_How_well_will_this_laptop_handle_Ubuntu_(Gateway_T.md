---
title: "How well will this laptop handle Ubuntu? (Gateway T-1620)"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by diggity801 on 2007-11-17
Im going to be buying a laptop soon and it is going to probably be the Gateway T-1620 

[http://support.gateway.com/s/Mobile/2007/Triton/1014881R/1014881Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/Triton/1014881R/1014881Rsp2.shtml)

I was wondering how well it will run games or if i could even run games decently on it? I know ATI is a pain in the *** when it comes to Linux. also the wireless card that is built into is based on a Broadcom chipset... am I going to have to use Ndiswrapper? The X1270 graphincs card, would it be able to run any games such as Team Fortress 2 on Linux?

---

### Post by dralokyn on 2007-11-17
the best information on laptops will be found here: [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by diggity801 on 2007-11-17
That Series of Gateway laptop isn't listed on there. How about the components? Specifically the ATI card and the Broadcom based wireless card.

---

### Post by bntuuu on 2007-11-24
The Gateway T-1620 comes with a Radeon X1270 and the Realtek RTL8187B.

To answer the big question, it handles Ubuntu just fine, however Xorg does not play well at all.

I was able to install 7.04 via the x86 alternate cd and create a dual-boot setup. 
The directions here: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
worked perfectly.

After I noticed the consistent Xserver error (no screens found), I patched up the system to 7.10 from the command line.
That also went quite smoothly.
The same error persists so I will try the workaround mentioned in bug #132716.
I have a suspicion that this is not the root of the error though.

At any rate, the system responds well and grub is easy to configure. Once the graphics issues are worked out this will be a worthwhile system to use.

Cheers

---

