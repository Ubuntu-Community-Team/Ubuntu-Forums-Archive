---
title: "kindly help. Suspend/Hibernate problem on Acer 3620 Laptop"
date: 2008-07-07
forum: Hardware
---

### Post by Avinash.Rao on 2008-07-07
Hello,

I have installed Ubuntu 8.0 on ACER 3620 Laptop with 1.5GB RAM. Everything seems to work fine except the Suspend and Hibernate options. Its a clean install no dual boot.

When i select suspend, i get a serious of text messages and is stuck at Suspending console. and nothing happens, i press a key, etc, but the system doesn't come back. I have insalled all the OS updates after installing the OS.

i noticed a error in these text messages.

582.008342 code: Bad EIP value
EIP [<f8bd7d30> 0xf8bd7d30 SS:ESP 00:f7571f28
end trace..

Please help
Avinash

---

### Post by Avinash.Rao on 2008-07-07
:confused:

---

### Post by Avinash.Rao on 2008-07-08
I managed to solve this. When i noticed the System log, the OS was probing the wireless adapter continuously. I didn't know how to stop the OS from doing this so i installed the correct driver for the Wireless NIC and both Hibernate and Suspend starting working.

Can i put this in the hardware compatability list so that its available for everybody!

Avinash

---

### Post by Avinash.Rao on 2008-07-08
How do i configure the display adapter in ubuntu? I didn't find any GUI tool that shows the graphics adapter i am using.
The /etc/X11/xorg.conf file says

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Thanks

---

