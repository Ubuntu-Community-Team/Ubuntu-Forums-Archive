---
title: "help with ubuntu file share on lan"
date: 2008-11-12
forum: General Help
---

### Post by washable mist on 2008-11-12
i am quite new to using linux, it took me only 5mins to setup a network file share with windows so i think i might need some help.

basicly  i have installed samba dn wish to put a couple of folders on my lan as file shares like i did in windows, 

when i right click the file in ubuntu and click on SHARING OPTIONS, then tick the SHARE THIS FOLDER box and finally CREATE SHARE i get the error message 
[I]
net usershare returned error 255: net usershare cannot open usershare directory /var/lib/samba/usershares. error permission denied[/I]

can anyone help me with this

---

### Post by john183 on 2008-11-12
Run Nautilus as root by pressing alt+f2 and type
```
gksudo nautilus
```
and try again you probably just don't have the proper permissions as your regular login.

---

### Post by Coreigh on 2008-11-12
Do you have Samba installed?

Also I tried it on my 7.10. But even though I was able to create a share I was not able to connect to it from a Windows computer.

---

### Post by washable mist on 2008-11-12
> **john183 said:**
> Run Nautilus as root by pressing alt+f2 and type
```
gksudo nautilus
```
and try again you probably just don't have the proper permissions as your regular login.
hit it right on the head there, i am learning something new everyday. but i would just like to ask, is there a way for me to remove passwords on the shares??

---

