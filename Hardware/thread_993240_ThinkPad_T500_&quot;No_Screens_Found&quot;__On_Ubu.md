---
title: "ThinkPad T500 &quot;No Screens Found&quot;  On Ubuntu 8.10"
date: 2008-11-25
forum: Hardware
---

### Post by DBQ on 2008-11-25
Hi everybody.  I just got a new Lenovo ThinkPad T500.  I did a clean install of Ubuntu 8.10. Installation seemed to work fine.  When I boot up the X-server fails to start.  The xorg.conf file seems very short.  I cannot post since it seems that thing does not see my USB drive. I do however, have an internet connection through wireline network (but alas have no internet browser since there is no X) :(.

Could somebody please help me?  I really need to get work done on it ASAP.

BTW, I tried doing startx, but it gives me a no screens found fatal error thing. 

Thank You very Much.

---

### Post by alliera on 2008-11-28
The T500 has two graphics cards. Try disabling the automatic switching in the BIOS:

press the blue button while startup>F1>Display - there you will have to change two settings (don't have a T500 here, so I don't know the exact names, but it's described on the settings page of the BIOS), one that switches the graphics card (set to the one you want to use) and one that tries to detect your OS (disable that one).

/ken

---

### Post by mkclarke on 2008-12-16
Hello DBQ,

Did Ken's suggestion work?  I'm curious if that solved the problem or not.

Thanks,

Mike

---

### Post by DBQ on 2008-12-16
It did!

---

