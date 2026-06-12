---
title: "Irda - how can I find device name"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by fdimmling on 2005-10-21
I'd like to connect my Nokia cellular phone to my Acert Travelmate 290LCi via Irda. Running irdadump I can watch the packets from the computer and the cell phone. However using the device /dev/ttyS1 - which worked in Hoary - gives an error message cannot open /dev/ttyS1.

fd@acer:~$ sudo dmesg | grep irda
[4294710.551000] irda_init()
[4294710.560000] IrDA: Registered device irda0
fd@acer:~$

But using /dev/irda0 gives an no such device error. irdadump seems to know the device but does not tell it. Who else knows?

Friedrich

---

### Post by JimLittle on 2005-11-18
Sorry I don't know the answer but since it's been so long since your post perhaps this suggestion will help.  There is a utility called lsof (list open files) that can show you every file (and device) on your system that is in use and by what program.

Try entering:
sudo lsof | grep irdadump

or just

sudo lsof | grep -i irda

and see if that gives you something useful.

HTH,

Jim

---

### Post by fdimmling on 2005-11-20
Hi Jim,

I get a working Irda connection when I manually create /dev/ircomm0 by

mknod /dev/ircomm0 c 161 0

but after  reboot the device is gone. I have to do it every time I need the device. I have not found the correct place (script) where I should put this line to create the device automatically at boot time.

Thanks for your advice

Friedrich

---

