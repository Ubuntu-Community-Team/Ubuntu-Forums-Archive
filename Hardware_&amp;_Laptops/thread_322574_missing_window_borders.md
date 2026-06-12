---
title: "missing window borders"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by bigdonH on 2006-12-20
This is driving me nuts. I have an ibm t43p with a fresh install of Ubuntu 6.10. All settings are at the default system settings from install time. Everything is working great, except for the one small issue of the missing window borders on my gnome desktop. If I open a terminal window, web browser, etc the window border is missing on the left side. This makes working with multiple overlapping windows difficult as there is no reference where one window ends and another begins.

I'm assuming that this maybe a video driver problem, but am not sure on how to proceed. Has anyone seen this issue before and have any hints on how to correct this?.

Thanks

---

### Post by ingo on 2006-12-22
No, haven't seen it before and it shouldn't be there. Does your computer have an NVidia card? If so, try installing their driver. Otherwise I can thinkk of nothing but reconfiguring X. The command escapes me at the mo, but a quick google should do it. 

A word of advice: before fooling around with your /etc/X11/xorg.file you should ALWAYS make a backup :)

---

### Post by bigdonH on 2006-12-22
No, the t43p has an ati video card. It's strange becasue there were no problems with dapper drake, but only appeared after a fresh install of edgy

---

### Post by ingo on 2006-12-23
Well, in that case have a look for ati in the forum and there is _tons_ of posts... I'd prefer that (installing a proper ATI driver that is) to configuring your present X.

HTH

---

