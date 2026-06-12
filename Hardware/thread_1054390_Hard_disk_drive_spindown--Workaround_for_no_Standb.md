---
title: "Hard disk drive spindown--Workaround for no Standby/Sleep"
date: 2009-01-29
forum: Hardware
---

### Post by saranam on 2009-01-29
My computer will not wake-up from sleep/standby on either Ubuntu or Windows.  I hear this is a common problem.  Here is a workaround:
Hard disk spindown/standby:
Open a terminal.
Check you disk(s) by typing: sudo fdisk -l
On most modern computers your hard disk will by /dev/sda, on older computers /dev/hda.

Option 1: Set your drive to spindown with hdparm (you will have to set it again if you reboot):
In terminal:  sudo hdparm -S240 /dev/sda  (or for older drives: /dev/hda)

Option 2:  If you are comfortable doing it, edit /etc/hdparm.conf:
In terminal:  sudo gedit /etc/hdparm.conf
Add this to the bottom of hdparm.conf:
/dev/sda {
	spindown_time = 240
	}
(remember to change sda to hda if that is the drive you have)
(if you have multiple drives, repeat entry for each)
Save and exit.  Now spindown will be set at each reboot.

(240 = 20 minute idle time before spindown/standby.
Here are more common values:
60 = 5 min
120 = 10 min
250 = 30 min
280 = 1 hour
340 = 2 hours)
(1-240 are 5 second intervals, 241 and beyond are 1 minute intervals, max: 5.5 hours)

---

