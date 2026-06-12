---
title: "Changing Encryt Key 128bit To 64 Bit ????"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by adnaann on 2006-04-22
I GOT IBM T42 AND I INSTALLED UBUNTU ON IT MY LAN CARD IS WORKING OUT OF BOX BUT I GOT SERIOUS PROBLEMS WITH MY WIRELESS CARD
I INSTALLED network-manager THE PROBLEM IS THAT IT DONT SHOWS THE
64BIT ENCRYPTION IN THE TABS , AND AS 64BIT ENCRYPTED KEY IS USED ON MY OFFICE NETWORK AND I GOOOGLED ALOT BUT CANT FIND ANY THING ABOUT HOW TO CHANGE YOUR ENCRYPTION FROM 128 BIT TO 64BIT AS I GUESS THATS THE ONLY THING KEEPIN ME DISSCONNECTED

ANYBODY KNOWS HOW TO DO IT ??

 OR ANY OTHER BETTER WAY TO CONFIGURE I CANT CHANGE THAT 64BIT KEY TO 128 BIT AS I M NOT THE NETWORK ADMINISTRATOR AND USING LINUX WAS MY CHOICE AS IT GAVE ME A SENSE OF FREEDOM ALL OTHER GUYS ARE STILL STICKIN WID DA STICKY WINDOWS 


SO I REALLY NEED HELP HERE TO START MY NEW JOURNEY OF FREEDOM

CHEEERS!

---

### Post by adnaann on 2006-04-22
where is the geek ?? 
 

 who knows tht ??
 
 
 any one just sumone ?? come to rescue

---

### Post by nolongerlivecd on 2006-04-22
It would be 40-bit I think, just like 128 corresponds to 104... extra 14bits for something else

---

### Post by adamkane on 2006-04-22
You don't need 4 question marks in your title, and you should already know not to use caps.

If you want an answer to your question, follow some protocol, and bump your thread once in a while, if no one has responded.

---

### Post by adnaann on 2006-04-22
well i used caps and corrrect spellin to make my clearly readable  ok so  u shudnt be takin tht as an offence and dont teach me protocol ok 

if u cant help dont respond ..



 and for u my friend its not like tht 104bit or 14 bits  network manager only shows 128bits  and my network is using 64bits and i cant change it to 64bits 
 anyworkaround ???

---

### Post by Buffalo Soldier on 2006-04-23
adamkane is just giving you advice and that is a sound and good advice. There is a possibility people will avoid helping you because of the perceived rudenss (all caps = shouting).

I highly suggest you to edit back your first post and wait patiently. Everyone here are just normal users that contribute their free time to help each other. So give it some time, I'm sure someone knowledgeable will come to help.

If after some time, you've still have not received any feedback.. bump up the thread from time to time. Shouting out loud is not the best way to start any journey :)

So far searching thru google this is the only answer i can find for your specific problem. 
[http://mail.gnome.org/archives/networkmanager-list/2006-February/msg00004.html](http://mail.gnome.org/archives/networkmanager-list/2006-February/msg00004.html)
> 40/64-bit passphrases are extremely dicey because there is no standard
hash from passphrase to WEP key.  Most manufacturers do it differently.
104/128-bit ones do have a (fairly) standard way.

---

### Post by YuHoo on 2006-04-23
The encryption ought to be automatically adjusted to your network. Also, if you were using an incorrect encryption level you wouldn't be able to use the network in the first place. I have helped people with similar problems of being on a wireless network and then having it fall off. It's one of two: a) Your router is hitting a lot of background noise; b) Your wireless card doesn't have the power to cut through things like wires surrounding your router.

There isn't really a solution to the problem if you can not replace or adjust the geography of the router, but when you're connected to the network, type iwconfig in the terminal and it should display a decibel reading. My good connection has a signal level of 53dBm and a noise of 84dBm. Sorry if this is the problem, but moving closer or replacing one of the components ought to help.

As for the topic of etiquette, check out [www.spellcheck.net](www.spellcheck.net) . Etiquette is a personal choice, but things like misspellings, bad grammar, etc... all lead to presumptions and bias against you. Manners and etiquette also is not just that, but it serves the purpose of showing respect to others.

---

