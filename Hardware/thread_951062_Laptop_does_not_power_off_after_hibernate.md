---
title: "Laptop does not power off after hibernate"
date: 2008-10-17
forum: Hardware
---

### Post by Vermind on 2008-10-17
Hello,
I have updated to 2.6.24-21-generic on my Hardy laptop, and it does not power off after I hibernate with s2disk (uswsusp package). When it should power off, I get an error message saying pm_ops->enter failed, calling power_off (Reason: Broken pipe)
I have not tried the older kernel yet, that is my next step. I also did some other stuff to optimize my laptop, such as disabling apm (since I have a new motherboard), disabling atd, and setting boot process (rc) concurrency to shell instead of none. I later reverted these changes, hoping to restore poweroff on hibernate, but it did not help.

I can manually power off by pressing the power button down on my laptop. After I restart, I can resume the system normally. However, after resume, some things just don't work: Lately running any command after resume just does not work: I cannot start gnome-terminal (if I hibernated from Gnome), or I cannot run any editor or sudo commands in a VT (if I hibernated from the virtual terminal (ctrl-alt-F2 and so on)). Howver, I am able to login in other VTs, but still unable to execute sudo commands.

Pressing the power button after a resume cause normal stopping of services, but after "Unmounting local file systems...." I soon get "mount: / is busy" two times, and then "* Will not halt" and nothing happens. pressing the power button again does nothing, but ctrl-alt-delete successfully reboots.

It would appear to me that shutdown itself is somehow bugged after resume, and when hibernating.

Shutdown (at least from GDM) after a non-resume bootup works.

Edit:
When booting with the 2.6.24-20-generic kernel, the system powers off properly after hibernate and resume also works well. So, for now, I am using the 2.6.24-20-generic kernel.

My laptop is an HP dv6520eo.

---

### Post by maximi89 on 2009-05-09
> **Vermind said:**
> Hello,
I have updated to 2.6.24-21-generic on my Hardy laptop, and it does not power off after I hibernate with s2disk (uswsusp package). When it should power off, I get an error message saying pm_ops->enter failed, calling power_off (Reason: Broken pipe)
I have not tried the older kernel yet, that is my next step. I also did some other stuff to optimize my laptop, such as disabling apm (since I have a new motherboard), disabling atd, and setting boot process (rc) concurrency to shell instead of none. I later reverted these changes, hoping to restore poweroff on hibernate, but it did not help.

I can manually power off by pressing the power button down on my laptop. After I restart, I can resume the system normally. However, after resume, some things just don't work: Lately running any command after resume just does not work: I cannot start gnome-terminal (if I hibernated from Gnome), or I cannot run any editor or sudo commands in a VT (if I hibernated from the virtual terminal (ctrl-alt-F2 and so on)). Howver, I am able to login in other VTs, but still unable to execute sudo commands.

Pressing the power button after a resume cause normal stopping of services, but after "Unmounting local file systems...." I soon get "mount: / is busy" two times, and then "* Will not halt" and nothing happens. pressing the power button again does nothing, but ctrl-alt-delete successfully reboots.

It would appear to me that shutdown itself is somehow bugged after resume, and when hibernating.

Shutdown (at least from GDM) after a non-resume bootup works.

Edit:
When booting with the 2.6.24-20-generic kernel, the system powers off properly after hibernate and resume also works well. So, for now, I am using the 2.6.24-20-generic kernel.

My laptop is an HP dv6520eo.
I have exactly the same problem, but the message "pm_ops" appear when the shutdown works correctly, but in my case the monitor still on when this fails, or shutdown the monitor, but with a message "saved image" of hibernate,  only the message appears when this works correctly.
Any idea? i have a kernel 2.6.29 i use Debian Squeeze.
And i use a Desktop PC.
Greetings!

---

### Post by Vermind on 2009-05-10
After I switched to Ubuntu Intrepid and later Jaunty, I have not had this issue. I recommend upgrading pm-utils...

---

### Post by darkghost2 on 2009-05-10
same problem .. i will try to ubuntu 9.04

---

### Post by maximi89 on 2009-05-17
> **darkghost2 said:**
> same problem .. i will try to ubuntu 9.04

the problem come from the file /etc/uswsusp.conf
that file maybe say reboot or poweroff, change to shutdown and it works finely ;)

---

