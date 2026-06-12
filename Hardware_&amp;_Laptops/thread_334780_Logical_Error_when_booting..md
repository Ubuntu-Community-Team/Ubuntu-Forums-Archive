---
title: "Logical Error when booting."
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by Jaygo333 on 2007-01-09
Whenever I boot into Ubuntu, it lags when Checking root system, appears.
Then it gives me a logical error and continues as if nothing happened.
I forgot the logical error number but it then continues to say it has dumped the required files into memory then it boots.
I get random errors when in Ubuntu, some files refuse to work, others refuse to save. 
Its as if the filesystem is dumped into RAM and only a portion of the system is ever saved back into the hard drive.

Then funny thing is, this only happens when I upgrade to Edgy.
When in Dapper, All works fine, WHY

---

### Post by hal10000 on 2007-01-09
You my boot your live cd and then check your root partition with [COLOR="Red"]sudo fsck -f /dev/yourdisk[/COLOR] 
The partition must NOT be mounted when doing this.

After booting, you may use [COLOR="Red"]dmesg | less[/COLOR] to see if errors occured.

Hope this can help you

---

