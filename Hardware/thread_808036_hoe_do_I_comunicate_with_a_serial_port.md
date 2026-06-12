---
title: "hoe do I comunicate with a serial port?"
date: 2008-05-26
forum: Hardware
---

### Post by arbel on 2008-05-26
hay all.
I am in to robotics and I want to activate my robot with my serial port. so I got a serial port adapter that I connect to my robot's microconroller. and now I need to send bytes to the robot and to receive bytes from the robot to the computer. I tried to use cutecom but I don't know how to use it.
thanks
Arbel

---

### Post by arbel on 2008-05-26
bump

---

### Post by arbel on 2008-05-26
bump again

---

### Post by jak on 2008-05-26
Never done it myself but your adapter should create a device within /dev. I would assume you could then read and write from the device using a program you write, or with simple command line tools like echo and cat.
Watch dmesg for the device being created when you plug it in, and get started from there.

---

### Post by johnl on 2008-05-26
```

sudo apt-get install minicom

```

Run minicom

Press control+a, then o to access the options page, where you can setup the baud, parity, etc.

You can press control+a then q to quit.

---

### Post by johnl on 2008-05-26
> **johnl said:**
> ```

sudo apt-get install minicom

```

Run minicom

Press control+a, then o to access the options page, where you can setup the baud, parity, etc.

You can press control+a then q to quit.

Actually, I just found something that I like better :)  GtkTerm is a serial port terminal that is similar to HyperTerminal, and has a much better user interface than cutecom.  Try installing 'gtkterm' from the repositories and checking it out.

---

