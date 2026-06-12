---
title: "how to install INCA IC-3562 USB webcam driver?"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Erdem on 2008-01-02
hi everybody...
i have a USB web cam INCA IC-3562.

[IMG]http://www.garantialisveris.com/FrontContent/ProductImages/115087.jpg[/IMG]

i installed camorama and EasyCam2 but my web cam still doesn't work.

have any idea how can i install it?

thanks for replies...

---

### Post by linuxwizard on 2008-01-02
Post the results from the command > lsusb

---

### Post by Erdem on 2008-01-02
nothing...
[IMG]http://img162.imageshack.us/img162/87/resultdx1.png[/IMG]

---

### Post by linuxwizard on 2008-01-02
Not as root >open up a terminal > type lsusb > press enter > post results

---

### Post by Erdem on 2008-01-02
i have that results
[PHP]erdem@pc:~$ lsusb
Bus 005 Device 004: ID 0c45:6270 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
erdem@pc:~$ [/PHP]

---

### Post by Erdem on 2008-01-02
blow up

---

### Post by linuxwizard on 2008-01-02
Sorry I could not get back to you, lost my internet connections by the time it came back it was bedtime. I have seen others with Microdia webcams use the driver from here.
[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

Doing a search this post is the only one I could find. Look on this page second post that is the same as yours. 
[http://ubuntuforums.org/showthread.php?t=351578&page=2](http://ubuntuforums.org/showthread.php?t=351578&page=2)

---

### Post by Erdem on 2008-01-02
thank u for helping linuxwirazd

i guess this cam not supported yet :(

---

### Post by vivalant on 2008-01-05
Try the version 2.09 of the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by Erdem on 2008-01-05
> **vivalant said:**
> Try the version 2.09 of the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)
thanks it is works!!!
but this driver is not free and i cant spend that money :(
how can i find free version of this driver?

---

### Post by vivalant on 2008-01-05
There'a not a free version of the Generic SN9CXXX driver. The author wants to be paied for releasing the whole code under the GPL, as written in the FAQ (question 4) at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:8105

---

