---
title: "[SOLVED] Installing 8.10 with Wubi offline"
date: 2008-11-10
forum: General Help
---

### Post by rv53705 on 2008-11-10
[FONT="Lucida Sans Unicode"]Hi, my first post. I'm trying to install Ubuntu 8.10 like I did with 8.04 using Wubi, but now Wubi forces me to download the ISO, when I downloaded and burned it, so everytime I try to install, tells me "Please connect to the internet" (something like that).

I've tried everything this forum has, from setting Wubi.exe on the same folder with the ISO (extracted too), but nothing works, Any advice else?

I need to upgrade, I run Ubuntu three days on a week (I combine with my XP Pro SP3), so don't think to be without Ubuntu.

Thanks.[/FONT]

---

### Post by brandon88tube on 2008-11-10
Do you have the new version of Wubi.exe? If you have the 8.04 version and are trying to install 8.10 I don't think it will work. If you still have problems could you take a screenshot of the 2 files together and then a screenshot of the error you are getting?

---

### Post by PGHammer on 2008-11-11
> **brandon88tube said:**
> Do you have the new version of Wubi.exe? If you have the 8.04 version and are trying to install 8.10 I don't think it will work. If you still have problems could you take a screenshot of the 2 files together and then a screenshot of the error you are getting?

Download the 8.10 version of Wubi (if you have the ISO of Intrepid already, put the freshly-downloaded Wubi in the same directory), and run it from that location.  (I did exactly that with Intrepid myself (and I already had a dual-boot setup in place); it worked like a charm.)

---

### Post by rv53705 on 2008-11-11
Hi guys, i'm still trying but i don't get it. I've got this screenshot:

[[IMG]http://img201.imageshack.us/img201/8454/wubi810lo5.th.jpg[/IMG]](http://img201.imageshack.us/my.php?image=wubi810lo5.jpg)

So i've tried everything: create a new ISO with the new Wubi a mount it, create a folder with the ISO files and the new Wubi, all.

What are the steps you used to get it?

---

### Post by Orlsend on 2008-11-11
> **rv53705 said:**
> Hi guys, I'm still trying but i don't get it. I've got this screenshot:

[[IMG]http://img201.imageshack.us/img201/8454/wubi810lo5.th.jpg[/IMG]](http://img201.imageshack.us/my.php?image=wubi810lo5.jpg)

So I've tried everything: create a new ISO with the new Wubi a mount it, create a folder with the ISO files and the new Wubi, all.

What are the steps you used to get it?

The Way I do it like yours, but I got a firewall (Zone Alarm free) which I tell to commence a "Internet Lock down" then its just checks for about 30 secs and continues the Install.

[I]"Si necesitas mas ayuda tambien hablo espanol :D "
[/I]

---

### Post by rv53705 on 2008-11-11
> **Orlsend said:**
> The Way I do it like yours, but I got a firewall (Zone Alarm free) which I tell to commence a "Internet Lock down" then its just checks for about 30 secs and continues the Install.

[I]"Si necesitas mas ayuda tambien hablo espanol :D "
[/I]

Entendí posees el mismo problema? Yo no tengo ningún problema con el Firewall (Kaspersky IS), pero si apago el router, me forza a conectarme para continuar. Actualmente estoy descargando la ISO mediante Wubi, pues no me gusta estar sin Ubuntu.

---

### Post by brandon88tube on 2008-11-11
> **rv53705 said:**
> Entendí posees el mismo problema? Yo no tengo ningún problema con el Firewall (Kaspersky IS), pero si apago el router, me forza a conectarme para continuar. Actualmente estoy descargando la ISO mediante Wubi, pues no me gusta estar sin Ubuntu.

Lol, I hope you were not asking for help in Spanish there because I don't speak Spanish. "No hablo español, hablo inglés por favor."


Also it looked like you had PowerISO open. Did you mount the ISO, did you edit it? If you did either of those do not do that.

---

### Post by rv53705 on 2008-11-11
I've done everything possible **brandon88tube**, edit it , mount it, the original ISO, but still nothing works.

I've advanced a little bit, i renamed the *Ubuntu 8.10 i386.iso* to *ubuntu-8.10-desktop-i386.iso*, the first time didn't work, but after did it, so when i rebooted i started Ubuntu, started loading, but after almost 10 minutes gave an error that said something like Hardware Drivers no found.

I think Ubuntu 8.10 with Wubi is much harder to install than 8.04, what do you folks believe?

PD1: I just shared some Spanish words, not requested for help, just wrote almost the same that i did before.

PD2: I downloaded the ISO trought Wubi, but when i rebooted, Ubuntu didn't appear.

---

### Post by ago on 2008-11-11
There is a log in your user temp folder (%temp%). Please post it here.

---

### Post by rv53705 on 2008-11-11
> **ago said:**
> There is a log in your user temp folder (%temp%). Please post it here.

A log in? I don't know what you mean, so i found 2 .tmp folders with Ubuntu installing folders and [this LOG file]("http://rv53705.110mb.com/files/Wubi-8.10-rev515.log").

PD: When i tried to install, i got Kubuntu, Xubuntu, Mythbuntu (not sure) desktop environment, why before not?

---

### Post by brandon88tube on 2008-11-11
Not sure why that happened, but there are slight differences between Ubuntu, Kubuntu, Xubuntu and Mythbuntu. The biggest difference is the look and the gui, like Ubuntu uses gnome, Kubuntu uses KDE etc. [http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu), [http://en.wikipedia.org/wiki/Kubuntu](http://en.wikipedia.org/wiki/Kubuntu), [http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu), [http://en.wikipedia.org/wiki/Mythbuntu](http://en.wikipedia.org/wiki/Mythbuntu). Those are some wiki links that have some screenshots of each and gives a little information. Choose whatever one you like.

---

### Post by rv53705 on 2008-11-11
> **brandon88tube said:**
> Not sure why that happened, but there are slight differences between Ubuntu, Kubuntu, Xubuntu and Mythbuntu. The biggest difference is the look and the gui, like Ubuntu uses gnome, Kubuntu uses KDE etc. [http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu), [http://en.wikipedia.org/wiki/Kubuntu](http://en.wikipedia.org/wiki/Kubuntu), [http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu), [http://en.wikipedia.org/wiki/Mythbuntu](http://en.wikipedia.org/wiki/Mythbuntu). Those are some wiki links that have some screenshots of each and gives a little information. Choose whatever one you like.

I knew that, but why before didn't appear?.

---

### Post by brandon88tube on 2008-11-11
To tell you the truth I am not sure. Maybe Ago might know.

---

### Post by rv53705 on 2008-11-13
Problem solved, i just retry today, installing in English and 4Gb, and everything works. I don't know why before not.

---

### Post by luckstrikes on 2009-04-03
The actual problem is that after WUBI has the ISO, it tries to download the MD5 checksum of the image from the internet. start WUBI with the option --skipmd5check and all goes well!!!

---

