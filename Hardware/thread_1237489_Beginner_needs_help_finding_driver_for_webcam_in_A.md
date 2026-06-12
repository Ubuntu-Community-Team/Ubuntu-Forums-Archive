---
title: "Beginner needs help finding driver for webcam in Averatec Buddy Netbook"
date: 2009-08-11
forum: Hardware
---

### Post by kristimyers on 2009-08-11
I am running Ubuntu 9.04 on an Averatec Buddy netbook (rebranded MSI Wind).  I can't figure out how to get the webcam to be recognized.  I am also having trouble getting the internal mic input to work.

I am a beginner with minimal command line experience, so please be kind!

Kristi

---

### Post by cariboo on 2009-08-11
The first thing we need to know is who manufactured the web-cam. To find out, open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

This will print out something that looks like this:

```
lsusb
Bus 002 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 005: ID 0665:5161  
Bus 002 Device 003: ID 045e:074f Microsoft Corp. 
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

As you can see from the above output, I have a Logitech QuickCam Messanger. Paste your output in your next post.

---

### Post by kristimyers on 2009-08-11
Here is what I got:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thanks!

---

### Post by cariboo on 2009-08-11
Unfortunately that didn't help, as your webcam is not listed. Was it turned off by any chance? To turn it on press Fn then F6 and run lsusb again.

---

### Post by kristimyers on 2009-08-11
OK, after using Fn+F6, I get this:

kristimyers@UB-NBR-netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 5986:0203 Acer, Inc 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is this helpful?  I know that my webcam worked just fine with WinXP, before I installed Ubuntu.  I overwrote WinXP completely, and now I wish I hadn't done so.  I miss my webcam.

---

### Post by kristimyers on 2009-08-22
Bump!

If anyone out there can help, I would really appreciate it!  I need that webcam and mic to work again so I can use Skype.

---

