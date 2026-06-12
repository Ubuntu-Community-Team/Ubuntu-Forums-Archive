---
title: "After waking up, keyboard has space bar or a number stuck"
date: 2016-09-09
forum: Hardware
---

### Post by ryaninteresting on 2016-09-09
I have the system set to sleep after 30 minutes of inactivity.  After I wake it up, the space bar or a number will be stuck.  So wherever the cursor is, a bunch of spaces or a bunch of numbers will be typed continuously, until I hit something on the keyboard.  This is especially problematic if I had a window open for something important.  Just now, I woke the computer up and a bunch of "4"'s got typed in my code in the PyCharm window.  I closed one tab, and more "4"'s got typed in the next tab.  It didn't stop until I pushed something on the keyboard.  I thought that upgrading from Ubuntu 14 to 15 would help, but the problem persists.

I'm using a Microsoft ergonomic keyboard.  It's old, so it has a PS/2 connector.  I use a PS/2 to USB adapter to connect it to the PC.  Is this a potential cause?

Any help appreciated!

---

### Post by DuckHook on 2016-09-11
Welcome to the forums, ryaninteresting.

It is possible that your old keyboard could be the culprit. Especially the PS/2 connector. I had an old MS Ergonomic that caused all sorts of kernel interrupts when PS/2 was plugged in. But mine had a native USB connector separate from the PS/2, so it worked well as long as I kept to USB and didn't plug in PS/2. Your hybrid connection *might* be the problem (only might). It should be easy to find out. Just borrow a pure USB keyboard from a friend (or another computer) for a day and see if the problem persists. If it goes away, then you know the problem is your keyboard and you may wish to replace it.

You can also take a look at your syslog (located at /var/log/syslog). It may show a lot of wonky keyboard interrupts. If so, then this is also a big clue that the keyboard is the culprit.

Last but not least, all Ubuntu 15.x versions are now out of support. If you want to try the keyboard on an upgraded system, go all the way to 16.04 to see if that helps. Frankly, I doubt the OS is your problem, but you can always try. If trying, don't upgrade (which may inherit a wonky config file that may be the cause of your problem). Instead, run a session from LiveUSB/DVD and test that way.

---

