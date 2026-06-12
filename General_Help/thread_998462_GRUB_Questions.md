---
title: "GRUB Questions"
date: 2008-11-30
forum: General Help
---

### Post by Hydrohs on 2008-11-30
I have Ubuntu installed on my external hard drive, along with the GRUB bootloader. When I have my external HD plugged in, GRUB shows me Ubuntu(twice) and windows, but I can't boot into Windows.

I'm wondering if I can edit this to remove one version of Ubuntu and the Windows, or if I can simply bypass GRUB all together and boot right into Ubuntu automatically when I have my external HD plugged in, because when I do I never intend to go into windows anyway.

---

### Post by caljohnsmith on 2008-11-30
OK, when you boot into Ubuntu, open a terminal (Applications > Accessories > Terminal) and do: 
```
gksudo gedit /boot/grub/menu.lst
```
And then change the "#hiddenmenu" line so that it doesn't have a comment in front of it:
```
hiddenmenu
```
Also change the "timeout" line to:
```
timeout 3
```
And lastly, if Ubuntu is the first entry in your Grub menu, change "default" to:
```
default 0
```
Then you should boot into Ubuntu automatically on start up. How about giving that a shot and let me know how it goes.

---

### Post by Hydrohs on 2008-12-01
I did all that and it worked fine, exactly how I want it to. thanks for your help. =D

---

