---
title: "upgraded to 14.04 and can't use the scanner"
date: 2014-07-01
forum: Hardware
---

### Post by teodosio on 2014-07-01
Hi!
I recently upgraded my Ubuntu from 12.04 to 14.04 and I cannot use my Brother DCP-150 C printer Scanner! It worked perfectly with the 12.04 version, but it says it doesn't find the scanner. The printer is working fine. How can I solve this. Brscan and brscan keytools are installed.
Thanks in advance if you can try to help me.

---

### Post by SuperFreak on 2014-07-01
Check this [LINK]("http://askubuntu.com/questions/116157/how-do-i-install-a-scanner-driver-for-a-brother-mfc-7420") I was able to get my MFC 5490CN Brother printer working when I had the same issue
I had the driver installed I just had to do this:
> 1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):

The lines to be added--------------------------- 


# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"


3. Restart the OS. 

---

### Post by teodosio on 2014-07-01
Hi! Just did it, but still the same... Thanks anyway.

---

### Post by teodosio on 2014-07-01
Hi Superfreak!
I tried to uninstall brscanconfig2 and then install it agaib and.... :-) It worked! It's working as well as in 12.04. I believe your suggestion also helped because I read it in the original link you posted! So, THANKS very much!

---

### Post by SuperFreak on 2014-07-01
Welcome. 
Please mark thread as SOLVED

---

