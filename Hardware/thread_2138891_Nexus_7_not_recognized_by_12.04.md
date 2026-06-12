---
title: "Nexus 7 not recognized by 12.04"
date: 2013-04-25
forum: Hardware
---

### Post by Jack Fisher on 2013-04-25
12.04 LTS 64 bit won't recognize my Nexus 7. I just tried running 13.04 from the install disk and it did recognize it. How do I get 12.04 to recognize the Nexux 7 so I can add and delete books from it?

---

### Post by Mark Phelps on 2013-04-25
You probably can't.  From what I've read, 13.04 includes improved versions of the drivers needed to see Android phones with newer versions of the OS (ICS and newer).

I've tried using 12.04 and 12.10 to see my Samsung S3 (with JB) -- and they will not work.

---

### Post by Jack Fisher on 2013-04-25
Thanks for the response. I kinda figured that, but was hoping...

---

### Post by Isamu715 on 2013-04-25
I got 12.04 to recognize my Nexus 7 by following this [tutorial]("http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html"), it worked without any problems and the device shows up in Nautilus properly. Another way is to set your Nexus USB connection mode to digital camera(PTP), it'll work in 12.04 but you'll only be able to access the Pictures folder and will need to move files directly on the device with an Android file manager(OI File Manager is a good choice).

---

### Post by Jack Fisher on 2013-04-26
Thank you. I tried the tutorial but got hung up over permissions for the script. I need to do some more reading about the file system.

---

### Post by Isamu715 on 2013-04-26
What script are you talking about? The tutorial is basically about adding a PPA and updating your system.
You should be fine with just:
```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
sudo apt-get upgrade
```
and reboot.

Come to think of it I could've just given you these commands instead of sending you to the tutorial.

---

### Post by Jack Fisher on 2013-04-27
Thank you, but I already took the quick way out. I upgraded to xubuntu 13.04. It recognizes everythin and has the extra benifit of being familar to me from when I was using Linux in 2009 and 10. I really appreciate the attention you gave me though.

---

