---
title: "Random Freezes under Edgy ( Kubuntu / ATI X300 )"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by chaosgeisterchen on 2006-10-27
Good morning everyone,

I was very impressed by the speed of Edgy and I really liked it very much - for about 20 minutes. This is the third time now - within 2 hours - that my machine randomly freezes during everday work. I assume it's a problem with the graphics driver which I already had under Dapper but I thought it'd be solved already.

I am  using an ATI X300 PCIE graphics card which is running under the **radeon**-Driver. Is there any possibility to run the system stable using this driver or do I have to change drivers?


Thanks for any answer in advance

chaosgeisterchen

---

### Post by zenrox on 2006-10-28
i dont thaink its limited to your pitucluar hardware
desktop pc with nvidia fx5500 8774 drivers
2ghz celron 786mbs ddr pc2100 ram
pleanty of hdd space
but it freezes to the point whare only a hard reboot would fix i dint have this prob in dapper

---

### Post by chaosgeisterchen on 2006-10-29
Maybe SWAP is not active? Try to **free** in the CLI and look whether SWAP is active.

Concerning my machine: It's running stable now. But I will keep away from Beryl as long it keeps killing my machine. My problems were most likely created upon old settings from Dapper transferred to Edgy. A clean install did away with the problems so far. 

I can only repeat my words:

Beryl is very unstable.

---

### Post by edwin11 on 2006-10-29
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]i'm using an X300 card too. No random freezes for me, but when my screensaver (GL type) kicks in, after a while, my X will restart on its own.

i used EasyUbuntu (not officially for Edgy) to install the ATI driver, which could be why.



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by edwin11 on 2006-10-29
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hey guys,

the link [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) posted on the thread [http://www.ubuntuforums.org/showthread.php?p=1683659#post1683659](http://www.ubuntuforums.org/showthread.php?p=1683659#post1683659) seems to have fixed my problem. Maybe you can give it a shot as well.



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by chaosgeisterchen on 2006-10-30
I will try out fglrx. The R300 drivers were a severe threat to my Dapper installation as well.

---

### Post by jamaas on 2006-10-31
Hi Edwin 

Thanks for this, the second solution, (running regular Ubuntu but might have started with OEM?) ie forcing restart of gdm worked for me, but I have to do it every time I reboot.  Anyone know how to fix this permanently.

Thanks all

Jim

> **edwin11 said:**
> [FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hey guys,

the link [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) posted on the thread [http://www.ubuntuforums.org/showthread.php?p=1683659#post1683659](http://www.ubuntuforums.org/showthread.php?p=1683659#post1683659) seems to have fixed my problem. Maybe you can give it a shot as well.



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

