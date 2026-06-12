---
title: "How to make RC.Local execute at boot?"
date: 2012-05-29
forum: Hardware
---

### Post by Lindsey334 on 2012-05-29
I have a problem on a Lenovo X220 that at every boot the display Brightness is always set to Maximum. Max_Brightness = 15. I desire Brightness = 3. I have just installed 12.04.

I found this Ask Ubuntu: [http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot](http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot)

I changed file /etc/rc.local to look like this:  
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 3 > /sys/class/backlight/acpi_video0/brightness
exit 0

But it does not work. When I boot, the brightness is always Maximum (15)

Now right after boot with brigtness at 15, if I go into Terminal and switch to ROOT (sudo su) and then type: echo 3 > /sys/class/backlight/acpi_video0/brightness 
then the brightness changes. Why won't this happen automatically at boot? 

Can someone please help me figure out how to fix this?

Thanks.

---

### Post by 2F4U on 2012-05-29
There is a bug report available here:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/882254](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/882254)

Can you check whether the suggested workaround solves your problem?

---

### Post by Lindsey334 on 2012-05-29
Thank you so much for this suggestion. But it didn't work.

I applied the change and rebooted. Still Max Brightness at 15. I came back later in the day and booted and the Brightness was at 3. I cheered! But then I booted a couple more times and all times Max Brightness was on after boot.

I do not know what accounts for it working on that one boot. I have tried booting on battery, with power cable plugged in. No pattern is emerging. But replacing the -x with -e and adding sh to beginning of the line did not work :(

I very much want to solve this. Please others, any suggestions?

---

### Post by brainwash on 2012-05-29
Another thread discussing the same problem:

[http://ubuntuforums.org/showthread.php?t=1976157](http://ubuntuforums.org/showthread.php?t=1976157)

---

