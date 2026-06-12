---
title: "terminal windows size question"
date: 2005-12-03
forum: General Help
---

### Post by daedalusman on 2005-12-03
Is there a way to get the Gnome Terminal window to remember its size. Whenever I open a new I have to resize it and I can't figure out how to get it to remember its previous size, which I would like it to 'cause it would save me the hassel of having to resize it all the time. Thanks

---

### Post by doitashimashite on 2005-12-03
If I were you I would use "konsole" which is a highly configurable terminal.

---

### Post by prodi_g on 2006-01-02
An easy way is to add the Terminal icon to your launcher (toolbar) and then right-click the icon and click on properties.  This will open the launcher properties for that icon.  

Look for the command textbox and add the following: **--geometry #x#** (where #x# represents the terminal dimensions).

Now everytime you launch the terminal program, it's the same as running: gnome-terminal --geometry #x#. 

Hope this helpls.

---

### Post by briancurtin on 2006-01-02
[QUOTE=doitashimashite]If I were you I would use "konsole" which is a highly configurable terminal.[/QUOTE]
it he was using KDE, i would 100% recommend this, but hes not

---

