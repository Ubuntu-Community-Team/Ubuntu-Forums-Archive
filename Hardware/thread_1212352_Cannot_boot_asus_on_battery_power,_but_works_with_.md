---
title: "Cannot boot asus on battery power, but works with AC"
date: 2009-07-13
forum: Hardware
---

### Post by poboy on 2009-07-13
Installed UNR Jaunty on ASUS 900A via USB with no problem.  Formatted the 4gb ssHD and an 8gb sdhc as ext3.  Mounted the sdhc as /usr.

All the major things I tested worked well including wifi, sound, touch pad, video. Ubuntu did not recognize AC in use for while, but then began recognizing it.  Not sure what I did to fix it or if it fixed itself.  

My problem started when I tried to boot up via battery power.  It will not boot w/out AC connection.  It hangs after the Ubuntu progress bar finishes and shows some error messages: "Checking battery state . . ", then shows some lines of a daemon that did not execute because "dmideconde: command not found", then ends with two lines that are:
[   9.3111691] sd 2:0:0:0 [sdb] Assuming drive cache: write through
[   9.314319] sd 2:0:0:0 [sdb] Assuming drive cache: write through

The above message appear to be in a hung console. If I ctl alt del, responds with a couple of more lines, then hangs for good.  Any other keyin just echos.

After it hangs, I cannot shut down except by turning off the asus.  

If I boot with A/C connected, it will boot fine and shutdown fine.  

This problem is easily repeatable.

NOTE:  I performed the automatic update and installed all security and recommended updates before I recognized the problem. 

Any help will be appreciated.

---

### Post by poboy on 2009-07-15
After much research, I discovered that this phenomina is called "jump starting" as in you must first attach AC to boot up, then you can detach AC and run on battery only.  AFIK, this has only been seen, before now, when one uses certain third party batteries on Asus netbooks.  I am using a new Asus 900a with the original battery which did not have this problem before loading UNR.

Spent too much time with this. Loaded eeebuntu and everything works fine.

--cheers

---

