---
title: "Caret Browsing problem with dell m1530"
date: 2008-10-21
forum: Hardware
---

### Post by jhan1 on 2008-10-21
I can triple boot xp,vista and ubuntu 8.10 on my desktop no problem,  but i decided to dual boot my Dell m1530 with vista and ubuntu and have a problem using firefox.
    When i open firefox and try to type in the search bar or address bar, a pop up for "Caret Browsing" comes up and tells me that F7 will enable or disable this feature.  This pop up appears an infinite number of times and will not close out. I have to kill firefox in the system manager because no buttons work while this pop up is present.
    I get the same results with installs of Intrepid and also with Hardy.  I finally wiped out ubuntu completely and just tried the live cds but got the same problem.  Any Ideas?  Thank You

---

### Post by Coort on 2008-11-04
uhmmm...same problem here...

---

### Post by Gausian on 2008-11-04
You need to fix you touchpad setting by adding


i8042.nomux=1

to the kernel line in /boot/grub/menu.lst

---

