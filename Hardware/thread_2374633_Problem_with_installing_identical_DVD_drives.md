---
title: "Problem with installing identical DVD drives"
date: 2017-10-17
forum: Hardware
---

### Post by dschaller on 2017-10-17
I recently installed a second DVD burner exactly like the one I already had installed. Ubuntu, however, only sees one DVD drive since they are identical and thus creates only /dev/sr0. I found the thread below, which I believe addresses the problem, but replacing the 60-cdrom-id.rules file in /lib/udev/rules.d with the proposed file in the thread did not solve it for me. It still doesn't create a second device. Maybe I put the file in the wrong place?

[https://ubuntuforums.org/showthread.php?t=2250891](https://ubuntuforums.org/showthread.php?t=2250891)

Anybody know best how to work around this little but of nuisance?

---

### Post by Autodave on 2017-10-17
I have 3 identical drives in one machine with no issues and no file modifications.  Does your BIOS see both DVD drives? If not, you have a bad DVD drive, cable, or port probably.

---

### Post by dschaller on 2017-10-17
Yes, the BIOS sees both drives just fine. They show up with exactly the same name, one on SATA4 and one on SATA5. That's why I thought it must be an ID problem.

---

### Post by Autodave on 2017-10-17
What happens when you insert a disc into the unrecognized drive?

---

### Post by dschaller on 2017-10-30
It's very strange. It will see it as a blank disc (even if it isn't), and when I eject it, it opens the tray on the wrong (empty) drive.

---

### Post by dschaller on 2017-10-30
I got things to work using the modified 60-cdrom-id.rules file mentioned in the initial post. However, I mistakenly put it in /lib/udev and it was overwritten when I rebooted, so I need to put it somewhere safer. It does seem to be the case that the udev rules do not anticipate two installed drives returning the same serial number string.

---

