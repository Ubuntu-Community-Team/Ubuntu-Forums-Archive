---
title: "boot resolution issue and how i solved it"
date: 2008-11-01
forum: General Help
---

### Post by Guest_Jim_* on 2008-11-01
Not sure if this has affected anyone else, but just in case I will put it up.
I upgraded from 8.04 to 8.10 today by mounting the alternate from the desktop. When it rebooted the monitor put up a message (after having said to boot into Ubuntu in Grub) saying the frequency was wrong and to either change it or read the manual. It is possible that Intrepid was booting up anyway, but I had no way of knowing.
I searched around on the forums and found this thread, [Terminal Resolution]("http://ubuntuforums.org/showthread.php?t=239970"). In order to make the change to the menu.lst file I had to burn a copy of the regular install disc and boot into the LiveCD. I then found the file and added the vga=791 and now Intrepid has booted up fine.

---

