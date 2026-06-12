---
title: "Boot up hangs on battery power"
date: 2009-05-10
forum: Hardware
---

### Post by chromatic.glissando on 2009-05-10
I have an HP Pavillion dv6809wm (dv6700). It's got a 64 bit processor, but I'm running Ubuntu 9.04 32 bit  for compatibility reasons.

When I'm on AC, startup and shutdown are snappy and coast along with no problems whatsoever. However when I try to startup or shutdown while on battery power, the processes have multiple snags. I have to override the hangs by hitting a key on the keyboard, otherwise the boot processes just stop. 

The battery is fine too...holds a charge well, newish laptop. This is baffling me o_O

uname -a : Linux steven-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

dmesg: [http://chromatic.izfree.com/boot.messages](http://chromatic.izfree.com/boot.messages)

^^ that should be from a boot that was hanging up.

---

### Post by chromatic.glissando on 2009-05-10
I apologize, just found a similar thread.

Wasn't able to on an earlier search

[http://ubuntuforums.org/showthread.php?t=1137421&highlight=Battery](http://ubuntuforums.org/showthread.php?t=1137421&highlight=Battery)

and

[http://ubuntuforums.org/showthread.php?t=1150854&highlight=battery+boot](http://ubuntuforums.org/showthread.php?t=1150854&highlight=battery+boot)

sort of similar :-\.

[http://ubuntuforums.org/showthread.php?t=1059545](http://ubuntuforums.org/showthread.php?t=1059545)

---

### Post by chromatic.glissando on 2009-05-11
Fixed by adding this option to the kernel options in menu.lst

acpi=noirq

not sure why it worked...but it did

---

### Post by kennethmsmith on 2009-05-19
can you please describe exactly where in the menu.lst file to add the "acpi=noirq" text?  I have an HP DV6000 series laptop with the same hang on battery boot issue.  I want to edit my menu.lst file as you stated, but not sure where to add the code.

Thanks

UPDATE:  Nevermind.... I figured out where to put it.  Thanks

---

