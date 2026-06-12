---
title: "Blank screen after using nvidia driver"
date: 2008-12-21
forum: Hardware
---

### Post by cencorot_91 on 2008-12-21
hello.
i am using intrepid on my dell inspiron 2650 with geforce2 go video card. When i use the nvidia driver, my screen goes blank. I can see the ubuntu logo on startup but when it proceed to login screen, it goes blank. I had to disable the driver. Is there any way i can use the driver so that i can enable all the eye candy on ubuntu?

---

### Post by cencorot_91 on 2008-12-21
no one knows??
hmm.....

---

### Post by sop408 on 2008-12-28
I use the same laptop. I don't think there isn't any solutions to that problem.
If you find out any, please post it.
Thank you.

---

### Post by kingocounty on 2009-01-04
Hello all, this is my first post as I'm a brand new Linux user and just bought an Inspiron 2650 to run it on.  I'm having this same video problem and thought I'd give this post a bump.  I don't even really need the full functionality of the card but I'd love to be able to change my screen resolution to something higher than 800x600.  Thanks in advance for any help!

---

### Post by cencorot_91 on 2009-01-14
I've found the solution!!

1. Add this line into /etc/modprobe.d/options 
```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=2
```

2.Install nvidia-kernel-common from synaptic package manager.
3.Activate the nvidia driver and restart computer

I'm new in ubuntu and if anything bad happen to your computer dont blame me. At least this solution work for me. :p :p

---

### Post by sop408 on 2009-01-14
I'll have a go tomorrow morning.
I will post the results.

---

### Post by rabbitreduxx on 2009-03-16
That did the trick. Adds like 2 more seconds to total boot time, but whatever. Thanks cencorot_91.

---

