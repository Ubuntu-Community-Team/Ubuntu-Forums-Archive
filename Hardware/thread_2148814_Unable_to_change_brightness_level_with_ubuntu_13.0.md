---
title: "Unable to change brightness level with ubuntu 13.04 and Dell"
date: 2013-05-26
forum: Hardware
---

### Post by honeycup on 2013-05-26
There was no problem with Ubuntu 12.10 but after upgrading to 13.04 I can't change the brightness level of my Dell 3721 laptop anymore. Nothing happend if I use the hardware keys or ubuntu system control. If I use the command  "echo xxxx | sudo tee /sys/class/backlight/intel_backlight/brightness" display brightness will change, but its very uncomfortable to use the terminal to change the brightness level. Is there any solution to reactivate the hardware keys?

> VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)"

---

### Post by Toz on 2013-05-26
Can you try the following kernel parameter (acpi_osi="!Windows 2012")? Like this (from a terminal window):

[LIST=1]
[*]Edit the grub configuration file:
```
gksu gedit /etc/default/grub
```
[*]Add the parameter by changing the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
[*]Save the file
[*]Update Grub:
```
sudo update-grub
```
[*]Reboot and test.
[*]
[/LIST]

---

### Post by honeycup on 2013-05-27
Thank you a lot, hardware keys are working again!

---

### Post by Toz on 2013-05-27
Great to hear. 
Can you mark this thread as solved by clicking on the "Edit" link in your original post, clicking on "Go Advanced' and changing the prefix to "[SOLVED]"? This way others can benefot from this solution.

---

### Post by nickG4000 on 2013-07-01
Hi

I'm still having trouble with this. I've tried the above as well as the suggestions in [http://ubuntuforums.org/showthread.php?t=2144815](http://ubuntuforums.org/showthread.php?t=2144815) 
What is interesting is that I can't change the brightness in the System Settings either, although the screen power saver works. 

In 12.04 I had no problem. This is a Lenovo Z575 laptop if that makes a difference

Any suggestions?

Thanks

---

### Post by Toz on 2013-07-01
> **nickG4000 said:**
> Hi

I'm still having trouble with this. I've tried the above as well as the suggestions in [http://ubuntuforums.org/showthread.php?t=2144815](http://ubuntuforums.org/showthread.php?t=2144815) 
What is interesting is that I can't change the brightness in the System Settings either, although the screen power saver works. 

In 12.04 I had no problem. This is a Lenovo Z575 laptop if that makes a difference

Any suggestions?

Thanks
Can you provide some more system information (from a terminal window):

1. Your kernel boot line:
```
cat /proc/cmdline
```
2. Your video card(s):
```
sudo lspci -vnn | grep -A12 VGA
```
3. Your brightness interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
4. A copy of your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

