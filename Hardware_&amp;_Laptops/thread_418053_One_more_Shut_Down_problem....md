---
title: "One more Shut Down problem..."
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by AlexLog on 2007-04-22
When I shut down my laptop with Ubuntu (6.06, 6.10 or 7.04) everything goes fine except the shutting off the power. I see the blank screen and have to press the power button at least for 5 sec to turn the power off. It looks like this 

[http://ubuntuforums.org/showthread.php?t=416645&highlight=shut+down](http://ubuntuforums.org/showthread.php?t=416645&highlight=shut+down)

I tried to add to kernel line «acpi=force» but it didn't help.

«sudo shutdown -h -P now» in terminal window doesn't help too. But then I start Ubuntu recovery mode «shutdown -h -P now» or «shutdown -h now» turns the power off properly.

By the way, SUSE and Mandriva shut down my laptop correctly (but I have lots of other problems with WiFi and built-in card reader).

Does somebody know the secret? Any help will be appreciated.

Thanks.

---

### Post by Wherdgo on 2007-06-07
> **AlexLog said:**
> When I shut down my laptop with Ubuntu (6.06, 6.10 or 7.04) everything goes fine except the shutting off the power. I see the blank screen and have to press the power button at least for 5 sec to turn the power off. 

Same here.  I have an older laptop BIOS (possibly pre-1999, so the screen pop sez) and suggests the acpi=force line also.  Looking for implementation clues.

---

### Post by Wherdgo on 2007-06-07
> **AlexLog said:**
> I tried to add to kernel line «acpi=force» but it didn't help.

Does somebody know the secret? Any help will be appreciated.

I have the same problem and experiences here.  Don't know if the positioning/order of where «acpi=force» is placed in the .lst file is significant, and am looking for some guidance before going and monkeying myself with kernel-affectiing files that I don't fully understand.  Trial-and-error with kernel things would seem a recipie for disaster...

---

### Post by Farquhar on 2007-06-07
I run a Toshiba Satellite Pro 4300 and had problems with shutdown as well.

I added the acpi=force to the menu.lst

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=440ec28d-4de0-4de5-9ea5-059c3b6ce7ef ro acpi=force

and ran this in terminal:

```
sudo update-grub
```

Solved the shutdown problem.  But sleep and hibernate do not work.
Just remember that is you do this that you will have to repeat it every time there is a kernel update.

Best of luck

---

