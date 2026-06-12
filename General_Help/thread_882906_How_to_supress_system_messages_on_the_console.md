---
title: "How to supress system messages on the console?"
date: 2008-08-07
forum: General Help
---

### Post by delcour on 2008-08-07
Hello,

I want to use vim at the console because I want not to disturbed by any blinking or color or popups and so on to be able to concentrate for 100% on my own thought and text.

But there are appearing system messages overwriting my text. Actually the system messages is somewhat about IRQ 21 and I shall use irqpoll as boot parameter. I do not want to see this or other system messages when I use vim to write important (at least for me) stuff which requires my full concentration.

How do I get rid of this annoying system messages?

Thank you in advance.

Delcour

---

### Post by cmnorton on 2008-08-07
You will have to re-configure the syslog facility. I cannot imagine you would want to suppress every message.

If you search for syslog facility and/or syslog.conf, you will find tons of posts.

---

### Post by unutbu on 2008-08-07
Try pressing Ctrl-Alt-F2 instead of Ctrl-Alt-F1.
Many programs during the boot process have output tied to the first virtual console (what you see when you press Ctrl-Alt-F1). The vc you get when you press Ctrl-Alt-F2 should be nice and quiet.

---

### Post by delcour on 2008-08-22
I always use Ctrl+Alt+F2 or ascending. 

In /etc/sysctl.conf I will change the line

kernel.printk = 4 4 1 7

to

kernel.printk = 2 4 1 7

I really do not want to see any message beeing written on the screen while  work. If I would use Gnome there I would also not see the messages on the console. Using Gnome I never saw an IRQ-21 message as appears from time to time at console.

Thank you for your hints.

---

