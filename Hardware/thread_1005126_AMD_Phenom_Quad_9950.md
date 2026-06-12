---
title: "AMD Phenom Quad 9950"
date: 2008-12-07
forum: Hardware
---

### Post by killer2239 on 2008-12-07
Will there be future support for controlling the processor performance? Right now changing it to on demand, or lowering its speed is disabled and only in performance mode.

---

### Post by iggykoopa on 2008-12-08
I have an AMD phenom 9500 and it has two steps, 2.2 and 1.1 ghz. Not sure what all is different with the 9950 that it wouldn't work. I just hope they have support for the thermal sensors in lmsensors soon.

---

### Post by killer2239 on 2008-12-08
> **iggykoopa said:**
> I have an AMD phenom 9500 and it has two steps, 2.2 and 1.1 ghz. Not sure what all is different with the 9950 that it wouldn't work. I just hope they have support for the thermal sensors in lmsensors soon.

I ran sensor-detect then added to gnome panel the temp. It is able to monitor it. Just cant monitor it in conky. =( , but i hope to be able to scale power to on demand. I noticed my AMD Athlon X2 ran 15C cooler from performance and on demand mode.

---

### Post by iggykoopa on 2008-12-08
when you run sensors-detect does it show up as the k10 module? I can add the sensor-applet for it but it stays at 40 degrees no matter what.

---

### Post by sweetsinse on 2009-01-01
there has been talk of a K10 module that will, i think should already, be out soon.

[http://lists.lm-sensors.org/pipermail/lm-sensors/2008-July/023816.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2008-July/023816.html)

there is also a link to that on Phoronix...

[http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA](http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA)

I used the attachment provided in the first link (the next guy in the list has a 9950 like me and said it worked fine):

[http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)

after doing that i *semi* followed these instructions:

[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)

1) i downloaded attachment.bin and renamed it to k10temp.c
2) i issued this command in the same directory as k10temp.c

make -C /lib/modules/$(uname -r)/build M=$(pwd) modules

3) i then made sure the module loaded ok

sudo insmod k10temp.ko

4) if that succeeds, and lm-sensors now sees a temp, i copy k10temp.ko to the appropriate modules folder

sudo cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon

5) and update the module cache/dependencies

sudo depmod

6) and lastly add the module 'k10temp' to /etc/modules


after all this i just rebooted and everything was working fine.  the readings have been spot on to my bios readings, after either hours of mprime or idling.

hope it helps

---

### Post by iggykoopa on 2009-01-01
thanks for the tip, I'll give it a try in a few minutes.

---

### Post by sweetsinse on 2009-01-06
i did it again after installing to another partition, and it looks like creating the makefile is a necessary step.  i didnt think it was using the makefile in any way since only issuing `make` does nothing; you have to use the full command.  either way the above works fine.

---

