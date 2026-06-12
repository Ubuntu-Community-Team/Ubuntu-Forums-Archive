---
title: "[SOLVED] USB Automount configuration"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by D4mn on 2006-10-13
Hi all.
I want to change the umask and location which the automount feature uses when pluggin my USB disk or camera, but I cannot find where this is configured.
I've been searching a lot know, but cannot find it. 

In another thread somebody spoke about adding a line to my fstab with the correct options, but when I do that, automount does not work any more with the device for which I added the entry.

](*,) ](*,) ](*,)  ....... Okay, not that bad, but it would be reallyreallyreally nice to have this changed!

Thanks !

---

### Post by dannyboy79 on 2006-10-13
> **D4mn said:**
> Hi all.
I want to change the umask and location which the automount feature uses when pluggin my USB disk or camera, but I cannot find where this is configured.
I've been searching a lot know, but cannot find it. 

In another thread somebody spoke about adding a line to my fstab with the correct options, but when I do that, automount does not work any more with the device for which I added the entry.

](*,) ](*,) ](*,)  ....... Okay, not that bad, but it would be reallyreallyreally nice to have this changed!

Thanks !

i have read thru this thread here and found that your answer lies within a few different of the posts. [http://www.linuxforums.org/forum/suse-linux-help/64671-usb-flash-hd-permission-trouble-2.html](http://www.linuxforums.org/forum/suse-linux-help/64671-usb-flash-hd-permission-trouble-2.html) 
Good luck. PS, i simply gogled "usb device mount location and permission defaults?" and found the answer, I hope it works for you.

---

### Post by D4mn on 2006-10-13
Thanks. Did that, but found so much info, I cannot really find the one matching what I need. I will check your URL's. 

Ciao !! :mrgreen: :mrgreen:

---

### Post by sprucio on 2006-11-26
Any answers? I've always wondered how automount and usb worked with permissions.

---

### Post by JPorter on 2006-11-28
Automounting does not use fstab.  Automount is a function of hal, based on the criteria listed in the .fdi files hiding at **/usr/share/hal/fdi/policy/10osvendor**

Hope this helps.

---

### Post by D4mn on 2007-08-02
Hi! Thanks a lot. 

I actually forgot about this post and use my USB drive mounted in /media and remount it to set the user rights okay.

Looking at the file 20-storage-methods.fdi I can see that I can set all properties !!

 Thanks, would NEVER have found this myself ... Mainly because it was not even clear to me how Ubuntu handles automounting.

:)

---

