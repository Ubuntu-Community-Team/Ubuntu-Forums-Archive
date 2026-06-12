---
title: "lenovo Hibernate Issue"
date: 2008-08-18
forum: Hardware
---

### Post by beercz on 2008-08-18
I have spent the last couple of hours searching through the forums to no avail.  Apologies if I have missed a possible solution to my problem.

I have a Lenovo 3000 N200 laptop, runnung Hardy with kernel 2.6.24-21-generic.  I cannot get it to hibernate, or, more specifically, to write to the disk, although the laptop does shut down.

When I resume again later I just return to the normal login screen.

I think it is a USB problem, but the error message appears for about 1 second before my laptop shuts down. Having attempted hibernate several times, I think I have managed to piece together the error message, it goes something like this:

> Suspend_device(): usb_suspend+0x0/0x30 [usbcore]() returns ***
could not suspend device 3-4, error -32

Anyone know how to fix this, or able to provide pointers as to what to do next?

Thanks in advance.

---

### Post by linux_tech on 2008-08-19
Likely has to do with the ACPI modules
What does cat /sys/power/state show?
or  ls -l /lib/modules/$(uname -r)/kernel/drivers/acpi

Did you try reinstalling the kernal yet?

Does hibernate work correctly on 2.6.24-19-generic kernal?
[http://packages.ubuntu.com/hardy/base/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy/base/linux-image-2.6.24-19-generic)

Does hibernate to ram work?

How to suspend and hibernate a laptop under Linux
[http://www.linux.com/feature/54610](http://www.linux.com/feature/54610)
suspend2- [http://www.tuxonice.net/](http://www.tuxonice.net/)
[http://ubuntuforums.org/showthread.php?t=187584&highlight=r50e](http://ubuntuforums.org/showthread.php?t=187584&highlight=r50e)

---

### Post by beercz on 2008-08-19
> **linux_tech said:**
> Likely has to do with the ACPI modules
What does cat /sys/power/state show?
or  ls -l /lib/modules/$(uname -r)/kernel/drivers/acpi

Did you try reinstalling the kernal yet?

Does hibernate work correctly on 2.6.24-19-generic kernal?
[http://packages.ubuntu.com/hardy/base/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy/base/linux-image-2.6.24-19-generic)

Does hibernate to ram work?

How to suspend and hibernate a laptop under Linux
[http://www.linux.com/feature/54610](http://www.linux.com/feature/54610)
suspend2- [http://www.tuxonice.net/](http://www.tuxonice.net/)
[http://ubuntuforums.org/showthread.php?t=187584&highlight=r50e](http://ubuntuforums.org/showthread.php?t=187584&highlight=r50e)
Thanks for replying linux_tech.

cat /sys/power/state shows:

> mem disk ls -l /lib/modules/$(uname -r)/kernel/drivers/acpi shows:

> -rw-r--r-- 1 root root  9064 2008-08-12 18:06 ac.ko
-rw-r--r-- 1 root root 23332 2008-08-12 18:06 asus_acpi.ko
-rw-r--r-- 1 root root 18260 2008-08-12 18:06 battery.ko
-rw-r--r-- 1 root root  9612 2008-08-12 18:06 bay.ko
-rw-r--r-- 1 root root 12240 2008-08-12 18:06 button.ko
-rw-r--r-- 1 root root  7652 2008-08-12 18:06 container.ko
-rw-r--r-- 1 root root 15296 2008-08-12 18:06 dock.ko
-rw-r--r-- 1 root root  7680 2008-08-12 18:06 fan.ko
-rw-r--r-- 1 root root 46328 2008-08-12 18:06 processor.ko
-rw-r--r-- 1 root root 10120 2008-08-12 18:06 sbshc.ko
-rw-r--r-- 1 root root 19152 2008-08-12 18:06 sbs.ko
-rw-r--r-- 1 root root 21652 2008-08-12 18:06 thermal.ko
-rw-r--r-- 1 root root 16472 2008-08-12 18:06 toshiba_acpi.ko
-rw-r--r-- 1 root root 25544 2008-08-12 18:06 video.koI haven't yet tried reinstalling the kernel as yet.

Hibernate does not work correctly on 2.6.24-19-generic kernal

Hibernate to ram works fine.

I will check out the links very soon, and reinstall the kernel.

Thanks again.

Can anyone shed any further light on this issue?

---

### Post by beercz on 2008-08-19
OK, I have reinstalled the latest kernel which seems to have fixed the problem.

I still get the error message, but my laptop hibernates now :-), even though the screen goes bright green for a while when resuming.

Does anyone know if a log file is created when hibernating, and if so where is it?

Not really that important but I would like to find what the exact message is (it doesn't stay on the screen for more than a second).

---

### Post by beercz on 2008-08-24
I have just discovered that my integrated SD Card Reader does not work after resuming from hibernation.

I think that the aforementioned briefly appearing error message relates to this issue.

Anyone got any ideas as to how to solve this?

Thanks in advance.

---

### Post by skydog2004 on 2008-08-25
the log file for hibernating/suspending is /var/log/pm-suspend.log

---

### Post by beercz on 2008-08-25
Thanks - I will check this and see if I can make progress.

---

