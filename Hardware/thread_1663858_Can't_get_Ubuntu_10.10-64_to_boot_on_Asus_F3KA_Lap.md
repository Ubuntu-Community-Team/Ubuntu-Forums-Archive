---
title: "Can't get Ubuntu 10.10-64 to boot on Asus F3KA Laptop"
date: 2011-01-10
forum: Hardware
---

### Post by c1k2j3c4 on 2011-01-10
I have a Asus F3KA laptop that uses a ATI 2600 mobile video card. The problem I am having is I can't Ubuntu 10.10-64 to boot. Ubuntu 10.10 will get as far as showing Ready with a blinking cursor and then goes black. I tried different media, downloads and burn speeds and no joy. All my burns work fine on my desktop computer so I know it not the disks. From the searching I have done the problem points to my ATI card, but unless I missed something I haven't found a solution. Does anyone know of a solution? I would really like to get Ubuntu 10.10 working on my laptop.

I should mention Ubuntu 10.04-64 boots a funs fine on my laptop. Mint 10 gives me the same problem. Thanks in advance!

---

### Post by c1k2j3c4 on 2011-01-12
Well I have given up on Mint 10 or even Ubuntu 10.10. I have put in too many hours trying to get Mint 10 or Ubuntu 10.10 to work and now I have probably worn out my dvd drive with all the installing I've done. Too bad, but I should have known. I have never been able to get any of the October releases of Ubuntu to work on my laptop since I bought it. 8.10, 9.10 and now 10.10 can be added to my list.

---

### Post by IcarusR on 2011-01-13
Did you try the kernel option 'nomodeset' this resolves your problem on a number of machines.

Instructions here...

[http://ohioloco.ubuntuforums.org/showthread.php?t=1613132]("http://ohioloco.ubuntuforums.org/showthread.php?t=1613132")

---

### Post by c1k2j3c4 on 2011-01-16
> **IcarusR said:**
> Did you try the kernel option 'nomodeset' this resolves your problem on a number of machines.

Instructions here...

[http://ohioloco.ubuntuforums.org/showthread.php?t=1613132]("http://ohioloco.ubuntuforums.org/showthread.php?t=1613132")

Thanks for the link. Thats is one I didn't find. Anyways yes I have. As a matter of fact if I delete "quiet splash" and insert "ro nomodset single" I can boot to the desktop using failsafe settings. Once I install the ATI drivers it boots to the command line. Typing startx gives me a "no screens found" error. Haven't found any cures that work yet.

---

