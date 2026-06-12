---
title: "How do I fix Xmodmap for 8.10?"
date: 2008-11-03
forum: General Help
---

### Post by dcroxton on 2008-11-03
Okay, the old Xmodmap format isn't compatible with the Xorg in Ubuntu 8.10.  I can live with that.  The question is, how do I fix Xmodmap or Xkb or whatever it is I need to fix so I can get the keys I want?  I use a lot of accented keys for various languages, and the ability to set up my own Multi_key and use it to generate accented characters was one of my favourite features of Linux.  What do I do now?

---

### Post by kellner on 2008-11-04
I also would like to know more about how exactly the xmodmap format has become incompatible. Some people have issues with down arrow and other navigation keys not working since the upgrade to 8.10 (see [this thread]("http://ubuntuforums.org/showthread.php?t=965998"), among others). 

I myself have managed to resolve some of these issues through determining keycodes with xkeycaps and updating my old customized xmodmap file. Running that file has restored all functionality (including mapping special characters to key combinations with altgr), except for the page down and some arrow keys. 

So in some ways, old xmodmap files do seem to be useable on 8.10 - but maybe not all their settings? But if so, which ones? More documentation on this would be great. I searched for xmodmap and evdev compatibility issues, but haven't found any useful resources yet.

---

### Post by gladstone on 2008-11-12
In the [release notes](http://www.ubuntu.com/getubuntu/releasenotes/810#X.Org%20evdev%20xmodmap%20incompatibility), do they just mean that the keycodes have changed?

I just updated my .Xmodmap keycodes by determining them all again using:
```
xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' | uniq
```

and all seems to be well...

---

### Post by Icebear on 2008-11-12
How to map a keyboard in ubuntu (xkb)

go toX11/symbols diretory, by typing cd /usr/share/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file, sudo cp ru ru_backup
then load the file up to edit, sudo gedit ru

find the section you want in it to change
in my case the phonetic layout

then swap changes you wish to make

for example: from
key <LatV> { [ Cyrillic_zhe, Cyrillic_ZHE ] };
to
key <LatV> { [ Cyrillic_ve, Cyrillic_VE ] };

If you want to add a 2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the "+" sighn ie. use U4C7 not U+4C7)

from
key <LatN> { [ Cyrillic_en, Cyrillic_EN ] };
to
key <LatN> { [ Cyrillic_en, Cyrillic_EN, U04C8, U4C7 ] };

then save

Then go System>preferences>Keyboard

then click layout options
then click other options button
then click layout option to choose a key to change the keyboard

then choose third level choosers
and choose button you wish to use for:
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

This is what I used to change my keyboard.

---

