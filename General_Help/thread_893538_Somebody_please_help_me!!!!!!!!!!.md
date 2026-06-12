---
title: "Somebody please help me!!!!!!!!!!"
date: 2008-08-18
forum: General Help
---

### Post by aviborse on 2008-08-18
[http://www.geek.com/feature-how-to-build-and-customize-your-own-pbx-with-asterisk-20080812](http://www.geek.com/feature-how-to-build-and-customize-your-own-pbx-with-asterisk-20080812)

Somebody please help me!!!!!!!!!! i did most of the part of this project but 
i m unable to edit 

/etc/asterisk/http.conf and
etc/asterisk/manager.conf

Kindly suggest me a way!!!!!!!!!

---

### Post by cdtech on 2008-08-18
> **aviborse said:**
> [http://www.geek.com/feature-how-to-build-and-customize-your-own-pbx-with-asterisk-20080812](http://www.geek.com/feature-how-to-build-and-customize-your-own-pbx-with-asterisk-20080812)

Somebody please help me!!!!!!!!!! i did most of the part of this project but 
i m unable to edit 

/etc/asterisk/http.conf and
etc/asterisk/manager.conf

Kindly suggest me a way!!!!!!!!!

You need to add sudo:
```
sudo gedit /etc/asterisk/http.conf
sudo gedit /etc/asterisk/manager.conf
```

---

### Post by scragar on 2008-08-18
```
gksu gedit /etc/asterisk/http.conf
gksu gedit /etc/asterisk/manager.conf
```

---

### Post by Kevbert on 2008-08-18
In Kubuntu does gedit work ?   I thought you had to use nano:
```
sudo nano /etc/asterisk/http.conf
sudo nano /etc/asterisk/manager.conf
```
To save press Ctrl+X, Y then return.

---

### Post by cdtech on 2008-08-18
> **Kevbert said:**
> In Kubuntu does gedit work ?   I thought you had to use nano:
```
sudo nano /etc/asterisk/http.conf
sudo nano /etc/asterisk/manager.conf
```
To save press Ctrl+X, Y then return.

My bad, scragar has it correctly.

---

### Post by scragar on 2008-08-18
no, kdesu no gksu for Kubuntu. I missed that.

and I think KDE uses kwrite instead of gedit:
```
kdesu kwrite /etc/asterisk/http.conf

```

---

### Post by aviborse on 2008-08-18
Thanks a lot guys.........i'll try all of them.
That PC is office once i'll go i'll try it out, did anybody chk out that project is it possible?.........

---

