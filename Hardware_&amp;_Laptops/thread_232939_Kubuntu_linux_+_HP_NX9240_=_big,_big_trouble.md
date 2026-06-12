---
title: "Kubuntu linux + HP NX9240 = big, big trouble"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by kurosdr on 2006-08-09
Hi,

Recently, i was offered from a reliable source (PC magazine) an ISO image of the so popular linux distribution, kubuntu linux.

Because i am a user who hasn' t seen many other operating systems exept windows, i decided to taste the difference of linux. So,i burned the ISO onto a CD, put it in the tray and restarted. What could possiby go wrong??

Well, it went...

the live CD booted normally and within seconds i was in the KDE desktop. After seeing some basic things (conqueror, etc), i decided to go back to windows. 

I quit without installing anything and booted again. BUT, instead of the hp logo that appears on start up, a got a horizontal line flashing, and when i tried to enter the password... it froze! 
Thats it! No error messages, no beeps, just the frozen password screen. I tried again many times, but it kept doing the same thing. For a moment, i thought the bios/TPM security were locked! I almost got sick And the worst of all? All that happended during vacation, in a remote island with limited internet access and no hp support centre nearby.

The solution? Removing the battery and inserting it again. After that, everythng worked just fine again. I dont know (and i dont want to know) what happened, but what i know i almost lose the WHOLE COMPUTER (not just windows), from a live CD that it is supposed to be safe for any system.

And then the open surce community are wondering why all people uses windows. Maybe because with them the computer works fine?

kurkosdr
from Greece

---

### Post by pancyber on 2007-02-14
probably sigterm could not kill a process, graphics or cpu scaling probably. As this process was not finished sucessfully vga buffer was not cleaned. Both laptops newer bios and Ununtu newer releases have overcame such issues. 

Try something newer like ubuntu 6.10
It worked for me without any problems.

---

