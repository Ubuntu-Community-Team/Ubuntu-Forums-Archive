---
title: "How to hide international fonts?"
date: 2008-07-17
forum: General Help
---

### Post by leenwebb on 2008-07-17
Hi all,
Can anyone enlighten me as to how I can hide/disable international fonts in Hardy Heron? I know how to install new fonts, but the font selection menus in GIMP and Open Office are chock-full of fonts I don't use  (I am, sadly, fluent only in languages which share the english alphabet).  

I don't mind uninstalling them (if that's the only way to pare down my menus), though I'm not sure how to go about doing that, either.

Thanks!
Eileen

---

### Post by unutbu on 2008-07-17
Type
```

dpkg --get-selections | grep ttf-
```

This will show you all the packages on your system that start with ttf-. Each installs some truetype fonts.

Select a package that you think you don't want. Type

```
dpkg --listfiles PACKAGE | more
```
(Press 'q' to quit 'more').

This will allow you to see the FILENAMEs you are about to remove. You can also take a look at the font by typing

```
gnome-font-viewer FILENAME

```

When satisfied you want to get rid of it, type

```
sudo apt-get purge PACKAGE
```

---

### Post by fragos on 2008-07-17
The simplest approach is to run the Synaptic Package Manager. Search for ttf and you'll get a list of all available and some font packages. Scan the list for installed fonts. Left click a font and you get a description. Mark for removal, those you no longer want. As well as giving you a shorter list to select from, Open Office will start faster.

---

### Post by Ichido on 2008-12-04
> **unutbu said:**
> Type
```




[CODE]gnome-font-viewer FILENAME

```

When satisfied you want to get rid of it, type

```
sudo apt-get purge PACKAGE
```


Can I 

*sudo apt-get purge FILENAME*

To REMOVE a particular FONT?

---

### Post by unutbu on 2008-12-04
Hi Ichido,
The command "sudo apt-get purge " expects a package name, not a file name. However, you can do this:
```

dpkg -S FILENAME
```

replacing FILENAME with the path to the ttf file.

This command should tell you which package installed the ttf file, if it was installed via the APT packaging system.

Using the output of the "dpkg -S" command, you can then run
```

sudo apt-get purge PACKAGE
```

---

### Post by sicofante on 2008-12-24
I've stumbled upon this thread while looking for a way to hide that lot of international fonts I absolutely don't need in my word processing or spreadsheets. But I do not want to remove them because I find it clean that Firefox shows the right glyphs when hitting an Arab, Chinese or Thai page, for instance.

So I would ask how to hide these fonts from font selection menus in OpenOffice, Abiword or any other application that allows font selection, but not removing them from the system, because I want them for Firefox or files I download which might use them.

I don't know GTK+ or Qt but I understand all these apps use a "font selector" widget (or whatever they call it these days) and that's where the trick should be found, but how?

Is it possible?

---

