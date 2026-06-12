---
title: "Black screen on toshiba"
date: 2011-02-14
forum: Hardware
---

### Post by Alavi on 2011-02-14
Hi guys,
fisrt of all, i sure hope anyone will be willing to help me, i'm not a beginner at using terminal and stuff, but nor am i a pro :)

i am working with [Toshiba m30x 118]("http://za.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ZA&com.broadvision.session.new=Yes&PRODUCT_ID=97929")

I have installed both the maverick 10.10 and 10.4 lucid, and it's exacly the same result.
the install will freeze, i started it with noapic and acpi=off, installs perfectly.
after the install, and a regular boot, ubuntu starts up, starts gui, and works for about 10-20s.
Than the screen goes black.

i have done a lot of searching via google, and the only answer i have found is an unfinished thread saying that i should reconfigure xorg.conf, the problem is that dpkg-reconfigure xserver-xorg does nothing at all. when i checked via failsafeX, and the /etc/X11/xorg.conf doesn't exist at all.

So, please, does anyone have any ideas?
would adding an noapic and acpi=off to boot help, and how to do it?
and if not, what to do? :(


Thank's in advance
Cheers
~Marko

Update: tried booting with noapic and acpioff, and no difference.

---

### Post by Alavi on 2011-02-15
Thank you very much, o dear community -.-

---

