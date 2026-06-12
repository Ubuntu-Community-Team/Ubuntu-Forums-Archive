---
title: "cannot get resolution above 800x600"
date: 2009-04-14
forum: Hardware
---

### Post by user sam on 2009-04-14
I am currently using  Ubuntu version 9.04 and i really like it but it has a quirk where it will not increase resolution above 800x600. I have browsed the forums before and tried the tricks here: [http://ubuntuforums.org/showthread.php?t=712702]("http://ubuntuforums.org/showthread.php?t=712702"), here: [http://ubuntuforums.org/showthread.php?t=775119]("http://ubuntuforums.org/showthread.php?t=775119"), and here: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution"),  as well as here: [https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434]("https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434"). I've tried every trick I know and everything either comes with an error message or is from an old version of ubuntu and no longer works. and in reply to doas777, that command won't tell me what video card i have, and looking for restricted drivers turns up absolutely nothing.

---

### Post by doas777 on 2009-04-14
well first off, what kind of vid card do you have?
if you don't already know, you can find out with
```
sudo lshw -C display
```

have you installed any restricted drivers for your vid device?
you can find them under System -> Hardware Drivers.
if so, what version?

---

