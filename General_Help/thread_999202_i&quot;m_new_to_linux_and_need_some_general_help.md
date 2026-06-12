---
title: "i&quot;m new to linux and need some general help"
date: 2008-12-01
forum: General Help
---

### Post by tchk1 on 2008-12-01
ok my first problem is that i set up my video card and it won't save settings i try to save here or create new folder
/etc/X11/xorg.conf
Unable to create new X config backup 
ile '/etc/X11/xorg.conf.backup'
and iget this error

---

### Post by hyper_ch on 2008-12-01
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Iowan on 2008-12-01
A stab in the dark... /etc/X11 is owned by root (drwxr-xr-x)  To write in that folder (ie. save a backup) you'll need to use **sudo**.

---

### Post by fenian on 2008-12-01
To edit the xorg.conf file you need to open the file with sudo (read more about sudo [here]("https://help.ubuntu.com/community/RootSudo")).To open the xorg.conf file with sudo...

Open a terminal (From the menu Applications>Accessories>Terminal)

Enter this command...

> sudo gedit /etc/X11/xorg.conf

A text editor (gedit) will open you can then edit the file as you need to and save the changes.

---

### Post by Iowan on 2008-12-01
[This]("http://www.psychocats.net/ubuntu/graphicalsudo") page suggests using **gksudo** for **gedit**.

---

### Post by shadowlands on 2008-12-01
is wrong but I am not sure how to post on here. 

I have installed Ubuntu with no problem, but Ican not connect to wireless. I have an Acer Aspire 5570z  
120 GBHDD 
1 GB DDR2 
with an 802.11b/g WLAN

I am not sure if more information is needed or not,  regarding the computer information.  I have found some really good information on this forum;however I am not sure where to put eh code in  nor do I know enough to ask good questions to ensure I have the correct codes needed.

I am placing the URl of the information in that I found  useful with the hopes someone can shove me assist me. 

[http://ubuntuforums.org/archive/index.php/t-540879.html](http://ubuntuforums.org/archive/index.php/t-540879.html)

d.sourceforge.net/download.php

Thank you in advance and I am sorry If I hijacked someones thread.

---

