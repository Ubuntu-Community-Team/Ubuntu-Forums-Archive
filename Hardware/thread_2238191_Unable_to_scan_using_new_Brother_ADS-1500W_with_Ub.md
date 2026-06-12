---
title: "Unable to scan using new Brother ADS-1500W with Ubuntu 14.04 LTS"
date: 2014-08-06
forum: Hardware
---

### Post by lmscully on 2014-08-06
I recently purchased a Brother scanner ADS-1500W and downloaded driver from Brother. I used the version for 13.04 because 14.04 wasn't available. When I start Simple Scan, the scanner is present but Fails to Scan. I called Brother for support but they said they only support Windows and Mac. I'm new to Ubuntu. Has anyone had any success with Brother ADS-1500W using Ubuntu 14.04 LTS?

---

### Post by plucky on 2014-08-07
Have you followed all the install instructions on the [Brother](http://support.brother.com/g/s/id/linux/en/instruction_scn1d.html?c=us_ot&lang=en&comple=on&redirect=on) website?

Especially the second one for "Setting for normal users"

Open a terminal and post output for ```
dpkg -l | grep -i brother
```

You could try starting simple-scan in superuser mode ```
gksu simple-scan
``` Does that work?

Good Luck

---

### Post by lmscully on 2014-08-08
I followed the instructions on the Brother website and tried your suggestions but no luck so far. I appreciate your reply. Thank you!

---

