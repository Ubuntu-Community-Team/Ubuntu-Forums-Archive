---
title: "problems with broadcom wireless adapter on dell xps m1530--ubuntu 12.04"
date: 2012-06-18
forum: Hardware
---

### Post by kchalk on 2012-06-18
I have a Dell XPS M1530 with a broadcom bcm4311 wireless adapter.  i ran "sudo apt-get install firmware-b43-installer and still cant get the wireless working.  This command usually works in other distros.  When i enter "sudo lshw -C network", it shows the wireless as being disabled.  When I click the icon at the top, the "enable wireless" button is dim and can't be clicked.  Can anyone help me with this?  Thanks to anyone who has the time to suggest a fix and let me know if you need any more information.

---

### Post by irv on 2012-06-18
> **kchalk said:**
> I have a Dell XPS M1530 with a broadcom bcm4311 wireless adapter.  i ran "sudo apt-get install firmware-b43-installer and still cant get the wireless working.  This command usually works in other distros.  When i enter "sudo lshw -C network", it shows the wireless as being disabled.  When I click the icon at the top, the "enable wireless" button is dim and can't be clicked.  Can anyone help me with this?  Thanks to anyone who has the time to suggest a fix and let me know if you need any more information.

I have the same wifi card and I just posted a fix here:
[http://ubuntuforums.org/showthread.php?t=2005942]("http://ubuntuforums.org/showthread.php?t=2005942")

---

### Post by kchalk on 2012-06-18
Odd enough, when I turned the wireless switch on the side of the laptop off and back on again, it started working.  Maybe it was stuck.  Well, thanks for the help  anyway.

---

### Post by irv on 2012-06-18
> **kchalk said:**
> Odd enough, when I turned the wireless switch on the side of the laptop off and back on again, it started working.  Maybe it was stuck.  Well, thanks for the help  anyway.

Great, glad you got it going.

---

