---
title: "HOW to set default application for a file type"
date: 2008-07-22
forum: General Help
---

### Post by brijith on 2008-07-22
Hai All,

I would Like to know how to set default application for a specific file type. I know how to do it thorough GUI. What I want to Know is what is actually happening behind GUI.

        Also how to change icon of a file type, say MP3. Where I should Change so that whenever I take mp3 files it is displayed with a given Icon


[COLOR="DarkRed"]**Thanks**[/COLOR]

---

### Post by pauper on 2008-07-22
> I would Like to know how to set default application for a specific file type.

```
ls $HOME/.local/share/applications
vim $HOME/.local/share/applications/defaults.list
vim $HOME/.local/share/applications/mimeinfo.cache
```

> Also how to change icon of a file type, say MP3.

```
grep -C 5 "icon_theme" $HOME/.gconf/desktop/gnome/interface/%gconf.xml
```

Make a note of "icon_theme" string value, i.e. "Human" for example.

Find out mimetype some class of files in question is using:
```
file -i ~/Desktop/example.mp3
$HOME/Desktop/example.mp3: audio/mpeg
```

More on mime is here:
```
less /usr/share/file/magic.mime
```

Now, let's find out the location of the image currently being used.
```
cd /usr/share/icons/Human
find . -name *mime-audio*
```

No results? Run search for entire /usr/share/icons

```
cd ..
find . -name *mime-audio*
./Tangerine/16x16/mimetypes/gnome-mime-audio.png
./Tangerine/22x22/mimetypes/gnome-mime-audio.png
./Tangerine/32x32/mimetypes/gnome-mime-audio.png
./Tangerine/24x24/mimetypes/gnome-mime-audio.png
./Tangerine/scalable/mimetypes/gnome-mime-audio.svg
./gnome/16x16/mimetypes/gnome-mime-audio.png
./gnome/22x22/mimetypes/gnome-mime-audio.png
./gnome/32x32/mimetypes/gnome-mime-audio.png
./gnome/24x24/mimetypes/gnome-mime-audio.png
./gnome/scalable/mimetypes/gnome-mime-audio.svg
```

Note: If you receive no positive results run search for *mpeg* as well.

A single sample from each theme is all you need:

```
display ./Tangerine/scalable/mimetypes/gnome-mime-audio.svg
display ./gnome/scalable/mimetypes/gnome-mime-audio.svg
```

Rename or remove the original--*offensive*--and move there the custom one instead.

P.S. For custom themes run search in $HOME/.icons

---

### Post by CatKiller on 2008-07-22
Vim? Psycho! :)

nano is probably easier for the new user to understand.

---

### Post by pauper on 2008-07-22
> nano is probably easier for the new user to understand.
:evil:
Cardinal Glick: Fill them pews, people, that's the key. Grab the little ones
as well. Hook 'em while they're young.
Rufus: Kind of like the tobacco industry?
Cardinal Glick: Christ, if only we had their numbers.
 
[http://www.imdb.com/title/tt0120655/](http://www.imdb.com/title/tt0120655/)

---

### Post by Flimm on 2010-08-14
Just for those who found this page on their favourite search engine and want to know how to do it through a GUI:

Right-click on the file, choose properties, and click on the "Open with" tab. From there you can select the default application for that file type.

---

### Post by brijith on 2010-08-14
Any one know how to do it through terminal ?

---

### Post by annu2127 on 2010-10-12
In Terminal type gedit /home/averma/.local/share/applications/mimeapps.list ...... now find the mime type & in front of it, the applications associated with it.....just put the application commands of your wish.

---

### Post by Johannes Eva on 2011-01-12
> **brijith said:**
> Any one know how to do it through terminal ?

Maybe this article I wrote could be a source of inspiration. It is a somewhat clumsy way but it works:

_**[How to change file associations on Ubuntu]("http://www.johannes-eva.net/change-the-default-application-ubuntu-linux")**_

(Tested with Ubuntu 10.10 Maverick Meerkat)

---

### Post by BrokenTusk on 2011-02-09
Here is the bare-bones solution to defining what app will open what:

Add this env variable to a session (ie: add to ~/.profile):
export DE="gnome" (even if you're in kde since it's only for xdg-open) 
now modify the MIME associations set in ~/.local/share/applications/defaults.list
and for KDE dudes and dudettes, additionally modify ~/.local/share/applications/mimeapps.list

NOTE: you must kill and restart app launchers like gnome-do for chgs to take affect

---

### Post by scorpious on 2012-05-28
I thought I'd dredge up this post as this is one of the first sites Google finds and some of the solutions are out of date (At least for ubuntu 11.10).

To change the default program using the GUI:
right click the file>>properties>>open with>>choose what program to use>>select 'set as default'.

Easy as that.:guitar:

---

### Post by oldos2er on 2012-05-28
Closed, please don't bump old threads.

---

