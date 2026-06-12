---
title: "USB / HIbernate / Sound problems related to Logitech web cam"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by SideShowFry on 2005-07-28
(Warning: I'm a complete linux noob)

FYI, FWIW, etc:

After installing Ubuntu (first linux install ever) neither Hibernate nor sound worked.  After a few hours of hunting around, I found that the hibernate script hung when attempting to rmmod ohci_hcd.  I also noticed that the web cam was coming up as an audio device.  So, I unplugged my web cam, and now both hibernate and sound work fine.

It seems like this might be useful info to somebody who might want to fix support for the web cam, and / or the overall USB / hibernate / sound problems, but I don't know where to post it.  Hopefully, someone with the same problem might find this, at least.

---

### Post by dave9191 on 2005-07-28
The hibernate and suspend features in linux are still fairly fresh and still in a work in progress. The work on some machines but not others. You might find that with a future release these problems will clear up :)

Dave

---

