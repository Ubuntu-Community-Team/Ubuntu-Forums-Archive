---
title: "Grub won´t load"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by Dekkzter on 2008-12-26
Hello

I´m installing Ubuntu 8.10 on my computer. I have Windows 2008 Server Enterprise on there since earlier and am installing Ubuntu 8.10 on the second partition on the first drive. The install is no problem and I chose to install Grub but it simply won´t load. It boots straight back into Windows.

Any ideas? 

Thx Jimmie

---

### Post by albinootje on 2008-12-26
> **Dekkzter said:**
>  I´m installing Ubuntu 8.10 on my computer. I have Windows 2008 Server Enterprise on there since earlier and am installing Ubuntu 8.10 on the second partition on the first drive. The install is no problem and I chose to install Grub but it simply won´t load. It boots straight back into Windows.

So there's no grub menu visible at all ?
Do you have some anti-virus protection on in the BIOS which prevents overwriting the MasterBootRecord ?

You can still follow these steps to try to fix it :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by pietjanjaap on 2008-12-26
Change your boot disk, you have choosen the wrong one.

---

### Post by caljohnsmith on 2008-12-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by Dekkzter on 2008-12-27
That was a long file so I made an attachment. I hope anybody can help me with that :)

---

### Post by didac on 2008-12-27
It looks your BIOS setup is set to boot from the third hard-disk, not the first, where GRUB is installed. Check your BIOS at boot.

---

### Post by caljohnsmith on 2008-12-27
> **didac said:**
> It looks your BIOS setup is set to boot from the third hard-disk, not the first, where GRUB is installed. Check your BIOS at boot.
+1. I agree, if you are booting straight into Windows right now, Dekkzter, it looks like you would have to be booting the sdc drive since that is where Vista has its boot files. Can you change your BIOS to boot the sda drive? That should hopefully be all it takes to at least boot Ubuntu, but booting Vista/XP from the Grub menu may need some tweaking to work.

---

### Post by Dekkzter on 2008-12-27
Yea. it worked when I changed boot disc in BIOS. and the grub loaded and i could chose Windows Vista and Ubuntu and both started without problem! Thx alot for the help! :)

---

### Post by caljohnsmith on 2008-12-27
I'm glad that changing your boot drive was all that it took to fix the problem; cheers and have fun with Vista and Ubuntu. :)

---

