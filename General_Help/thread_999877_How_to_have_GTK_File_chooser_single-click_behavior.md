---
title: "How to have GTK File chooser single-click behavior?"
date: 2008-12-02
forum: General Help
---

### Post by hilariusmind on 2008-12-02
Hello folks

I want to have a consistent single-click behavior on Debian/KDE, Kubuntu/KDE and Ubuntu/Gnome.

On debian/KDE and kubuntu/KDE all KDE applications and the desktop are fine. But all GTK-based file choosers still require double-clicking (Example: firefox/iceweasel).

On Ubuntu/Gnome I've configured nautilus for single-click behavior. Now I can single-click on Nautilus and on the desktop. However, GTK-based file choosers still require double-clicking.

How can I configure GTK so that all GTK file choosers use the single-click behavior? (I'm guessing that there is some configuration file somewhere that allows one to configure that)

Thanks

HM

---

### Post by loomsen on 2008-12-02
Open up gconf editor and look for this key, so basically do this:
```
gconf-editor
```

and navigate to
```
/desktop/gnome/peripherals/mouse/
```

There's a key called **single_click**

Check, done.

---

### Post by loomsen on 2008-12-02
ooops, dblpost

---

### Post by hilariusmind on 2008-12-03
> **loomsen said:**
> Open up gconf editor and look for this key, so basically do this:
```
gconf-editor
```

and navigate to
```
/desktop/gnome/peripherals/mouse/
```

There's a key called **single_click**

Check, done.

Hello loomsen

I've looked there but it was already checked (maybe Nautilus had already changed it). However, in Firefox, OpenOffice, Evolution and all other GTK-based applications (except for Nautilus and the desktop), the file chooser still requires double-clicking in folders.

I've searched for other "single-click" keys in gconf-editor, but found only an additional one, which is not editable:

```
/schemas/desktop/gnome/peripherals/mouse/single_click
```

All it seems to be needed is to open **folders** with single-click, because the rest is fine. Maybe we need to create a new key (that the code already checks for)?

This double-click requirement makes it very difficult to teach (older and poor) people how to use the computer, because they never know when to double or to single click. It seems to work if we just tell them: just click once on what you want. Unfortunately, some applications are not qt-based and we can't find a way to configure GTK file choosers for single-click. :-(

Thanks anyway,
HM

---

### Post by loomsen on 2008-12-03
Ouh, exactly the opposite here, I can't handle single-click interfaces at all :D

What you could try is enabling double klicks if you hold the button for some time.
You gotta try, cause, as I said, I like it doubled :) 

[[img]http://www.ubuntu-pics.de/thumb/6723/screenshot_07_u1969p.png[/img]](http://www.ubuntu-pics.de/bild/6723/screenshot_07_u1969p.png)

---

### Post by inigo48 on 2010-03-17
I have the same problem. It is very annoying, sometimes you still have to double click even if you selected single click behaviour in Nautilus. (the firefox save window is a good example)

Any idea how to solve this? Or is this a bug? If yes I think this should be added to the next 100 paper cuts project. This makes the desktop environment kinda inconsistent.

---

### Post by taxus on 2010-03-22
According to this [LinuxQuestions.org post on single click in the file chooser]("http://www.linuxquestions.org/questions/linux-newbie-8/single-click-to-activate-items-gnome-file-locate-dialog-783804/"), this is a [bug that has been around since 2003]("https://bugzilla.gnome.org/show_bug.cgi?id=121113").

I'm frustrated by the same issue. Since switching to Kubuntu 4 months ago, I switched and now prefer the single click. I try to use KDE or Qt apps but it's not always possible, I must use a few GTK+ ones...

At least in Firefox there is a workaround: I installed Flashgot and use KGet as downloader. That way when I download files, the KDE file chooser is used, but it doesn't always work and it doesn't work if I save the HTML page.

---

### Post by hilariusmind on 2011-02-12
Any updates on this?

---

### Post by henriquemaia on 2011-06-11
> **hilariusmind said:**
> Any updates on this?

Same question here, same problem. Any way of achieving this?

---

