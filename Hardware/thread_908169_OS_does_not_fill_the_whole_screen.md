---
title: "OS does not fill the whole screen"
date: 2008-09-02
forum: Hardware
---

### Post by Mr.Kuchinawa on 2008-09-02
I have recently installed xubuntu on an old Fujitsu Siemens machine. I had some trouble installing it, but after I updated the BIOS everything went pretty good. 

My only complaint is that screenshot does not fill up the whole screen. The screen itself is 3-4 inches bigger than what is displayed. So how to fill it?

Forgive me if this is the wrong place to post this. Any help will be appreciated.

---

### Post by overdrank on 2008-09-02
> **Mr.Kuchinawa said:**
> I have recently installed xubuntu on an old Fujitsu Siemens machine. I had some trouble installing it, but after I updated the BIOS everything went pretty good. 

My only complaint is that screenshot does not fill up the whole screen. The screen itself is 3-4 inches bigger than what is displayed. So how to fill it?

Forgive me if this is the wrong place to post this. Any help will be appreciated.

Hi have you tried the command ```
gksu displayconfig-gtk
``` and adjust the resolution there. What is the model of the graphics card? You can use the command lspci in the terminal located under application, accessories. Then look for VGA

---

