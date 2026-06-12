---
title: "How to install canon 2900 on Ubuntu 12.10?"
date: 2013-03-20
forum: Hardware
---

### Post by trinhhoangda on 2013-03-20
I'm using Ubuntu 12.10, i have a canon 2900 printer. I tried to install it but it didn't work! I followed this link: [http://www.unixmen.com/installation-can ... -on-linux/]("http://www.unixmen.com/installation-canon-lbp2900-on-linux/")
I tried 2 ways in this post but now it's still not work. Can you help me install it?
The second,can you show me how to uninstall error drivers? Can I create system restore point like in windows os?
The third, what are fifo0 and lp0? Must I change these port when i install printer? (my laptop have four usb port)
Thanks all!

---

### Post by pdc on 2013-03-21
......you mean an LBP2900 printer?

I think the best tutorial is this one

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

.......it is in French, by Sivella; so run it through google translator

...... you don't tell us if you are using 32bit or 64bit.......the 32bit is a lot simpler............

with the account by Sivella, you do NOT need to create the fifo directories that were formally advised;

see how you get along with this thread of Sivella's;

post back if we can help in any way

Ubuntu provide this guide

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

but I think it is quite incomplete, but if you read through it, you will recognise some of what Sivella covers..........

---

### Post by trinhhoangda on 2013-03-21
> **pdc said:**
> ......you mean an LBP2900 printer?

I think the best tutorial is this one

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

.......it is in French, by Sivella; so run it through google translator

...... you don't tell us if you are using 32bit or 64bit.......the 32bit is a lot simpler............

with the account by Sivella, you do NOT need to create the fifo directories that were formally advised;

see how you get along with this thread of Sivella's;

post back if we can help in any way

Ubuntu provide this guide

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

but I think it is quite incomplete, but if you read through it, you will recognise some of what Sivella covers..........

Thanks pdc! But i can't read this guide. Can you give me one in Vietnamese or Engish? (I'm Vietnamese).
My printer is Canon LBP 2900, I use Ubuntu 12.10 32bit.

---

### Post by pdc on 2013-03-22
[http://translate.google.co.nz/translate?sl=fr&tl=vi&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp](http://translate.google.co.nz/translate?sl=fr&tl=vi&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp)

let us know how it goes;

32bit is great; you start at section 2 and it should go smoothly; 

the commands should be something like

> [COLOR="#FF0000"]sudo / usr / sbin / lpadmin-p LBP2900-m-v CNCUPSLBP290CAPTK.ppd ccp :/ / localhost: 59787-E[/COLOR] 

if you have only one printer, your LBP should be lp0 so next command should be

> [COLOR="#FF0000"]sudo / usr / sbin / ccpdadmin-p LBP2900-o / dev/usb/lp0[/COLOR]

then 

> [COLOR="#FF0000"]sudo service start ccpd[/COLOR]

.....Sivella then details in 2.3 how to ensure it all happens each time!

let us know how it goes

---

### Post by trinhhoangda on 2013-03-24
Thanks pdc! I followed this link: [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) and my printer worked. It's wonderfull! But, can you tell me: "why my printer print very slow when i print a document? if i print test page, it will print faster". Can you resolve this problem for me?

---

### Post by pdc on 2013-03-25
> [COLOR="#0000FF"]can you tell me[/COLOR]: "why my printer print very slow when i print a document? if i print test page, it will print faster"

...................um...........................no........................in contrast...............................my LBP3100B is quick; you would need to google around...........do you have lots of memory in your computer?

---

### Post by trinhhoangda on 2013-03-27
Thanks! I will search on google.

---

