---
title: "Screen Brightness not working."
date: 2012-06-15
forum: Hardware
---

### Post by kiwimenace on 2012-06-15
Laptop(netbook) in question is a                           Toshiba NB550D/02F PLL5FA-02F02C(amd c60/hd 6290).

I have searched quite a bit but to no luck. My problem is that i cannot set the brightness with the FN keys. The keys work, as in the wee indicter slider pops up in the top right of the screen and slides up or down as i try to change the brightness but the brightness does not change.

I hope somebody has a solution for this. Thanks in advance.

---

### Post by Toz on 2012-06-15
According to here: [http://www.kubuntuforums.net/showthread.php?58370-Precise-on-the-Toshiba-NB550D]("http://www.kubuntuforums.net/showthread.php?58370-Precise-on-the-Toshiba-NB550D"), blacklisting the toshiba_acpi module fixed the problem. To do so, add:
```
blacklist toshiba_acpi
```
...to the end of **/etc/modprobe.d/blacklist.conf** and reboot.

If that doesn't work, you could try using the **acpi_backlight=vendor** kernel parameter

---

### Post by kiwimenace on 2012-06-15
Neither of those options worked.

Anybody else got any ideas?

---

### Post by hexion on 2012-06-16
Check the instructions here: [http://ubuntuforums.org/showthread.php?t=1985757](http://ubuntuforums.org/showthread.php?t=1985757)

---

### Post by newboon2 on 2012-06-16
> **hexion said:**
> Check the instructions here: [http://ubuntuforums.org/showthread.php?t=1985757](http://ubuntuforums.org/showthread.php?t=1985757)

My Toshiba NB555D (older model than the OP's, with AMD C30; Radeon HD 6250) exhibited the same issue after upgrading from 11.10 to 12.04.

The instructions in the linked thread fixed it for me.

Thanks!

---

### Post by kiwimenace on 2012-06-17
Still not luck guys. Thanks for the suggestions so far though.

I might actually do a fresh install of 12.04 anyway, this one has been a bit experimental so it a bit messy. Never know some of these solutions may even work after that who knows.

Keep those suggestions coming if your reading though.

cheers

---

### Post by kiwimenace on 2012-06-17
Right, I did a fresh install 12.04 ubuntu(not lubuntu as this thread is tagged as, not sure why that is). 
It worked!
Installed ati catalyst driver.
It stopped working!
Installed ati catalyst driver update.
It worked

So great i have brightness control again!

Thanks for taking the time to help me out guys, greatly appreciated.

---

### Post by kiwimenace on 2012-06-18
I take it all back. It stopped working.

I did the three steps in the linked solution and it appears to have fixed it for now(fingers crossed).

If it has fixed it I will come back in a week or so and mark this solved.

Again, many thanks to the community for there inputs.

---

