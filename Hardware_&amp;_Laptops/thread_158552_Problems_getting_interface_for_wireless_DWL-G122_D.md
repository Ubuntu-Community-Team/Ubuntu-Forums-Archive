---
title: "Problems getting interface for wireless DWL-G122 D-Link USB Dongle"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by monomaniacpat on 2006-04-11
Having followed the instructions from [this](http://www.ubuntuforums.org/showthread.php?t=106846) thread, I managed to build the driver, which is now succesfully loaded on my machine. However, I have no interface for the device.

Here's what I did:

```
patrick@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]
patrick@ubuntu:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
```

Can anyone suggest what I can do to get the device working?

Thanks,

mono.

---

### Post by Darkriser on 2006-04-11
follow this thread ([http://doc.gwos.org/index.php/Rt2x00drivers)](http://doc.gwos.org/index.php/Rt2x00drivers)). it's very similar, but there are VERY important details 
(sudo mv /etc/modprobe.conf /etc/modutils/rt2570
and
sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko)

---

### Post by mrios on 2006-04-11
[QUOTE=Darkriser]follow this thread ([http://doc.gwos.org/index.php/Rt2x00drivers)](http://doc.gwos.org/index.php/Rt2x00drivers)). it's very similar, but there are VERY important details 
(sudo mv /etc/modprobe.conf /etc/modutils/rt2570
and
sudo mv /lib/modules/2.6.xx/extra/rt2570.ko /lib/modules/2.6.xx-xx-xxx/kernel/drivers/net/wireless/rt2570.ko)[/QUOTE]

I've done all of these things. I still have the same problem as the original poster. My problem is described in great detail at this ubuntuforums link: [http://www.ubuntuforums.org/showthread.php?t=157809]("http://www.ubuntuforums.org/showthread.php?t=157809")

This problem is very frustrating. This card works with OpenBSD... and has done so for a long time. Given the number of posts on this issue in the hardware forums, I hope that Ubuntu developers give it a look.  I like Ubuntu's features and wide software selection, but I may switch to OpenBSD because my computer is essentially useless without working wireless. 

Thank you to anyone who can provide some help.

---

### Post by monomaniacpat on 2006-04-11
I had a look at my dmesg. It seems to report the same things. Please, if anyone knows anything about this, help us out!

---

### Post by monomaniacpat on 2006-04-13
Anyone?

---

