---
title: "Hardy won't shut down or reboot"
date: 2008-10-31
forum: General Help
---

### Post by mojohn on 2008-10-31
I tried to post this message at [http://ubuntuforums.org/showthread.php?t=347601](http://ubuntuforums.org/showthread.php?t=347601), but was informed it's read-only. So, I decided to post it here.

I don't know when it happened, but for some reason, Hardy won't reboot or shut down unless I enter sudo init 0 or sudo init 6 in the terminal. This is a bit of a hassle, so I created two scripts, named them .reboot and .shutdown, saved them in my home directory, and made them executable. Then, I created two launchers, with nice icons, of type "application", and the path to the appropriate script. 

Because I didn't want to have to enter my password each time, I edited my /etc/sudoers list and added the following line: 

john ALL=NOPASSWD: /home/john/.reboot,/home/john/.shutdown

But, my launchers won't work. I can still go in through terminal, type the appropriate init command, and the machine will shutdown or reboot as expected. Any ideas why my launchers won't work?

Thanks, mojohn

---

### Post by lordmyth on 2008-10-31
my install won't shutdown either, the last output is "acpid exiting". I think it actually completes the proper shutdown sequence but never powers off

making silly hacks isn't what you're supposed to do mojohn :P

---

