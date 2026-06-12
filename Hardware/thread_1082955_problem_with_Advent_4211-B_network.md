---
title: "problem with Advent 4211-B network"
date: 2009-02-28
forum: Hardware
---

### Post by waheedrafiq on 2009-02-28
I can't access internet as I can't connect to my LAN , I have the above mini-laptop and refuse to use windows.


is there any help I can get on this , this was working fine until i did the updates from Ubuntu for some reason it disable my LAN i  now have a icon with explanation mark.



I beg  you no I beg beg you to help me 


regards

Waheed rafiq

how do you do ipconfig in linux

---

### Post by dimmat on 2009-03-17
I had the same problem with Advent 4211 and Ubuntu 8.10. After updating, the LAN card stopped functioning. There seems to be a problem with the new kernel that is installed after the update (2.6.7.11). Try this link:

[http://people.ubuntu.com/~smb/bug326891/](http://people.ubuntu.com/~smb/bug326891/)

Download and install the latest kernel.
(linux-image-2.6.27-11-generic_2.6.27-11.27b326891v2_i386.deb worked for me)

LAN card works again!

Enjoy!!

PS: The resolution also applies for MSI Wind U100 since it has the same hardware as Advent 4211.

---

### Post by waheedrafiq on 2009-03-27
Sorry for the later reply mate I only get to use my internet during the weekend , as i can't get my wireless to work.

I manage to get LAN working via removing the new kernel 8.10 and selecting 8.7 kernel this seem to have done the trick but how do I get the wireless to work

---

### Post by dimmat on 2009-03-28
For fixing the wireless try this link:

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:)

and select 'Option #2'.

Have fun!! :-)

---

### Post by waheedrafiq on 2009-03-29
Thanks for the tread  link I have read it and shall have to decide if I have to use a external wireless card or not.


I also get this error "Enter Password for default keyring to unlock"  the application NetworkManager Applet /usr/bin/nm-applet wants to access to the dfault keyring. but is locked.


any ideas I have try my root password it does not work.

---

### Post by waheedrafiq on 2009-03-29
O my God , I have fix it ,  okay guy's I am not a guru or a Wizz Kid, but I have fix it. 

basically all I did was right click on the two computer icon and then created a Wireless connection , but I think what really fix this was that I apply all the latest  updates as it found 67 updates and I think this could have fix it.


anyway I am a happy Linux L plate person. 


thanks for your great support with out it would just not be possible.

---

