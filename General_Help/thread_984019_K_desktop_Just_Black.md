---
title: "K desktop Just Black"
date: 2008-11-16
forum: General Help
---

### Post by Lex-Man on 2008-11-16
I've installed the KDE desktop from Ubuntu Synaptic Package manager but when I start up a session in KDE I get the loading screen and then it drops straight to black.  Is there anyway to sort this out?

---

### Post by Lex-Man on 2008-11-16
Can anyone help me with this.

I have an ATI 3850 graphics card and have had the same problem with the 32-bit ubuntu.  And I can't use any desktop effects under the 64-bit version.

---

### Post by Mackwic on 2008-11-16
Hello Lex-Man,

Can you see the edge of the windows? If yes, it's easy.

When you're login, start a console login.
After that, you can edit the file ~/.kde/share/config/kwinrc with nano for example.

Look the section [Compositing], make sure enabled = flase. If not. It's the problem.

---

### Post by Lex-Man on 2008-11-16
```
[$Version]
update_info=kwin_focus2.upd:kwin_focus2,kwin_focus1.upd:kwin_focus1,kwin.upd:kde3.0r1,kwin.upd:kde3.2Xinerama,kwin_on_off.upd:kwin_on_off,kwin3_plugin.upd:kde3.2

[Desktops]
Name_1=
Name_2=
Number=2

[Plugins]
kwin4_effect_coverswitchEnabled=true

[Windows]
TitlebarDoubleClickCommand=Maximize
```

That is all the file contains.

---

### Post by Lex-Man on 2008-11-16
It's cool I changed the line

kwin4_effect_coverswitchEnabled=true

to false 

and it worked fine.

---

