---
title: "Drivers"
date: 2012-04-05
forum: Hardware
---

### Post by Harris6310 on 2012-04-05
Hello, I have just installed Ubuntu 10.04 on my laptop and I would like to know how to get the drivers I need. My laptop has an AMD APU, so I will need a display driver for that. And my wireless isn't working, so I will need a driver for that. Where can I get these from? System > Administration > Hardware Drivers just displays blank.

---

### Post by kc1di on 2012-04-05
first do you know what your wireless card is?
you can find it by typing the following in a terminal
```
lspci
```

If it's a broadcom you'll need to install some drivers for it. 
your looking for a line that says something like this:

```
 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

---

### Post by Harris6310 on 2012-04-05
This is what I'm getting.

> RaLink Device 5390

---

### Post by Harris6310 on 2012-04-05
I have installed a display driver from the AMD website but still not able to use wireless.

---

### Post by kc1di on 2012-04-05
here's a link to a thread that may lead you to the answer. Sorry I'm at work now and can't research it further at the moment.

[http://ubuntuforums.org/showthread.php?t=1855675]("http://ubuntuforums.org/showthread.php?t=1855675")

---

### Post by Harris6310 on 2012-04-05
> **kc1di said:**
> here's a link to a thread that may lead you to the answer. Sorry I'm at work now and can't research it further at the moment.

[http://ubuntuforums.org/showthread.php?t=1855675](http://ubuntuforums.org/showthread.php?t=1855675)

I will have a look through it.

I have also noticed that I have no sound either.

---

### Post by Harris6310 on 2012-04-05
I looked through that post and it did not make any sense to me. What do I have to do to install the driver?

---

### Post by Harris6310 on 2012-04-06
Bump, can anyone help me?

---

### Post by Mark Phelps on 2012-04-06
> **Harris6310 said:**
> I will have a look through it.

I have also noticed that I have no sound either.

Please don't start adding problem after problem to the same thread.  That just makes it real confusing to keep the solutions and approaches seperate.  Please start a separate thread for each problem -- as they are likely to require very different solutions.

---

### Post by Mark Phelps on 2012-04-06
> **Harris6310 said:**
> I looked through that post and it did not make any sense to me. What do I have to do to install the driver?

You will have to download driver source code and then follow the details to build a kernel module from those, and then bind that module to the kernel.

If it sounds complicated, that's because it is.

You have to do a LOT of work to get the drivers installed -- as the thread indicates.  This is not MS Windows where you stick in a driver disk, or run Windows Update and -- then you're done.

If you're not up to using the command line and building modules, then you're not going to be able to install the driver.

---

### Post by Yellow Pasque on 2012-04-06
> **Harris6310 said:**
> I looked through that post and it did not make any sense to me. What do I have to do to install the driver?
Copy/paste the 6 commands here into the terminal: [http://forum.ubuntuusers.de/post/3473742/](http://forum.ubuntuusers.de/post/3473742/)

---

