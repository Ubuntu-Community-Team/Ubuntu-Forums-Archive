---
title: "Sony emory Stick Laptop Port Problems"
date: 2008-11-02
forum: Hardware
---

### Post by MikeyDL on 2008-11-02
I rebuilt a 1.5 Year old Dell 1420 laptop with Ubuntu 8.10 and have been very happy with the driver support.  8.10 picked up my built in webcam laptop specific buttons like sound up/down ect.  However, decided to import some pictures off my Sony memory stick pro and found that when I plugged in the memory stick into the laptop port it didn't load the device in ubuntu.  

Was trying to search for some help but didn't couldn't find anything on this subject.  Does anybody have an information on how to get these devices to work?

Thanks!

---

### Post by ahumin on 2008-11-06
I have the same problem in an Inspiron 1520. The controller is a Ricoh R5C822 (according to lspci). It picks up SD cards fine but I get nothing when inserting a memory stick pro. I don't even get any error from dmesg.

---

### Post by jbernardo on 2008-11-06
The (experimental) MS module isn't built in the ubuntu kernels. You need to build your own module from the kernel sources. :(

---

