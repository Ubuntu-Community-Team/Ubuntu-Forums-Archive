---
title: "Computer hangs, wont respond, and leaves nothing in logs"
date: 2011-08-02
forum: Hardware
---

### Post by sliverdragon37 on 2011-08-02
I've been running Ubuntu on my laptop (Asus M50vm-X1) for 3 years now, and I've had this issue maybe five or six times. I've searched around but found nothing that seems to mention this, and would be very interested if anyone else has run into something similar.

Occasionally during normal use, my computer will become completely unresponsive. The current state of the display will be preserved, but no attempts to move the cursor nor any key presses do anything. Even the raising skinny elephants trick (<alt>+<prt sc>+'r'+'s'+'e'+'i'+'u'+'b') is useless against this total and complete hang. The only thing that works to bring the computer out of this state is to hold the power button and force the BIOS to restart the computer.

I ran into this problem today, and decided to check the logs to try to figure out what could be causing it. Here I found further confusion: though I'd had the computer on almost constantly (other than a brief 30 second suspend or so) and it hand hung for a max of 5 minutes, there was a 20 minute gap in both /var/log/syslog and /var/log/messages. The entire time from waking up after suspension until hanging was simply not present in the logs. Further, the first entry in /var/log/syslog from after recovering from hanging started 'AAug  2', instead of 'Aug 2', as if something had crashed in the middle of writing to the log.

Has anyone else come across this problem, or (even better) does anyone know what's going on and have a solution?

Thanks!

---

### Post by sliverdragon37 on 2011-08-02
Twice in one day, and still nothing in the logs. Is there some kind of more aggressive kernel logging service that I could install, so that there will be more info next time it happens?

---

### Post by cha5on on 2011-08-02
Sounds like a kernel/driver issue.  Trouble is, if a kernel panic happens in this way that keeps the display stuck as-is, it's difficult to get at the cause.

What I'd ordinarily suggest is connecting another computer to the serial port and setting up the machine to write everything useful to the serial console.  However, since this is a laptop that probably doesn't have an old-style DE-9 serial port, you'd probably have to try output using USB to achieve something similar.  However, if [http://www.mail-archive.com/bug-grub@gnu.org/msg11558.html](http://www.mail-archive.com/bug-grub@gnu.org/msg11558.html) is any indication, the system might not be able to continue writing to USB after that kind of failure.  However, since there aren't really any other options, USB serial console is probably your best bet if it becomes a frequently recurring issue.

---

