---
title: "Why can't I cat /dev/tty* or /dev/pts/*?"
date: 2008-11-08
forum: General Help
---

### Post by damis648 on 2008-11-08
Whenever I try to cat a tty only random characters come through, some stay in the tty and some come through, but nothing very consistent, and each character only appears once. Either with cat or in the tty. I've never actually tried to do this before... is this just the way it usually is?

---

### Post by bab1 on 2008-11-08
These are special files.  They interface block or character based devices to the OS.  They are not for users to read or manipulate. 

See [[COLOR="Red"]**this**[/COLOR]]("http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/").

---

### Post by gpsmikey on 2008-11-09
If the baud rate is correct, it actually can work -- I have experimented with my hot tub controller that sends out data at 9600 baud and when plugged into /dev/ttyS0, I can cat that "file" and see the data when it comes in every minute or so.  You do have to have the baud rate correct as well as the correct parity, #bits as well as the handshake (or none) correctly set up for it to work.

mikey

---

