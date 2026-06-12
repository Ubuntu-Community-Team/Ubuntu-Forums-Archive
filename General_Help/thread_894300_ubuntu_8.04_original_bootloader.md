---
title: "ubuntu 8.04 original bootloader"
date: 2008-08-19
forum: General Help
---

### Post by fahd on 2008-08-19
Hi folks ...!
I tried ubuntu 8.10 alfa4 in my removable harddisk, unfortunately it had overwritten my fixed-harddisk (official ubuntu 8.04) MBR. It had located it's bootloader in the original fixed-harddisk. When I switch off or remove the removable harddisk, the system does not start up (i often get a grub error), cause the bootloader area located in the MBR of the original harddisk points to the MBR of the  removable harddisk, which in turn was off. In short, how can i regain the original bootloader (ubuntu 8.04) prior the ubuntu 8.10 alfa4 installation. Any suggestion would appreciated. Thanks a lot.

Remark:
The ubuntu dev. team should take it in consideration, that MBR of an existed harddisk SHOULD NOT BE OVERWRITTEN without the endorsement of the user. Thanks again.

Fahd
080819

---

### Post by falcon61102 on 2008-08-19
Sounds like you just need to resetup the GRUB on your MBR which is no big deal.  Boot up and go to your terminal, then run:
```
sudo grub
```

You will now be in the GRUB setup menu, first you want to find where you GRUB has it's startup files so run:
```
find /boot/grub/stage1
```

That should give you at least one output, and you are going to want the lower one.  Meaning if it prints out (hd0,1) and (hd1,0), you are going to want the first one.  Use the first output that your receive from the above line for the next line:
```
root (hd0,1)
```
Replace (hd0,1) with whatever your first output is then you need to run the following line:
```
setup (hd0)
```

This should print about 6-8 lines of code.  If the setup was successful, you should see no "FAIL"'s at the end of any of the lines.  If you do, something isn't right.  You should be able to restart and be good to go at this point.

---

### Post by fahd on 2008-08-19
Thanks a lot for falcon61102 for his rapid help. That solved my problem with the exception that we should reboot from live cd, and giving falcon61102's advice. This is the real linux world, it has a great community of advocates. Thanks again falcon61102.

Fahd
080819

---

### Post by falcon61102 on 2008-08-19
No problem, glad you got it fixed.

---

