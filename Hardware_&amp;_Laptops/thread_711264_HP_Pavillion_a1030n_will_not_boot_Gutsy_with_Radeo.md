---
title: "HP Pavillion a1030n will not boot Gutsy with Radeon 9200"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by trixx on 2008-02-29
Does not boot. At all. Brings be to the Ubuntu loading page, with the logo, and a status bar below it, and it gets about 1/5th of the way. When I used to try to run Kubuntu, I had the same problem, and it showed the status of the boot, and it'd always hang at "Starting Hotplug Subsystem".

I can't get into ubuntu to install restricted drivers for the 9200, because I can't even get INTO Ubuntu with it plugged in. Please help :(

---

### Post by Yellow Pasque on 2008-02-29
This does not sound like a video driver issue at all. Based on the Kubuntu error, I would try disabling USB in the BIOS. Also, try booting with the nosplash option so you can see where it hangs.

BTW, the restricted driver is for the Radeon 9500 or later.

---

### Post by trixx on 2008-02-29
But I can boot with onboard video... just not with the video card :/ I'll try disabling USB, and nosplash... I'll update in a few minutes.

Ok I disabled usb legacy mode or something in my BIOS... that didn't do anything, and I couldn't find out how to use nosplash command? I went into grub, and went to make a new command for booting Ubuntu, and when I did, I put in nosplash as the command, then when I left, and came back into the boot commands, it was gone, and it just keeps deleting it when I put it there :/

---

