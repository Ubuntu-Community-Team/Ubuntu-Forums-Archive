---
title: "Fan won't stop running"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by yerch on 2005-02-20
I have a bad feeling that somewhere in this forum there is an answer to this, but I sure can't find it.  

I have a Sony VAIO RX-650 desktop that I recently installed Ubuntu on.  The only real problem is that the fan runs constantly in Ubuntu and it is driving me nuts.  The fan almost never runs in Windows.  I'm guessing this is some kind of power management issue but I have no idea where to even begin.  

Any advice is greatly appreciated.

Thanks,
eric

---

### Post by virtualXTC on 2006-06-05
My girlfriend has a PCV-RX651 and with the same issue. 
The only advise I can give to you is DON'T BUY SONY!!!  If their market share collapes, maybe they'll stop loading their machines with propritary crap.

Also I hear of some sucess stories of getting fans to work properly in SUSE - I'm probably gonna check it out for my self.

Good luck!

---

### Post by virtualXTC on 2007-02-18
I have a solution that was posted here:
[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

install package: lm-sensors
run: sensors-detect (answered "yes" to all of their questions)
run: pwmconfig
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add
/usr/sbin/fancontrol &
to /etc/rc.local

---

