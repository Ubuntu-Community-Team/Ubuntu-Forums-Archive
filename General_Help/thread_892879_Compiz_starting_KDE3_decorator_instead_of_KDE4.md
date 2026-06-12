---
title: "Compiz starting KDE3 decorator instead of KDE4"
date: 2008-08-17
forum: General Help
---

### Post by drbob07 on 2008-08-17
I recently installed compiz-fusion from the repos, I am using KDE 4.1 on Kubuntu 8.04.

It would appear that Compiz is starting kde-window-decorator from KDE3, whereas I'd like it to start the KDE4 window decorator.

If I start kcontrol from the command line, instead of systemsettings, I can change the window decorations, but kcontrol only has KDE3 styles, since it is after all a KDE3 app.

Is there any way to have Compiz start the KDE4 window decorator? I'd prefer not to have to use the built in compositing effects since KWin still lacks many plugins and doesn't have as fast of a compositing engine on my old hardware.

Thanks in advance.

---

### Post by Keithamus on 2008-09-30
Just wanted to say I'm also experiencing this problem.

Compiz initiates kde-window-decorator, which is a KDE3 application, and so brings with it all of KDE3's styles. This unfortunately means you can't use any KDE4 themes.

I wish I could get a fix for this! The only solution seems to be using emerald, which frankly, sucks.

---

