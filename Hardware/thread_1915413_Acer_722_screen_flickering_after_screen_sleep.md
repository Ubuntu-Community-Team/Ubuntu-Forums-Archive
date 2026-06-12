---
title: "Acer 722 screen flickering after screen sleep"
date: 2012-01-26
forum: Hardware
---

### Post by sailah on 2012-01-26
Hi,

Just bought Aspire One 722 (c60, 4gb ram). Tried Ubuntu 11.10, Mint 12, Mint LMDE, Ubuntu 10.10. Except for the last one, when the screen goes to sleep, and after waking up it flickers terribly. Even after restart takes some time for this effect to die out. Doesn't happen when I turn off the screen manually Fn+F6, only after automatic sleep. Perhaps a hardware issue, but maybe bad drivers affecting the hardware to some extent? Don't want to distroy the netbook (Would use 10.10 but don't know how to enable wireless - believe atheros chip). Does anyone have the same problem? Change the sleep mode for the screen to 1min and check it too please!

Thanks

---

### Post by Absolute Novice on 2012-01-28
I am having the same problem with my new netbook.

It rapidly changes the brightness settings and there is no way I can stop it. It happens after every time I close the lid or put it to sleep and as of yet I haven't been able to fix it.

Just bumping this thread so hopefully some linux guru will save the day.

---

### Post by sailah on 2012-01-30
That's a comforting news to some extent ;p

And a few more details: When flickering happened and is dying out Fn+F6 can enhance it again, but it's ok if you use it FIRST yourself.

Solution for now is to disable automatic monitor switching.

---

### Post by stetteo on 2012-02-08
I have the same issue, it is acceptable, but i hope it will be solved with new drivers.

---

### Post by nroewe on 2012-02-19
I've found suspending and then resuming seems to make it stop most of the time. It's a pain but at least a work around until it's fixed. I just close the lid to suspend. Not the best on the hard drive unless you wait 5 or 10 seconds to power back up.

I actually originally exchanged my machine thinking I had a defective one. What concerns me is how it still flickers in the BIOS after a reboot if you restart right after it starts. I hope this gets fixed eventually.

---

### Post by jenicek on 2012-03-28
Hi I have the same problem as you. So have  you found any solution so far?
Thanks Jenicek. 
> **sailah said:**
> Hi,

Just bought Aspire One 722 (c60, 4gb ram). Tried Ubuntu 11.10, Mint 12, Mint LMDE, Ubuntu 10.10. Except for the last one, when the screen goes to sleep, and after waking up it flickers terribly. Even after restart takes some time for this effect to die out. Doesn't happen when I turn off the screen manually Fn+F6, only after automatic sleep. Perhaps a hardware issue, but maybe bad drivers affecting the hardware to some extent? Don't want to distroy the netbook (Would use 10.10 but don't know how to enable wireless - believe atheros chip). Does anyone have the same problem? Change the sleep mode for the screen to 1min and check it too please!

Thanks

---

### Post by fredknex on 2012-04-08
-nevermind, apparently. guess it still does it on occasion. Hopefully links are helpful anyhow.



i believe is a driver problem. mine stopped doing it after installing the open source drivers, see #3 here-

[http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722](http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722)

Dont install the amd catylst drivers or it wont be able to resume from suspend properly.


this post was helpful as well-

[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)

---

