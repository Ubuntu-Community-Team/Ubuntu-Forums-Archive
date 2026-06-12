---
title: "[SOLVED] Textpad"
date: 2008-10-13
forum: General Help
---

### Post by Jacob Collstrup on 2008-10-13
Heya,

I have this wonderful text editor for windows, called 'textpad', I'd very much like to have it work in ubuntu or have a similar program for ubuntu. I need the macro and the column marking functions in my daily work.

Jacob

---

### Post by hyper_ch on 2008-10-13
There are many, many editors native on linux. Have you checked if non supports that?

---

### Post by Jacob Collstrup on 2008-10-13
> **hyper_ch said:**
> There are many, many editors native on linux. Have you checked if non supports that?

I'm not sure if I expressed myself clearly or if I just plain don't understand the question you ask.

Uhm,..I need a text editor where I can markup columns as easily as I can mark up lines. I tried Gedit, and I can't make it do it. So either I need to find one that can or have textpad run in wine.

At this point I don't know any editor for ubuntu that can do this. But also I only know gedit.

And now for my stupid question:oops:: this 'non' you speak of...is that a text editor or did you mean 'none', to both possibilities makes sense.

Jacob

---

### Post by hyper_ch on 2008-10-13
it should be "none"... search the repositories for "editor" or "text editor" and you will find a lot of them.

---

### Post by geirha on 2008-10-13
vim has these features. Emacs probably have them too, though I haven't used emacs that much.

EDIT: Oh, and last time I tried, textpad (version 4.5 I think) worked with wine, and it seems the latest versions do too: [http://appdb.winehq.org/appview.php?iAppId=85](http://appdb.winehq.org/appview.php?iAppId=85)

---

### Post by Jacob Collstrup on 2008-10-13
> **geirha said:**
> vim has these features. Emacs probably have them too, though I haven't used emacs that much.

EDIT: Oh, and last time I tried, textpad (version 4.5 I think) worked with wine, and it seems the latest versions do too: [http://appdb.winehq.org/appview.php?iAppId=85](http://appdb.winehq.org/appview.php?iAppId=85)

Vim is rather slow when doing those block markups...how do I make my textpad from winXP work through wine? I have no idea how to start. I think I have wine now, at least I tried to install it, but I'm not sure if I still need something.

Jacob

---

### Post by justleen on 2008-10-13
Kate does column selecting... and, as mentioned, vi / vim

---

### Post by homemadejam on 2008-10-13
You could just install this program that you like with WINE if you can't find a Linux one that fits your needs.

Jam

---

### Post by geirha on 2008-10-13
You right click the exe-file and select Run with Wine (or something like that). Or from a terminal, you would do something like ```
wine /media/windows/Program\ Files/Textpad/textpad.exe
```

I would, however, recommend you run the installer instead, and install a seperate copy of textpad in your homefolder (C: in wine will be the automatically generated folder ~/.wine/drive_c/ so install it at the default C:\program files\textpad or whatever)

Installing will usually create a launcher in the Applications menu (under a new subsection; wine) and on the desktop.

---

### Post by justleen on 2008-10-13
just stumbled on this [URL="http://en.wikipedia.org/wiki/Comparison_of_text_editors#Basic_features"]wiki...
[/URL], which has an over view per editor, and a feature list which contains columns select.

---

### Post by Jacob Collstrup on 2008-10-14
Heya, I actually managed to get textpad to work through wine by running the installer. Thanks for the help! :)

Jacob

---

