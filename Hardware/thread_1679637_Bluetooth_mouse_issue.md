---
title: "Bluetooth mouse issue"
date: 2011-02-01
forum: Hardware
---

### Post by fuchur on 2011-02-01
I use a bluetooth mouse on a thinkpad. In principle it works fine, but after 5-30 minutes the mouse stops working. 

A fix is to type:

sudo hciconfig hci0 lp RSWITCH

then the mouse works again and keeps working until the next reboot. 

My problem is now to make this permanent. Here is what I know so far:

(*) On older  versions, this used to work by deleting the last three words from the line
   lp rswitch,hold,sniff,park;
in /etc/bluetooth/hcid.conf.

However,  Ubuntu 10.10 does not have this file and I did not have success with just creating it. But maybe I screwed up here, in other context people do suggest to just create this file. 

(*) One can google patches for bluetooth-related packages that add such options to main.conf. However, it seems overkill for me to compile these packages, and I did not find any binaries.

(*) Maybe one could just autostart the command sudo hciconfig hci0 lp RSWITCH
 somehow. What exactly would I need to get this work? I read about /etc/rc files but found it confusing. 


Appreciating any suggestions


Additional info: it seems installing blueman does not make a difference. I am using 10.10 64 bit.

---

### Post by ajgreeny on 2011-02-01
You could try adding the command minus the sudo, just above the exit 0 line in the /etc/rc.local file with ```
gksu gedit /etc/rc.local
```so it looks like
```
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
hciconfig hci0 lp RSWITCH
exit 0

```

---

### Post by fuchur on 2011-02-02
Thanks, It seems that worked. Although I would still be interested to know if there is a more elegant solution...

---

