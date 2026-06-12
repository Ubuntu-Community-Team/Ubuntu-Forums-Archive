---
title: "Serial port problems and questions"
date: 2009-02-24
forum: Hardware
---

### Post by leachja on 2009-02-24
I've been looking at doing some serial port programming. I've done a ton of research and I've finally got a computer that I can use to test what I've been programming. After reading and coding a week or so, I am still unable to get any non-standard baud rates to change. Setserial doesn't seem to be changing my baud rate at all actually. I'll set it to have a divisor of 16 and base_baud of 115200 on one computer and divisor of 32 and base of 38400 and they communicate perfectly which should not be happening.

My end goal is to be able to communicate with an old piece of hardware that is operating at around 3600 baud, if anyone has any hints I'd appreciate it. I've read the POSIX serial programming guide and a few other guides and it just doesn't seem like what they have working is working for me.

Thanks in advance.

---

### Post by dreesthomas on 2009-12-12
Did you ever find an answer to the non-standard serial bit rate question?  I'm in the same position, except need 16667 bps +/- (a divisor of 7 would do the trick if I could make it stick).

David

---

