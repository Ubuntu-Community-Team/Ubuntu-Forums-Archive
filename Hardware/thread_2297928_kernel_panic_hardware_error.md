---
title: "kernel panic hardware error"
date: 2015-10-07
forum: Hardware
---

### Post by matt18 on 2015-10-07
Ok, so i have not been able to install ubuntu 14.04 or 12.xx of any flavor such as lubuntu or ubuntu because i keep getting a black screen right after i hit try ubuntu without installing. so i tried some boot options such as nomodeset -- vga=785. it now runs through the basic startup but now i get a bunch of kernel panics which i was not having before.

65.54030 fatal machine check on current cpu
65.54030 hardware error cache level: L3?GEN (timed out)

there are about 6 others.

what the heck is going on???? Ubuntu should not be this damn hard to install haha

thanks in advance guys

---

### Post by weatherman2 on 2015-10-07
What kind of hardware?  What CPU?  Have you ever installed Linux on it successfully in the past?  Was there an OS successfully installed up until now?  Were there any hardware issues prior to this?

Are you trying to install 32 bit or 64 bit Ubuntu?

Have you tried running Memtest from the Ubuntu boot menu?

---

### Post by MartyBuntu on 2015-10-07
Have you tried the **Alternate Install** disk?

---

### Post by matt18 on 2015-10-07
You would think that after being a member for loooong time, i would know to post what you asked for marty. Sorry.

Yes i had win xp running before but due to a mbr issue, i am wanting to install linux instead. I could fix mbr easily but im wantimg ubuntu for its speed and mem usage. 

As far as i know, its a 64 bit version. Download says so haha. My hardware is as follows

AMD 5500+ socket 939
4gb ddr 400 ram
40gb ide hdd
ATI x1900xtx

I just finished a 6 hour mem test with no errors. Test was still going when i got home from work and it was on pass number 9. Could not see any indication of errors. 

Original issue was screen was going black during install. As in i could not get it to load the live cd or the install menu. Something to do with the new kernel not having certain information. I tried nomodeset xforcevesa and recieved a no ums support for radeon module. Im assuming radeon module is my radeon gpu. Then after i tried vga=785, i get kernle panic.. 

Thanks

---

### Post by matt18 on 2015-10-07
No i have not tried alt install disk... What is this you speak of?

---

### Post by matt18 on 2015-10-08
Here is a pic of the errors i am receiving:

[IMG]http://i59.tinypic.com/161iygx.jpg[/IMG]

Memtest passed with flying colors. 9 passes with no errors. So i have no idea why ubuntu 12.10 and 14.04 is freakin out. I have tried lubuntu and ubuntu. I have not tried linux mint yet but i have downloaded it haha :)

---

### Post by weatherman2 on 2015-10-08
Try updating the BIOS.

---

