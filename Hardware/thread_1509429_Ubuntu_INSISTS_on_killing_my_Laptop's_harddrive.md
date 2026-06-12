---
title: "Ubuntu INSISTS on killing my Laptop's harddrive"
date: 2010-06-14
forum: Hardware
---

### Post by lelaurent on 2010-06-14
Hello everybody,  I recently installed Ubuntu 10.4 on my brand new Eee PC 1005P.
 Thankfully, I quickly (after only about 6 hours of battery use and 2000 Spindowns) noticed that Ubuntu was killing my harddrive by idiotic power management settings.  I have not yet been able to figure out where the evil settings are stored that set 

hdparm -B 128 /dev/sda 
 on EVERY wakeup and boot (!)
  I traced the evil configuration to /usr/lib/pm-utils/power.d/95-hdparm-apm which apparently was written with the problem in mind, but still ignorant of it:    >  #On battery we set hdparm -B 128, because the head parking is # very useful for shock protection.   **No it is not!**  I edited the file to only invoke hdparm -B255, but to no avail!  Because Laptop-Mode seems to be enabled! 
 Questions:
  1) How to tell laptop-mode tools not to issue the evil idiotic command? -OR- how to permanently disable harddrive powersaving without laptop-mode installed? 
 2) This is braindead. After a default install, the harddrive is still killed slowly. This bug is from 2007. Why are the developers ignorant of it? It nearly amounts to malicious injury of the user's property and destroys any confidence I had in Ubuntu.

---

### Post by khelben1979 on 2010-06-14
Have you looked inside the BIOS if there's a possibility to change powersaving features?

---

### Post by hsoulen on 2010-06-14
Hi,

This quick article might help:

[http://atm11.wordpress.com/2009/05/08/disable-frequent-hard-disk-spindown-in-ubuntu/](http://atm11.wordpress.com/2009/05/08/disable-frequent-hard-disk-spindown-in-ubuntu/)

There are additional parameters, google can help. I have found this to be an issue with netbooks on both 9.10 and 10.04.

Cheers,

Hank

---

### Post by trekrem on 2010-06-15
> I edited the file to only invoke hdparm -B255, but to no avail!

try -B 254 as some hard drives won't recognize 255.

---

