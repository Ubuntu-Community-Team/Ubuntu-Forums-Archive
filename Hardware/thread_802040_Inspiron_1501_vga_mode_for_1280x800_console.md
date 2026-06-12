---
title: "Inspiron 1501 vga mode for 1280x800 console?"
date: 2008-05-21
forum: Hardware
---

### Post by treblemaker on 2008-05-21
Installing 8.04 on Dell Inspiron 1501 with 1280x800 display, ATI graphics.

If I give *any* value for "vga=0x###" on the kernel boot command line (at least, any that I have tried so far), I get one of two things happening:

1) blank screen until X starts

   or

2) mode is rejected as "invalid" and I'm left with an 80x25 console


*This problem appears to be specific to the Dell Inspiron 1501.  So please, understand that general solutions such as "use 'vga=ask'", or "vga=791" will not address this issue -- already tried.  And my google-fu appears to be weak, today.*


Are there any video modes that will work on this laptop other than 80-column modes?  I'd love to be able to have, for example, a 128x50 console!  But the kernel and Inspiron are conspiring against me.

Thanks and Best Regards,
T.

---

### Post by treblemaker on 2008-05-21
Just wanted to add that this laptop is using the ATI Radeon Xpress 1150 (X1150) graphics chipset. 

Is there any tool I can run that will tell me what graphics modes are supported at boot time?  "vga=ask" only gives me 80x## options, and with 1280x800 to work with I should be able to get at least 128x50!  

Thanks and Best Regards,
T.

---

### Post by treblemaker on 2008-05-21
In case anyone comes here looking for help on the same problem, I finally found this post, which shows how to use "hwinfo" to get a list of the supported video modes.

[http://ubuntuforums.org/showthread.php?t=759732&page=2&highlight=radeon+Xpress+console](http://ubuntuforums.org/showthread.php?t=759732&page=2&highlight=radeon+Xpress+console)

Best Regards,
T.

---

