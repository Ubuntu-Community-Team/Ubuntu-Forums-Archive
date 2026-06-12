---
title: "Ubuntu 7.10 won't suspend on Thinkpad T60"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by jonchan on 2007-10-20
Hi all, this is my first post on this forum and new to Linux.  I have a Windows background of many years and since using Vista decided to try something else!!  I thought of Linux, someone mentioned Ubuntu, so here we are!  Based on my last experience of Linux many moons ago, I'm pleasantly surprised with the ease of use of Ubuntu.  I've been playing with it for several weeks now experimenting with Ubuntu/Kubuntu/Xbuntu and find that Ubuntu is best for me.  

I installed 7.04 and upgraded to 7.10 on my Thinkpad T60 with Ati x1400 graphics.  Initially I had problems with suspend not working on 7.04 but trawled around the internet to finally find a solution.  However since upgrading to 7.10, the suspend function has stopped working again.  All I get when I try to suspend is that the screen goes blank and the crescent moon LED flashes continuously.  None of the fixes for 7.04 has worked on 7.10.

So has anyone else come across this problem and fixed this issue on 7.10?  The only workaround I've found for this problem is boot up using previous kernel 2.6.20.16 from Ubuntu 7.04 instead of 2.6.22.14 that comes with Ubuntu 7.10.

Thanks.

---

### Post by ColombianGold on 2007-10-20
Hey...

Im having a similar issue, in my case the crescent moon doesn't even start flashing. I tried previous fixes but no luck. All it does when I close the lid is turn of the screen.

jonchan
How did you get to boot to 7.04 kernel? All of my kernel options in grub are 7.10.

Thanks

CG

---

### Post by ColombianGold on 2007-10-20
Got it fixed...
:)

---

### Post by trippinnik on 2007-10-20
How did you get it fixed?  There's a bug report too [https://bugs.launchpad.net/bugs/134476](https://bugs.launchpad.net/bugs/134476) and I am compiling my own kernel...

---

### Post by minaev on 2007-10-20
> in my case the crescent moon doesn't even start flashing.

I have fixed this problem by editing /etc/acpi/hibernatebtn.sh. I replaced the line 

acpi_fakekey $KEY_SUSPEND

with this one:

/etc/acpi/hibernate.sh

You may want to try running the hibernate.sh by hand to check if it works before you put it into hibernatebtn.sh.

---

### Post by ColombianGold on 2007-10-20
Sorry about that...I didn't fix it...I just rolled back the kernel.
Have you had any luck?

I think this won't have a fix until ati does something...but Ill keep looking for a solution.

CG

---

### Post by trippinnik on 2007-10-20
still compiling my kernel.  I am still disapointed about the lack of feedback on the bug report.  I filed it back when it was beta, and a number of other people confirmed.  Unfortunately the issue that's reported on the release notes only affects the ATI proprietary driver.

---

### Post by trippinnik on 2007-10-22
No, I can't seem to figure out which configuration part is different in the kernel.  can you post the .config file from to old kernel (I did a clean install so I don't have it).
you can get it with this command: sudo cp /boot/config-`uname -r` ./home/<yourusername>/Desktop/config

---

### Post by faif on 2007-10-24
I can use suspend mode now if I disable ATI restricted driver.
xorg use vesa driver by default.
Just waiting for ATI update driver or opensource ATI driver.

---

