---
title: "ATI Radeon HD 6570 Drivers and Performance Problems"
date: 2011-03-28
forum: Hardware
---

### Post by .bashrc on 2011-03-28
Hello,

I am running Ubuntu 10.10 on an HPE-59t desktop computer, with an ATI Radeon HD 6570 graphics card. I configured the machine with this card under the express assumptions that the drivers would "just work". Mistake No. 1.

So I think I have the proprietary ATI drivers installed, downloaded from their driver site. However, I'm having two issues.

1. Very slow redraw when moving certain windows.
2. The AMD Unsupported hardware watermark in the lower right hand corner of the screen.

I've searched for the latter issue and found the threads, but they were not helpful. So if there are any additional suggestions, I'd appreciate it.

Any help would be greatly appreciated.

---

### Post by .bashrc on 2011-03-31
So after uninstalling all the fglrx stuff and reinstalling it via the "Additional Drivers" panel in Ubuntu, now basic 2D and 3D appear to be working. 

To solve the AMD Watermark issue, here's what I did (you need sudo access):

1. Create a script called amdsucks.sh:

#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

2. run the script using:
sudo sh amdsucks.sh

   The watermark still persisted after this.

3. Now edit that file so that the DRIVER line reads:
DRIVER=/usr/lib/xorg/**extra-modules/**modules/drivers/fglrx_drv.so

Notice we've added the extra-modules folder here. Save the script and re-run (2).

4. sudo reboot, and all should be well.

Hope this helps someone else who stumbles across this.

---

### Post by Compare on 2011-05-14
> **.bashrc said:**
> So after uninstalling all the fglrx stuff and reinstalling it via the "Additional Drivers" panel in Ubuntu, now basic 2D and 3D appear to be working. 

To solve the AMD Watermark issue, here's what I did (you need sudo access):

1. Create a script called amdsucks.sh:

#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

2. run the script using:
sudo sh amdsucks.sh

   The watermark still persisted after this.

3. Now edit that file so that the DRIVER line reads:
DRIVER=/usr/lib/xorg/**extra-modules/**modules/drivers/fglrx_drv.so

Notice we've added the extra-modules folder here. Save the script and re-run (2).

4. sudo reboot, and all should be well.

Hope this helps someone else who stumbles across this.


Please make a Video !?

---

### Post by kdude63 on 2011-11-16
> **Compare said:**
> Please make a Video !?

You've a lot to learn my friend. ;)

---

