---
title: "Language problem after update from 7.10 to 8.04.02"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by lemik on 2009-04-12
Hello, when I installed from DVD the 7.10 desktop version, I selected Russian language. Everything was OK till I upgraded to the 8.04.02 version.
Now on the very first screen, when it's need to enter login and password I can enter only &#1089;yrillic letters, but my login and password are in roman, so I can't even login. I was proposed to change the login to automatic mode, but there are some other users in the system. 

How can I return to roman alphabet in the very first screen?

I made my login automatic (from LiveCD changed the file "etc/gdm/gdm.conf", enabled automatic login), entered the system, changed the language to English, but still, on the login screen I can enter only &#1089;yrillic letters. 

And another question - after upgrade I can't found applets for system administration. How can I start them from command line?

Thank you.

---

### Post by zvacet on 2009-04-12
You can try to edit your xorg.con file 

```
gksudo gedit  /etc/X11/xorg.conf
```

and you will see 

#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"ru"
#	Option		"XkbOptions"	"lv3:ralt_switch"

#EndSection

change it to 

#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#	Option		"XkbOptions"	"lv3:ralt_switch"

#EndSection

save and close  file.After restart you should be able to login.

P.S.I assumed that your language is Russian.If it is not sorry,but advice is good anyway.

---

### Post by lemik on 2009-04-12
Thank you. It really helped, but now I have another problem: when I click on the menu "System" - the third from left on the up line, I have only started Firefox instead of rich previous menu. How can I re-establish this menu?

Thank you.

---

### Post by zvacet on 2009-04-12
**System>preferences>main menu**> on the left select group (internet for example) and then on the right select what you want to be displayed.

---

