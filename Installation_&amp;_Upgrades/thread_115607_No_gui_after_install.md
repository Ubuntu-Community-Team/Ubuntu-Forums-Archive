---
title: "No gui after install"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by l3lackEyedAngels on 2006-01-10
I just installed Breezy on my Dell Inspiron 8000, but at the end of the install it said that some packages are missing, but that I could install them later. When I rebooted, I didn't end up in gnome like I expected to. Instead I'm at a command prompt and I don't know what to do now. I have installed different versions of Ubuntu on another computer without this problem. I did however get this problem when I tried a net install with Sarge. This time around, I installed from the net with Ubuntu. I feel as though I am missing a step. Help is much appreciated.

---

### Post by nkhansen on 2006-01-11
have you tried a 

$ sudo aptitude update
$ sudo aptitude -f install

? Maybe the mirror coughed at you during install?

---

### Post by l3lackEyedAngels on 2006-01-11
Is Aptitude apt-get? I have apt-get installed. I know because I was playing around and managed to upgrade the kernel and install wget.

---

### Post by hillbilly on 2006-01-11
Hmm..not sure what Aptitude is. But try > sudo apt-get install ubuntu-desktop.

---

### Post by christhemonkey on 2006-01-11
does it spew out any error messages on boot?

---

### Post by l3lackEyedAngels on 2006-01-11
No. I get the brown ubuntu screen where it tells you that everything is ok, and everything is ok. Then I have a black screen with white letters, asking me to log in, which I can do.

---

### Post by christhemonkey on 2006-01-11
hmm, the mystery thickens....

---

### Post by l3lackEyedAngels on 2006-01-11
Thank you all for your help. I will try your suggestions as soon as I can get access to el internet without my girlfriend hassling me about playing with linux too much.

---

### Post by kaamos on 2006-01-11
[QUOTE=l3lackEyedAngels]I will try your suggestions as soon as I can get access to el internet without my girlfriend hassling me about playing with linux too much.[/QUOTE]
Been there.. ;)

---

### Post by l3lackEyedAngels on 2006-02-24
It appears that I never concluded this. hillbilly's suggestion, >  			 				sudo apt-get install ubuntu-desktop worked very well. Thanks!

---

