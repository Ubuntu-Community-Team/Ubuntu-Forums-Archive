---
title: "Solution to ATI RADEON watermark"
date: 2011-06-20
forum: Hardware
---

### Post by Grasber on 2011-06-20
Hi folks. I was having some issues with the "AMD Unsupported hardware" watermark with my Radeon 6370 using the privative driver. I found a solution [here]("http://ubuntuforums.org/showthread.php?t=1762329"), which is the one that appears almost anywhere. Unluckily for me it didn't work. The problem was that it was referencing a file that didn't correspond to the actual driver file that my Ubuntu was loading.
In my case, the correct script is:

> #!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
The original script had this line:
> DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.soBut the the one that worked for me is:
> DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.soHope it helps :)

---

### Post by BeeDee on 2011-08-06
Thanks Grasber. Your modified line worked for me on my new HP Pavillion DM1 -3101EA.

Now I just need to get the touchpad to tap for right click and I'll be as happy as a sandboy.

---

