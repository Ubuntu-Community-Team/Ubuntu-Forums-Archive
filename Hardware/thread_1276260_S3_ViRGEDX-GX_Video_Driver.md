---
title: "S3 ViRGE/DX-GX Video Driver"
date: 2009-09-26
forum: Hardware
---

### Post by robertoreto on 2009-09-26
[B][FONT=Tahoma][SIZE=3][COLOR=Navy]Hello! :)
I've got this problem. I hope you can help me.
I've got a old PC (Intel Celeron @ 1.7 GHz) with a S3 ViRGE/DX-GX Video Driver.
In U/K/Xubuntu, the maximun resolution I have is 800x600 @ 60, while in Windows I had others.
I've searched for the Linux driver, but I haven't found anything.
I hope you understand me since my native language is Spanish.
Thank you all.[/COLOR][/SIZE][/FONT][/B]

---

### Post by k33bz on 2009-09-26
This is suppose to work, let me know if it does.
[http://linux.die.net/man/4/s3virge]("http://linux.die.net/man/4/s3virge")

sudo apt-get install xserver-xorg-video-s3virge

---

### Post by robertoreto on 2009-09-27
> **k33bz said:**
> This is suppose to work, let me know if it does.
[http://linux.die.net/man/4/s3virge](http://linux.die.net/man/4/s3virge)
 
sudo apt-get install xserver-xorg-video-s3virge
 
I've already done that. Nothing happens.
```
ana@ANA:~$ sudo apt-get install xserver-xorg-video-s3virge
[sudo] password for ana: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
xserver-xorg-video-s3virge ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ana@ANA:~$
```At the end it says:
> xserver-xorg-video-s3virge is already installed in its latest version
0 updated, 0 will be installed, 0 to remove and 0 not updated
I think that's is because, in the list of Supported Hardware in [that page]("http://linux.die.net/man/4/s3virge") there isn't a S3 ViRGE/**DX-GX**.
 
Isn't anything else that I can do?
Thank you [**k33bz**]("http://ubuntuforums.org/member.php?u=296107") ... so far.

---

### Post by robertoreto on 2009-10-09
Well, since I was trying to install a Linux distro on this old PC, I decided first for Ubuntu with the Xfce Desktop because I read it is faster. Then I got this problem and then Ubuntu started to become really slow. So, I look for another distro and I found Zenwalk. I downloaded it, burned it, installed ... and problem solved. It recognized other resolutions and it's a big bit faster the Ubie. :P

---

