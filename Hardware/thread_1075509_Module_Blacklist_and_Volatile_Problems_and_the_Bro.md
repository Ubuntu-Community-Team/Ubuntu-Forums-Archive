---
title: "Module Blacklist and Volatile Problems and the Broadcom Driver"
date: 2009-02-20
forum: Hardware
---

### Post by JamieKitson on 2009-02-20
Hi,

I've been trying to install Broadcom's STA driver. I can do it manually but I haven't managed to get it going from boot. This seems to be for two reasons. 1) the ssb module still loads despite being blacklisted in /etc/modprobe.d/blacklist and 2) there is another wl module in volatile that is built(?) at boot and I don't know how to remove.

Can anyone help me with these two problems? Is blacklisting broken? Is there another way to blacklist modules? How do I remove wl.ko from volatile pertinently?

I know that I can add my manual commands to rc.local but that seems like a lame solution to me.

I believe that Broadcom's STA driver is preferable to the b43 driver as the later uses ndiswrapper. Am I right in these two assumptions?

Thanks, Jamie Kitson

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by JamieKitson on 2009-02-21
Ok, I wasn't doing things the Ubuntu way. Fired up Gnome and enabled the Broadcom STA driver (previously I had downloaded and compiled it) in the restricted driver/hardware manager and it seems to be ok now.

Can anybody tell me how I could have done this on the command line?

---

