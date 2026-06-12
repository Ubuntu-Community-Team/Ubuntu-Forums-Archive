---
title: "[B]installing ATI drivers crashes Ubuntu 9.04[/B]"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by andy08 on 2009-04-26
Hello, 
I installed Ubuntu 9.04 without any problems. Video didn't run. So I search for ATI display driver. I found info to look into Synaptic package manger and look for envy. I installed the packages and restarted. Ubuntu seemed to start-up normal until it comes to the desktop. The desktop backgrond appears half three times before it changes to the black screen and I have to reboot. Live cd won't work either, Recovery the system didn't help.I could only install Ubuntu new.

I downloaded the newest ATI driver for my graphic card for Linux (ati-driver…installer-9-3-x86.x86_64.run), but the system tells me "gedit has not been able to detect the character coding".

Sound no problems, but no video. 

Thanks for your help.

---

### Post by Randati on 2009-04-26
You need to run installer
```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

---

### Post by andy08 on 2009-04-26
Hi thanks for your quick answer.
I tried this. The answer:sh: Can't open ati-driver-installer-9-3-x86.x86_64.run

---

### Post by Randati on 2009-04-26
I'm not sure about installer's name. Change it to right and it should work.

---

### Post by andy08 on 2009-04-26
sorry, I'm not a pro. Do you mean sudo sh ati-driver-r-9-3-x86.x86_64.run ?

Thanks

---

### Post by Randati on 2009-04-26
Yes, that is right file.

---

### Post by andy08 on 2009-04-26
sorry same result. can't open.

---

### Post by Randati on 2009-04-26
Are you sure that you are in same folder that where that file is (cd /right/folder)? And file name is that what you downloaded from ATI?

---

### Post by andy08 on 2009-04-26
This might be the problem. I stored the download on my desktop. Does it matter? The name is correct.

---

### Post by StuartN on 2009-04-26
> **Randati said:**
> You need to run installer
```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

ATI Catalyst 9.3 or older will crash your Ubuntu 9.04. See this thread for the result, and how to recover: [http://ubuntuforums.org/showthread.php?t=1133931&highlight=fglrx+sudo](http://ubuntuforums.org/showthread.php?t=1133931&highlight=fglrx+sudo)

---

### Post by andy08 on 2009-04-26
Thanks Stuart,

I'm reading it.

---

### Post by leere68 on 2009-04-28
ok, so I've got Jaunty installed in Virtual Box on Vista.  I'm a linux newbie and when I tried installing the ATI 9.4 drivers (I have a Radeon 3870), the installer would open and then I would get an error message telling me that vcdk is missing.

What is vcdk and how do I fix this?

---

