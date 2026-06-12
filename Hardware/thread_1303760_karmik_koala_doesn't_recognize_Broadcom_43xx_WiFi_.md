---
title: "karmik koala doesn't recognize Broadcom 43xx WiFi adapter"
date: 2009-10-28
forum: Hardware
---

### Post by SOULTE on 2009-10-28
hi there. 
I've downloaded and installed kubuntu karmic koala RC. It doesn't work with my Broadcom 43xx wifi adapter. I even tried to load with linuxant.com driver loader script but it says there is no 43xx card exist! ](*,)
What is wrong with that? Is it becos of RC release or just karmic?

I've attached kernel messages log too.

---

### Post by Giblet5 on 2009-10-28
It's because the broadcom chip isn't supported by the kernel.

[This link]("http://ubuntuforums.org/showthread.php?t=405990") has helped a lot of people. If it helps you, then please reply and mark this thread (SOLVED).

---

### Post by Ayuthia on 2009-10-28
The dmesg information shows that the b43 module does not support this chipset yet.  However the Broadcom STA module should work for you.  You should be able to find the Broadcom STA module in System->Administration->Hardware Drivers.  It might need an internet connection to get it activated.  Hopefully that is just a RC/beta thing because normally it does not need one.

---

### Post by SOULTE on 2009-10-30
i justed installed the final version of ubuntu karmic & saw there isn't support for 43xx in kernel no more! it's a bit strange cos the previous versions support it. gonna test the solutions you have suggested...

---

### Post by drbobb on 2009-10-30
To make a bcm43xx work generally requires you to install a package called b43-fwcutter. I don't know why this isn't handled in a more user-friendly fashion. After that, at least my bcm4318 works fine.

---

### Post by Ayuthia on 2009-10-30
> **drbobb said:**
> To make a bcm43xx work generally requires you to install a package called b43-fwcutter. I don't know why this isn't handled in a more user-friendly fashion. After that, at least my bcm4318 works fine.

b43-fwcutter works for most of the Broadcom chipsets, but the one that the original poster has is not supported (14e4:4315).  The Broadcom STA driver and the NDISwrapper driver are the only options.

Hopefully the open-source firmware can soon be implemented into Ubuntu so that some of the Broadcom cards will just work out of the box.

---

### Post by drbobb on 2009-10-30
Oh I'm sorry, I didn't read the log he attached before posting.

---

