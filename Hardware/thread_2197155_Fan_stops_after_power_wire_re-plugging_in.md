---
title: "Fan stops after power wire re-plugging in"
date: 2014-01-02
forum: Hardware
---

### Post by ponasdzinglas on 2014-01-02
I just installed Ubuntu 13.10 on my laptop with AMD 7560m + HD4000.
To stop fan noise and overheating I installed fglrx and tlp
```
sudo apt-get install fglrx fglrx-pxpress 
sudo add-apt-repository ppa:linrunner/tlp 
sudo apt-get update 
sudo apt-get install tlp tlp-rdw 
sudo tlp start
```
Now I have this issue: fan sometimes starts to spin very loudly and annoyingly. Then I plug out power wire and fan stops (surprisingly).
My question is: is there a way to stop this madness without playing with wire?
Sorry for my bad English.

---

### Post by whitesmith on 2014-01-02
Welcome to the forum. I think you would get more responses if you asked the moderator to move it to Hardware. Cheers!

---

### Post by QIII on 2014-01-02
Moved to Hardware.

Does it ever do this while it is unplugged?

---

### Post by ponasdzinglas on 2014-01-03
I did not noticed this while unplugged. Maybe it tries to swich on to "performance mode" while plugged in...

---

### Post by QIII on 2014-01-03
When plugged in, have you allowed the fan to run at high speed for some time to see if it settles down on its own?

pxpress is very new, so it might be worth checking that out and filing a bug if that is the case.

---

### Post by ponasdzinglas on 2014-01-06
Yes, fan settles down after some time. I've checked temperature and it keeps on 46+-1 C. I wouldn't stop after replugging if it was overheating. I'm getting used to this...

---

