---
title: "Laptop cannot restart."
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by ychen on 2005-07-27
I have a problem about TOSHIBA TE2000 laptop which cannot restart from Linux - when it restarts, it fall asleep ;) so I have to press the power button. It is too boring when switch to Windows.

---

### Post by luca_linux on 2005-07-27
Try to pass "nolapic" as a kernel parameter at boot.

---

### Post by ychen on 2005-07-28
This doesn't work, nor "noacpi" "noapm".
I am so depressed. :mad:

---

### Post by ychen on 2005-09-09
It still has problem on restarting, but "freeze" issue can be solved by setting CPU speed on TOSHIBA TE2000. ;-)

---

### Post by iimess on 2005-09-09
I had a similar issue with Toshiba Satellite M35X S329
Whenever I hibernated from Windows and tried to restart from Ubuntu it froze at "Restarting the computer"
Somehow it got fixed magically without me knowing it......

---

### Post by ychen on 2005-09-09
You mean you can restart now?
Somebody said the restart issue might be solved in linux-2.6.12 :-?

---

### Post by iimess on 2005-09-10
[QUOTE=][/QUOTE]
 I think I'm still using 2.6.10
Anyway restart works now even Windows was hibernated.

Do you have the same problem (hibernation) or Ubuntu can't restart no mattar what?

---

### Post by ychen on 2005-09-10
My laptop cannot restart now, and sometimes hibernate like being freezed, especially using Firefox.
Do you have any suggestion?

---

### Post by taj on 2005-09-12
Maybe it's sleepd? Remove it or take all parameters out of its config file (/etc/default/sleepd)
After I installed sleepd the laptop fell asleep everytime after 30 sec. As you can understand it took a few wakeups before I was able to remove sleepd.

---

### Post by ychen on 2005-09-18
I don't have "sleepd" on my computer.

The restart and sleep problems on laptop are very painful. :mad: 

Another problem is that my laptop will sleep when I use some command in console mode -- especially "apt-get -h" or "apt-cache -h". That's very strange!

---

