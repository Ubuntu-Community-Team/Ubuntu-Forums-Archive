---
title: "Flashing Laptop BIOS"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by SnhKnives on 2005-06-02
Sorry if this question has been asked before. I did a few searches on this site to see if there had been similar threads but found nothing that helped me with my problem.

I use an Asus M6N laptop. 1.8Centrino, 1gb DDR333, Radeon Mobile 9700.

However like many laptop users on this site, My battery does not show up/Ubuntu cannot determine the time left of recharge or battery life.

I saw that another user on this site also uses an M6N and runs Ubuntu. He said that he updated his bios and everything after that was fine. 

I went to the asus site and downloaded the newest BIOS ROM.

File name M6N0214A.ROM

I know i have to flash the bios and update with the new one. However the only instructions that Asus gave me were to use a program they made for windows. Many other searches I made also mainly described how to do it through windows apps.

I do not have a Floppy A: drive on my laptop, if anyone has any advice please let me know.

thanks.

---

### Post by fastluck on 2005-06-14
Does your laptop have a Compact Flash or similar media card?  If it does, it might boot from that.

---

### Post by luca_linux on 2005-06-15
I'm here. Don't worry about...there are many ways to update your bios.
Just have a look at here: [http://m6n.ath.cx/forum/viewtopic.php?t=215](http://m6n.ath.cx/forum/viewtopic.php?t=215)
For any problem I'm here. Just write me.

---

### Post by luca_linux on 2005-06-15
Anyway, everyone having problems with battery lifetime indicator can try this patch: [http://m6n.ath.cx/aml_method_exec_hack.patch](http://m6n.ath.cx/aml_method_exec_hack.patch).
It's been tested only on Asus M6N(e) laptops, but should work on every notebook having AML errors at boot (just have a look at dmesg).
Anyway the Asus M6N(e) users should update their bios instead of using this patch, since there've been some important fixes, especially for the suspends (S3 and S4) and the fan.

---

