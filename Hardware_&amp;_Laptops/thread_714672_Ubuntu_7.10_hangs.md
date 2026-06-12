---
title: "Ubuntu 7.10 hangs"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Shanison on 2008-03-04
Ubuntu 7.10 almost drives me crazy. Attracted by a lot of new features for 7.10, i unstalled 6.06 LTS and installed 7.10 instead in yesterday afternoon. The problem is that after installing ubuntu 7.10, everytime i boot the computer, the screen will go totally black and after 4 minutes it finally came to the log in screen.But after using for 3 minutes,no matter what i did, the computer will just hang there. 

After searching the web for a long time, i fixed the black screen on boot problem by changing the usplash.conf. Now the problem is that it still always hangs. At first i thought this problem is also caused by the bug of usplash.conf. But even after i fix that, no matter what i do, after a while it will just hang there. I have manually reboot my computer for 10+ times since yesterday. Someone plz help, i am new to ubuntu.

ps: My laptop is IBM T43. And i also have windows XP installed.

---

### Post by BillDozer on 2008-03-04
Do you have an NFS mount? I have noticed that if I mount to a 7.04 server that it takes up to two minutes before it continues. Try to enter grub at start up and remove the splash and quiet from the boot line. Then you can see where it takes a long time.

---

### Post by Shanison on 2008-03-04
thanks for your reply. The black screen boot problem has been solved, and now it takes quite a short time to log in. But the problem is the system always hangs. I couldn't use it for up to 3 minutes...

---

### Post by gopkumar on 2008-03-05
Hi,

I just installed Ubuntu 7.10 on my T43 today and ended up with the same problem as yours  - my X will hang randomly! It happened half a dozen times by the time I did some googling and found out with some trial and error that removing the Driver "ATI" from /etc/X11/xorg.conf and making it Driver "fglrx" and restarting X solves the problem - of course you have to do an aptitude install fglrx-driver. Hope this helps ..

---

