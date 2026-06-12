---
title: "network card not working"
date: 2008-09-30
forum: Hardware
---

### Post by Vcktor on 2008-09-30
Hello I've recently installed Ubuntu 8.04 lts on my toshiba laptop but the ethernet card is not recognized. The card is from Marvell and they've recently released a driver for linux. I've downloaded the driver but not sure how to install since i'm completely new to linux. hope someone can help, thanks

---

### Post by jcathey on 2008-09-30
I had the same problem.  Run the following commands and you will be flying high.

Run all of this as root user by entering sudo before each command.

# rmmod sky2 (it is ok if this does not show as inserted)
# cd /lib/modules/2.6.24-16-generic/kernel/drivers/net (the 2.6.24-16-generic folder might vary in number depending on your kernel)
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

After doing these commands run the following command to insert the sky2 module:

modprobe sky2

This should have your card up and running, but when you reboot you will have to run modprobe sky2 again unless you add "sky2" to the end of the /etc/modules file.

This worked great for me and if you need to know how to get the atheros 5007eg wireless card working if you have that one i can help with that too.

I hope this helps,

Jeremy

---

