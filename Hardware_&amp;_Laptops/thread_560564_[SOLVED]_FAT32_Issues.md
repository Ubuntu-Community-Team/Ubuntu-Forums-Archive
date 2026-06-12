---
title: "[SOLVED] FAT32 Issues"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by Fingers &amp; Thumbs on 2007-09-26
Hello,
   I use a handheld audio recorder, namely the Edirol R-1,  which uses compact flash cards.
I have used this with ubuntu in the past, with no problems, but having not used it for a while, I've come to use it again and it comes up with the message "Unable to mount volume". Checking syslog, using dmesg |tail and I find that it is attempting to mount it using NTFS. 
   I have installed NTFS config since I last used the unit, could this be the problem?

I dunno,

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by geraldm on 2007-09-26
You found a problem others have already encountered.
There is an answer in this thread:
[http://ubuntuforums.org/showthread.php?t=488330](http://ubuntuforums.org/showthread.php?t=488330)

And the followup for mounting repeatedly, rather than once:
betterway is what I found on this ubuntu page

use this for mounting ntfs volumes that are internal and for external usb ntfs volumes just let it auto mount and then click properties and set it as writeable.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) 

Gerald

---

