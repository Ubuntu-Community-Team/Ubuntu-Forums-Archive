---
title: "Evolution failure after Automatix"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by mjunior on 2006-01-25
Hello guys,
I need a tip. Did install the Automatix scripts and run it filling almost all the checkbox available. After that, my Evolution refuses to link to firefox in order to open a new window automaticaly by clicking some address recieved by e-mail.
So far the best I could do is copy the line and paste onto Firefox..but that's kind of sucks..
Any clue which setting the script changed? I already did a quick research at the proprieties on Firefox and Evolution and couldn't find anything related with those links...

Thanks in advance.

---

### Post by arnieboy on 2006-01-25
[QUOTE=mjunior]Hello guys,
I need a tip. Did install the Automatix scripts and run it filling almost all the checkbox available. After that, my Evolution refuses to link to firefox in order to open a new window automaticaly by clicking some address recieved by e-mail.
So far the best I could do is copy the line and paste onto Firefox..but that's kind of sucks..
Any clue which setting the script changed? I already did a quick research at the proprieties on Firefox and Evolution and couldn't find anything related with those links...

Thanks in advance.[/QUOTE]
go to system --> preferences --> preferred applications and change "browser" from **mozilla-firefox** to **firefox**

---

### Post by mjunior on 2006-01-27
[QUOTE=arnieboy]go to system --> preferences --> preferred applications and change "browser" from **mozilla-firefox** to **firefox**[/QUOTE]

Hello arnieboy,

thanks for your help. Another issue.. the repositories were changed by Automatix. The script made a copy from previous info? Can I backup as it was?

Thanks.

---

### Post by arnieboy on 2006-01-27
[QUOTE=mjunior]Hello arnieboy,

thanks for your help. Another issue.. the repositories were changed by Automatix. The script made a copy from previous info? Can I backup as it was?

Thanks.[/QUOTE]
u probably meant that u want to restore the original sources.list. yes u can do that but the risk associated with that is entirely your own.

---

### Post by mjunior on 2006-01-27
Hi again,

What do you mean by risks??
By the way, I didn't backup the previous source list before run the Automatix. The script did some backup before change the file?

One last question...regarding the new codecs..I'm able to run most of the audio/video extensions now, but still have a few problems with some wmv ...
When I try to open I receive a error message saying that there's no support for encrypted files...
When I first see the files I was trying to open the icon showed wmv but after the error it switch to asf..
I post it in another setion and some guys are talking about drm...
[http://ubuntuforums.org/showthread.php?t=121502](http://ubuntuforums.org/showthread.php?t=121502)

---

### Post by arnieboy on 2006-01-27
[QUOTE=mjunior]Hi again,

What do you mean by risks??
By the way, I didn backup the previous source list before run the Automatix. The script did some backup before change the file?

One last question...regarding the new codecs..I'm able to run most of the audio/video extensions now, but still have a few problems with some wmv ...
When I try to open I receive a error message saying that there's no support for encrypted files...
When I first see the files I was trying to open the icon showed wmv but after the error it switch to asf..
I post it in another setion and some guys are talking about drm...
[http://ubuntuforums.org/showthread.php?t=121502](http://ubuntuforums.org/showthread.php?t=121502)[/QUOTE]
by risks I mean breaking your system if u have the wrong repos on your original sources.list.
Automatix makes time and date based backups of most files including sources.list. check the /etc/apt folder.
I hope u have w32codes installed for viewing the different files. these codecs are not comprehensive. there will be a format or two which u will not be able to play on linux.

---

### Post by mjunior on 2006-01-30
Still about the automatix, I tried to install Opera browser cause I had a few bad experiencies with Firefox due few months. The script runed smoothly but when I tried to use the browser by clicking aplications\internet\Opera (the icon wasn't there btw) I got the error:
Não foi possível lançar a entrada

Detalhes: Falha ao executar processo filho "opera" (Arquivo ou diretório não encontrado).

Any clue?

---

### Post by mjunior on 2006-02-01
Don't need to bother replying anymore..

I saw a few http downloads errors on the log script...It might be something on office's firewall, so I took my laptop home and runned Automatix again...The Opera installed perfectly this time..

Thanks.

---

