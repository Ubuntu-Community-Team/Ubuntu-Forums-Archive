---
title: "X-Fi"
date: 2008-08-06
forum: Hardware
---

### Post by db92 on 2008-08-06
yes, well, i already know that the x-fi topic has been quite talked about and that there is the [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656) x-fi beta driver thread but still, i opened this new thread for something that might not be new even, but i have not seen it mentioned in other threads (maybe i didnt see them?)

so i have tried&"accomplished" both the methods @ the link above with ossv4 and custom kernel+patched official x-fi drivers, but the custom kernel+official x-fi drivers requires you to backroll from 2.6.24-19(at least the current kernel version) to 2.6.24-3 (even after a sudo apt-get update && sudo apt-get upgrade, the linux-source-2.6.24 insisted on downloading 2.6.24-3 for me :| ). 
with various tricks i found on the web, i have managed to compile and install the official x-fi beta2 drivers on newest kernel and i believe that with a bit of support and/or effort, we might get working drivers :\

for some reason the system->preferences->sound menu acts as if there is no driver installed, even though the drivers are normally installed (test button gives the usual error [http://img139.imageshack.us/my.php?image=soundca1.jpg](http://img139.imageshack.us/my.php?image=soundca1.jpg).

seriously, im quite eager to get this working, besides for my own satisfaction, this would help the community a fair bit, considering the trouble/confusion this x-fi incompatibility has caused :P

at this moment, i feel i may be considered an idiot for bringing up this topic once again, but im desperate enough to get working drivers that i dont really care anymore! :p

---

### Post by stchman on 2008-08-06
Creative released the X-Fi in 2005 and there STILL IS NOT a good Linux driver.

I have now put Creative in the same boat as Broadcom.

---

### Post by jacmoe on 2008-09-16
I followed [Amtams guide]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675"), and made sure to get and install new nvidia drivers via envyng before installing the patched XFI driver.

It worked, sort of, because XFI killed my nVidia..

I found the solution here:
[Adding vmalloc and uppermem to startup script to increase memory]("http://ubuntuforums.org/showthread.php?t=181857")

And it works!
On Ubunto 8.04, the Hardy Heron. :)

Thank you so much Amtam! :D

---

