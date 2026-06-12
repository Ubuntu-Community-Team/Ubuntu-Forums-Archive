---
title: "Nautilus doesn't open files in Kate/Kwrite (and other weird stuff)"
date: 2008-07-14
forum: General Help
---

### Post by svivian on 2008-07-14
I have uninstalled and reinstalled these because I thought there was a problem with them. But since the upgrade to 8.04 Nautilus won't open any files in Kate/Kwrite. Opening with Text Editor (gedit) works fine.

Also, when I go to file properties > Open With > Add, the list of applications has a ton of duplicates - Kate and Kwrite are there about 10 times each, Text Editor is on there twice. Is there some kind of 'definition' file for these somewhere? Or a simple way to clean this up?

---

### Post by Vivaldi Gloria on 2008-07-14
> **svivian said:**
>  Also, when I go to file properties > Open With > Add, the list of applications has a ton of duplicates - Kate and Kwrite are there about 10 times each, Text Editor is on there twice. Is there some kind of 'definition' file for these somewhere? Or a simple way to clean this up?

In file properties > Open With, select the one you want to remove and click on the remove button with a minus sign on it.

---

### Post by svivian on 2008-07-14
> **Vivaldi Gloria said:**
> In file properties > Open With, select the one you want to remove and click on the remove button with a minus sign on it.

There is no Remove button. I'm talking about when you click the Add button in the Open With tab. You get a dialog titled "Add Application"; it's a big list of apps installed on your system. Many of them are listed 2 or more times.

---

### Post by Vivaldi Gloria on 2008-07-14
> **svivian said:**
> There is no Remove button. I'm talking about when you click the Add button in the Open With tab. You get a dialog titled "Add Application"; it's a big list of apps installed on your system. Many of them are listed 2 or more times.

Ahh. Now I get it. Sorry mate, I don't know that one.

---

### Post by bushda on 2008-07-14
> **svivian said:**
>  I have uninstalled and reinstalled these because I thought there was a problem with them. But since the upgrade to 8.04 Nautilus won't open any files in Kate/Kwrite. Opening with Text Editor (gedit) works fine. [quote]

Setting it to open permanently with a different application is simple. Right click on the file, select properties, click on the Open With tab, and set the program you wish for it to always open with. 

[IMG]http://lh4.ggpht.com/myrtlebeachbums/SHv6ufTz7tI/AAAAAAAAhZA/iJaNwPBT9iE/s800/properties-open-with.jpg[/IMG]


[quote=svivian;5383526] Also, when I go to file properties > Open With > Add, the list of applications has a ton of duplicates - Kate and Kwrite are there about 10 times each, Text Editor is on there twice. Is there some kind of 'definition' file for these somewhere? Or a simple way to clean this up?

I [COLOR=Red]***THINK***[/COLOR] that what you're looking for is /usr/share/applications. That folder is where the links to the items on your menu, as well as some other things, go. I'd check to see if there are multiple entries for Kate and Kwrite in there. Make sure to save a backup somewhere in case you nuke the wrong .desktop file.

---

### Post by svivian on 2008-07-15
> **bushda said:**
> Setting it to open permanently with a different application is simple. Right click on the file, select properties, click on the Open With tab, and set the program you wish for it to always open with. 

[IMG]http://lh4.ggpht.com/myrtlebeachbums/SHv6ufTz7tI/AAAAAAAAhZA/iJaNwPBT9iE/s800/properties-open-with.jpg[/IMG]

I already did that (months ago before upgrading) and Kate is set as the default for .php files. But however I try to open the files - by double-clicking, Enter key, right-click and choosing a program - files will not open with Kate/Kwrite.

I am sure there is nothing wrong with the apps themselves - I ran **kate <filename>** and it opened the file with no problems. I can also drag files from Nautilus to an already-open Kate.

> I [COLOR=Red]***THINK***[/COLOR] that what you're looking for is /usr/share/applications. That folder is where the links to the items on your menu, as well as some other things, go. I'd check to see if there are multiple entries for Kate and Kwrite in there. Make sure to save a backup somewhere in case you nuke the wrong .desktop file.
No, there is only one entry of Kate and Kwrite there. Though there are several entries for Bluefish, Konqueror and some other items.

---

### Post by svivian on 2008-07-15
OK I think I found them in **/home/scott/.local/share/applications**. Removing them from here seems to get rid of them from the "Add Applications" dialog.

However, there is another oddity I just remembered - the applications in this dialog appear to be ordered randomly rather than, say, alphabetically, which would be more logical.

I seem to be able to fix the first problem. I opened the .desktop file in gedit (had to drag+drop of course, because right-click gives only "Open" and no app options) and saw a line: **Exec=kate --use %U**.
So I used that command as a custom command in the "Add Applications" dialog.

Which leads me to the question: why doesn't selecting the app in the standard way - ie choosing "Kate" in the "Add Applications" dialog, which corresponds to the .desktop file - run the %U command?



EDIT: here's the stuff from the .desktop file, in case it means anything to anyone (maybe people can spot an error):
```
[Desktop Entry]
Encoding=UTF-8
GenericName=Advanced Text Editor
[COLOR="#808080"]*language variations omitted*[/COLOR]
Name=Kate
[COLOR="#808080"]*language variations omitted*[/COLOR]
MimeType=text/plain;
Exec=kate --use %U
X-KDE-StartupNotify=true
X-KDE-HasTempFileOption=true
Icon=kate
Path=
DocPath=kate/index.html
Type=Application
Terminal=false
InitialPreference=8
X-DCOP-ServiceType=Multi
Categories=Qt;KDE;TextEditor;
X-Ubuntu-Gettext-Domain=desktop_kdebase


```

---

### Post by Vivaldi Gloria on 2008-07-15
> OK I think I found them in **/home/scott/.local/share/applications**. Removing them from here seems to get rid of them from the "Add Applications" dialog.

Good find there.

> the applications in this dialog appear to be ordered randomly rather than, say, alphabetically, which would be more logical.

That also bothers me. I expect you to continue your series of discoveries and find that one also. ;)

---

