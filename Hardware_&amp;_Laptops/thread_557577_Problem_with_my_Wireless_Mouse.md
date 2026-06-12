---
title: "Problem with my Wireless Mouse"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by Neo40 on 2007-09-22
Hi,

I bought a new HP dv2410 laptop and I also bought a RetailPlus wireless mouse.
The mouse works when using Windows but doesn't with Ubuntu.
Anyone has a idea how I can fix it?

Thanks!

EDIT: Don't know what I did but works now after reboot! :)

---

### Post by w4ett on 2007-09-22
The first step is to ensure your mouse is being recognized by Ubuntu.....boot up and in the terminal type:

```
lsusb
```

and see if in the output of the command you see this:

> w4ett@w4ett-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 050d:705c Belkin Components 
Bus 002 Device 004: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 002 Device 003: ID 043d:0100 Lexmark International, Inc. 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000  
[COLOR="Blue"]Bus 001 Device 003: ID 045e:00e1 Microsoft Corp. [/COLOR]
Bus 001 Device 001: ID 0000:0000  
w4ett@w4ett-desktop:~$ 



Yours won't look the same, (I have a MSsoft wireless mouse on this system).....

---

### Post by jyu617 on 2007-10-14
> **w4ett said:**
> The first step is to ensure your mouse is being recognized by Ubuntu.....boot up and in the terminal type:

```
lsusb
```

and see if in the output of the command you see this:




Yours won't look the same, (I have a MSsoft wireless mouse on this system).....

I have the same issue setting up my wireless mouse.  The output of lsusb shows that the mouse is being detected.  What do I do next to get it working?  

Thanks!

---

### Post by VVebbie on 2007-10-16
Edit: never mind, it was resolved.

---

### Post by Joeb454 on 2007-10-16
Please mark the thread as solved :)

---

### Post by jyu617 on 2007-11-02
I don't believe this thread is solved.  

What are the next steps after determining if the mouse is being detected?

Thanks!

---

