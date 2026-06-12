---
title: "&quot;CUPS server error&quot; on ubuntu 9.10"
date: 2009-11-12
forum: Hardware
---

### Post by unclesam.xu on 2009-11-12
I did a fresh install of ubuntu 9.10. after I update , the cups stop working. When I use preference->default printer, it shows "CUPS server error - The CUPS scheduler is not running." When I try to open a terminal and run "http://localhost:631", it shows

bash: [http://localhost:631:](http://localhost:631:) no such file or directory

If I try to type in a browser , it shows "can't connect to cups server"

I am using ubuntu 3 years , no this issue, I have a MFC 210C, and it even works right after I did the fresh install and then install the driver from brother's website.

two days ago there is a major update on cups, doesn't help at all.

please le me know how I can fix this. any help appreciated.

---

### Post by cariboo on 2009-11-12
Is cups running? Open a terminal and type:

```
sudo service cups restart
```

and paste any error messages in your next post.

---

### Post by unclesam.xu on 2009-11-12
when I run that , it shows :

"cups: unrecognized service"

obviously it is not running. that is my first post , is said it is not running

I have already checked sympatic manager, I have installed cups. and reinstalled couple times after I read this forum. and then two days ago I did the system update.

---

### Post by unclesam.xu on 2009-11-12
pump

---

### Post by trigoman05 on 2009-11-13
> **cariboo907 said:**
> Is cups running? Open a terminal and type:

```
sudo service cups restart
```

and paste any error messages in your next post.

This fixed that error for me, thank you.

---

### Post by unclesam.xu on 2009-11-13
I said , it shows

cups: unrecognized service

please. I have to switch to windows xp to print something.

---

### Post by santhony on 2010-05-26
This fixed my issue on Lucid Lynx..  Appears the CUPS service is not starting at boot..

---

