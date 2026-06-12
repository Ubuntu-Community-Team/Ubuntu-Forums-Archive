---
title: "Sreem Syntax highlighting XML files."
date: 2008-07-29
forum: General Help
---

### Post by gazotem on 2008-07-29
Hello all, The Screem website states: 

> Syntax Highlighting

    As you would expect there is support in the editor for syntax highlighting, to allow easy identification, at a glance, of what HTML is present. This is of course customisable via the application preferences to whatever colours you like, **_[COLOR="Red"]or even more so by editing the XML syntax files to highlight the patterns you want.[/COLOR]_**

    As SCREEM is a GNOME based application it supports highlighting all the languages that are supported in the GNOME default text editor.


So from that I was trying to find the place to put/edit the xml syntax files, but I have not had any luck.  Can anyone point me in the right direction?

Thanks a lot.

---

### Post by y-lee on 2008-07-29
> As SCREEM is a GNOME based application it supports highlighting all the languages that are supported in the GNOME default text editor.


Hmm see [Custom Code Highlighting for gedit - and your system]("http://ubuntuforums.org/showthread.php?t=736843").

Accordingto that the xml files should be found /usr/share/gtksourceview-2.0/styles/ 

Note for older versions of ubuntu it maybe something like /usr/share/gtksourceview-1.0/language-specs

hope that helps

---

### Post by gazotem on 2008-07-30
> As SCREEM is a GNOME based application it supports highlighting all the languages that are supported in the GNOME default text editor.

Yes, that is where I am confused.  Essentially what I want to do is access the /usr/share/gtksourceview-2.0/styles/Oblivion.xml SyntaxHighlighting style that comes packaged with gtksourceview-2.0 in Screem (Edit->Preferences->SyntaxHighlighting) as well as another style I created myself.   I would stick with gedit but from what I am gathering it does not have auto-completion for PHP.

Obviously this isn't urgent whatsoever so any help is great.

---

### Post by y-lee on 2008-07-30
> Yes, that is where I am confused. Essentially what I want to do is access the /usr/share/gtksourceview-2.0/styles/Oblivion.xml SyntaxHighlighting style that comes packaged with gtksourceview-2.0 in Screem (Edit->Preferences->SyntaxHighlighting) as well as another style I created myself.

Do you not have a Oblivion.xml at /usr/share/gtksourceview-2.0/styles/ ?

if you do and wish to edit it

```
gksudo gedit /usr/share/gtksourceview-2.0/styles/Oblivion.xml
```

Now edit the file and save your changes. The changes should effect both screem and gedit.

One way to add a style you create your self or to create one open gedit as root

```
gksudo gedit
```

 and save your file to the directory **/usr/share/gtksourceview-2.0/styles/ **just be sure to name it ***something*.lang** where *something* is the name you wish it to have, for example mumps.lang for a style for the mumps programming language.

> I would stick with gedit but from what I am gathering it does not have auto-completion for PHP.

Hmm never thought about auto-completion for php on gedit. I will give it some thought maybe and get back with you. Screem is a good editor but I think of it as more for HTML and such like that than anything but use it for whatever you want.

---

### Post by gazotem on 2008-07-30
Okay, that makes a lot of sense... probably should have realized that myself.  Thanks for direction.


What freeware php editor do you recommend?  I have gPHPedit which I have not messed with too much.  Bluefish is real nice but I find it a little bit cluttered.  I have been using gedit the most right now with some great plugins, it just gets it done for me but I like trying out new programs cause sometimes it takes awhile for the small features to set in.

I also have Quanta but have not looked at it yet.

Also, any opinion on the phpEclipse plugin?

Screem supposedly has some crashing issues but I was going to give it a go but if you have any other recommendations I am all ears.


Thanks again.

---

### Post by y-lee on 2008-07-30
I suppose gedit does lack auto completion, I am not a big gedit user but I did find this rather useful post [Customizing gedit as a Web Developer’s IDE]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html").

---

### Post by gazotem on 2008-07-30
> I suppose gedit does lack auto completion, I am not a big gedit user but I did find this rather useful post Customizing gedit as a Web Developer’s IDE. 

Yeah, been there, its a great walk-through.

Thanks.

---

### Post by y-lee on 2008-07-30
> **gazotem said:**
> What freeware php editor do you recommend?  I have gPHPedit which I have not messed with too much.  Bluefish is real nice but I find it a little bit cluttered.  I have been using gedit the most right now with some great plugins, it just gets it done for me but I like trying out new programs cause sometimes it takes awhile for the small features to set in.

I am not the person to ask that as I don't know or code in php and if i did I would use vim or gvim. lol. that would probably be my advice use Vim or emacs but I would suspect you are looking for something easier to learn and you might get better responses if you ask this question on the programming part of the forums.

Anyway maybe somebody will come along with better advice on this issue for you so this serves mostly as a bump. :)

As for screem crashing I played around with it for a couple months and never had it crash. your results may differ tho. good luck.

---

