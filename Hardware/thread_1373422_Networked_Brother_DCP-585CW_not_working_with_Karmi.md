---
title: "Networked Brother DCP-585CW not working with Karmic"
date: 2010-01-05
forum: Hardware
---

### Post by MickSulley on 2010-01-05
Hi,
I have a Brother DCP-585CW printer connected to my network.  I loaded the drivers from Brother and it worked fine on Jaunty.  I recently did a fresh install on my laptop of 64 bit Karmic, installed the printer exactly as I did before and it does not work.  It all looks OK from the laptop, appears to print OK, the printer wakes up, but no print.  it still works OK from the desktop which is still on 64 bit Jaunty.

Any idea what could be wrong?

Thanks 
Mick

---

### Post by Jose Catre-Vandis on 2010-01-06
This might help

[http://ubuntuforums.org/showthread.php?t=1373928](http://ubuntuforums.org/showthread.php?t=1373928)

---

### Post by MickSulley on 2010-01-06
Well it looked promising when I read through it, but still the same I'm afraid.  When I send a test page the printer display lights up, so it is communicating, the print queue says that it completed, just no paper coming out!  It works fine from my desktop which is still on Jaunty.

I've also just tried it via USB and that doesn't work either.

Scanning worked straight off, not a problem with that.

Thanks anyway, if you have any other ideas I would be happy to try them.

Cheers

Mick

---

### Post by Jose Catre-Vandis on 2010-01-07
Have you done these bits (from Brother site)
```
For dpkg users:
1. Install the standard c library for 32bit applications (e.g. lib32stdc++6(Debian) or ia32-libs(Ubuntu))
2. Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
Command1: mkdir /usr/lib/cups
Command2: mkdir /usr/lib/cups/filter

2-2. Create /usr/share/cups/model if it does not exist
Command: mkdir /usr/share/cups/model

3. Install the drivers using "--force-architecture" or "--force-all"option.

4. Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter

5. Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32 exists.
Command : cp /usr/lib/libbr* /usr/lib32/
```

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081)

Specifically for 64bit distro

---

### Post by MickSulley on 2010-01-07
It works!!!!!!!

Installed ia32 and followed the steps you listed.  When I installed the printer there wer two listed on the network, the first one did not work but the second one did.  I have also installed as a USB local and that works as well now.

I guess I can upgrade my desktop to Karmic now.

Thanks you very much for your help

Mick

---

### Post by Jose Catre-Vandis on 2010-01-07
Yippee :)

Please mark as solved

---

