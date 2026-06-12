---
title: "Keyboard layour editor for Linux?"
date: 2008-10-11
forum: General Help
---

### Post by amn108 on 2008-10-11
I need to find either a way or software that lets me edit certain keys for foreign layout typing. Anyone knows where these files are, that one can edit, or which packages deal with that. Can't seem to find anything...

---

### Post by Julius1988 on 2008-10-11
try
[http://www.jwz.org/xkeycaps/]("http://www.jwz.org/xkeycaps/")
don't know for sure whether this is what u want.

---

### Post by Icebear on 2008-10-11
the keyboards layouts are kept at:

/usr/share/X11/xkb/symbols

this is a howto I wrote for myself to change the the russian keyboard it might be able to help you.

How to map a keyboard in ubuntu 

go to X11/symbols diretory, 	by typing cd /etc/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file,	sudo cp ru ru_backup
then load the file up to edit,	sudo gedit ru

find the section you want in it to change 
in my case the phonetic layout

then swap changes you wish to make

for example: from
key	<LatV> {	[    Cyrillic_zhe,    Cyrillic_ZHE	]	};
to
key	<LatV> {	[    Cyrillic_ve,    Cyrillic_VE	]	};

If you want to add a  2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or  FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the +  sighn  ie. U4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options 
then choose the layout switching and chose what option you want

then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

### Post by robertmf on 2008-11-07
[color="darkred"]&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; :-)[/color]

---

