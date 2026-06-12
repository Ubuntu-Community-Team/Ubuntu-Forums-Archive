---
title: "Ubuntu 8.10 install inside Windows, how to make disk portion larger?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2008-12-06
Ubuntu 8.10 install inside Windows, how to make disk portion larger?

I recently Installed Ubuntu 8.10 within Windows XP (like a program), when installing, I chose 5GB disk space of my 120GB laptop drive. I was uncertain if I would like Ubuntu or not so I limited the size as my drive was nearly full. The install worked great but I am running out of disk size that is apportioned to Ubuntu install. Within Windows XP, I freed up more drive space (about 60GB) thinking it would help Ubuntu, but it doesn't. So, is there a way to change the Ubuntu portion of 5GB drive space to more like 20GB? So that I can install more programs within Ubuntu? Without uninstalling and reinstalling? BTW, I am a complete Ubuntu Newbe. Thanks for any advice and help. ~Mahogan

---

### Post by Astenorh on 2008-12-06
check this website : [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

it has a lot of answer.

What you need to do is install lvpm, run it and choose the option resizehome

PS : If you are planing to use Ubuntu a lot. You should consider installing it on a dedicated partition. (The disk will be faster)

---

### Post by Mahogan on 2008-12-06
Thanks for replying.  I downloaded the program as you suggested.  When  running the program it does not give the the option to resizehome.  Just resize.  I chose resize,  told it 15000 mb rather than the 5000 mb existing.  I notice on the progress screen it says "Creating new root.disk size of 15000 mb."  When reading the instruction it says that I should resizehome for the virtual install, then rename the new locations from within windows. see link:  [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

 Did I do something wrong?  Should I cancel?

---

### Post by Mahogan on 2008-12-06
Thank you astenorh, this process works flawlessly!:p

---

