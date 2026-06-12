---
title: "Allow read-only automounting"
date: 2009-06-08
forum: Hardware
---

### Post by pmgeahan on 2009-06-08
Folks - 

My office uses a hardware write-blocking unit to review hard drives.  This unit is basically an external hard drive carriage, but it's guaranteed to not allow anyone to write to it.  

Here's my issue - when I plug the unit into my Ubuntu box(9.04, standard install), it recognizes the drives and the partitions, and tries to auto-mount them.  It then throws an error, because it can't mount the drives read-write.  I can then go to the command line and mount it ro manually, and everything is peachy.

So here's my question - I want to be able to plug these in and have them automount, even though it'll be mounting read-only.  I'd even be happy with this machine mounting everything read-only, since we really only use it for this purpose.

Is there a setting somewhere that'll allow this?  

Thanks for the help.

---

