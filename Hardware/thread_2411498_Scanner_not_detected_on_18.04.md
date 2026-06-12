---
title: "Scanner not detected on 18.04"
date: 2019-01-31
forum: Hardware
---

### Post by danielsender on 2019-01-31
I have two Dell machines running 18.04. One was an upgrade from 16.04 (M90) and the other was a fresh install (M6800). I have a Brother printer/scanner MFC-7820N that was operating properly on the M90 while it was running 16.04. After the upgrade the scanning feature does not longer work. On the M6800 I followed the same procedure that I originally used on the M90, downloading the drivers from the Brother website and following their instructions. The scanner seems to be properly configured by checking with the program brsaneconfig2:
```

brsaneconfig2 -q | grep SCANNER
0 SCANNER             "MFC-7820N"         I:192.168.2.17
```

I was wondering if this is a bug or there is something new in sane/xsane that has to be done.

---

### Post by Claus7 on 2019-01-31
Hello,

I would advice you to try a couple of easy steps and check what will happen.
1) you could try adding this ppa to your system first
launchpad.net/~rolfbensch/+archive/ubuntu/sane-git
2) then restart both your computer and your printer/scanner
3) in case it does not work, try one more time either rebooting or restarting your machine
4) last but not least don't just try simple scan, yet try xsane first to check if your scanner is recognized and then choose simple scan

Hope you won't need to reach step 4,
Regards!

---

### Post by slickymaster on 2019-01-31
*Thread moved to **Hardware**.*

---

### Post by danielsender on 2019-01-31
I did follow your steps but unfortunately xsane nor simple-scan see the scanner.

---

### Post by Claus7 on 2019-01-31
Hello,

maybe following steps from the link below might be in the right direction for you. Have you tried checking scanner as root? As I was able to see a fresh install is recommended for the (same company) scanner to work. One other thing you could try is to completely purge your printer/scanner configuration and start anew. If it works like that, you might save yourself from a fresh installation.
[https://ubuntuforums.org/showthread.php?t=2390815](https://ubuntuforums.org/showthread.php?t=2390815)

Regards!

---

### Post by danielsender on 2019-01-31
I tried as root but it didn't work. I installed and uninstalled the driver already a few times. This [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012) leads me to think that my scanner falls in this category.

Anyway, thanks for your help.

---

### Post by danielsender on 2019-01-31
I tried as root but it didn't work. I installed and uninstalled the driver already a few times. This [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012) leads me to think that my scanner falls in this category.

Anyway, thanks for your help.

---

### Post by Claus7 on 2019-02-01
Hello,

it might be as you mention, yet have you checked answer 25 from the link you posted? It makes some linking that might work for you, yet it is harder than the things proposed earlier.

Hope it gets fixed soon,
Regards!

---

### Post by danielsender on 2019-02-01
> **Claus7 said:**
> Hello,

it might be as you mention, yet have you checked answer 25 from the link you posted? It makes some linking that might work for you, yet it is harder than the things proposed earlier.

Hope it gets fixed soon,
Regards!

That was the problem!!! I did before what answer #25 indicates, but I made a typo when I entered the name of the link, I typed libsane-brother.so instead of libsane-brother2.so.

Thank you very much for your time and energy.

---

