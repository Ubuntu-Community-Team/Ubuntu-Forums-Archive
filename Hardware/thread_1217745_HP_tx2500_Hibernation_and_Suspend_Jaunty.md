---
title: "HP tx2500 Hibernation and Suspend Jaunty"
date: 2009-07-19
forum: Hardware
---

### Post by cenzorrll on 2009-07-19
Hi, I have an HP tx2525 with ubuntu 9.04 jaunty.  i've gotten everything to work that i care about (touchscreen, wacom, sound) but it doesn't seem that anybody has been able to fix the hibernation and suspend problem.

the system goes into hibernation and suspend just fine, the problem is when i try to start up again.

when coming back from hibernation the video drivers seem to fail and i get a few green bars at the top, after about a minute longer it appears to try to load a login screen (small grey window with a white bar) like when coming back from suspend. i can move the mouse, but there is no place to input.

with suspend, the login screen comes up but i can't input anything.  keyboard doesn't work and mouse doesn't work. <solved>

any help would be appreciated

---

### Post by cenzorrll on 2009-07-19
aha, i found the solution to the suspend problem. it involved editing /boot/grub/menu.lst

however i'm still having trouble with hibernation.

---

### Post by ajr901 on 2009-07-22
> **cenzorrll said:**
> aha, i found the solution to the suspend problem. it involved editing /boot/grub/menu.lst

however i'm still having trouble with hibernation.

so can you please post the solution? i have the same problem.

---

### Post by chadmerkert on 2009-07-25
Hey  ajr901

This is how i got the suspend and resume working on my tx2500z:

[http://ubuntuforums.org/showpost.php?p=6189450&postcount=374]("http://ubuntuforums.org/showpost.php?p=6189450&postcount=374")

---

### Post by ajr901 on 2009-07-28
> **chadmerkert said:**
> Hey  ajr901

This is how i got the suspend and resume working on my tx2500z:

[http://ubuntuforums.org/showpost.php?p=6189450&postcount=374]("http://ubuntuforums.org/showpost.php?p=6189450&postcount=374")


thanks a million!

---

### Post by cenzorrll on 2009-10-30
i'm marking this thread as solved as hibernation and suspend both work in 9.10

to get suspend to work it's a similar process as above, just a different file. read the Grub2 thread to get help with this.

---

### Post by Docaltmed on 2009-10-31
> **cenzorrll said:**
> i'm marking this thread as solved as hibernation and suspend both work in 9.10

to get suspend to work it's a similar process as above, just a different file. read the Grub2 thread to get help with this.

Having problems finding Grub2 thread you reference. Any links?

---

### Post by cenzorrll on 2009-11-01
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+tips]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+tips")

link to the grub 2 page.

the file i edited was /etc/default/grub
and the line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"

---

