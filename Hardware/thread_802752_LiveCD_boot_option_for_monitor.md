---
title: "LiveCD boot option for monitor?"
date: 2008-05-21
forum: Hardware
---

### Post by shawn_duggan on 2008-05-21
I'm trying to run the Hardy LiveCD on a system that has a LG222WT monitor.  It won't go past the login screen....no visible errors, it just tries to log in and goes back to the screen.  I suspect it is the monitor causing this (SuSe recognizes it).

Are there any boot options I can use to get past this?  I do have a section of xorg.conf that was given me I'm pretty sure will work, but don't want to spend the time to install if I am not sure everything else is ok.  I do realize Wubi makes it relatively painless but still...Part of me would like to broaden my knowledge of boot options also in case I run into this again.

TIA.

---

### Post by cwbar_1 on 2008-05-21
I hope I'm not steering you in the wrong direction but, try adding noapic irqpoll noirqdebug to the boot options on the initial boot screen.  Just press F6 and add to the end of the line where the cursor puts you.  (It always seems to work for me when installing on laptops that are graphically stuborn.

---

### Post by shawn_duggan on 2008-05-23
Thanks for the suggestion but unfortunately it did not work.  Oddly enough, the LiveDVD of Kubuntu picks up my monitor perfectly.

---

