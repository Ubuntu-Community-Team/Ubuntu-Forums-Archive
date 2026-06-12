---
title: "[SOLVED] Can Firefox be run using Qt?"
date: 2008-07-29
forum: General Help
---

### Post by dodle on 2008-07-29
Unless I'm run, firefox is a Gtk application.  I was wondering if it was possible to use Qt for it so that it would integrate better with the KDE Desktop.

(Please don't make fun of me if the answer is obvious:))

---

### Post by sdennie on 2008-07-29
No, as far as I know, this is not possible.  For a long time Firefox has faked gtk but, with FF3, it seems that xulrunner is more or less using gtk widgets.  I believe KDE can make gtk apps look like the native QT theme but, I'm not sure if the applies to FF3 because it still only appears to be a gtk app.

---

### Post by ibutho on 2008-07-29
There was a Firefox port to Qt, but I guess there wasn't much developer interest so the project seems to have stalled. If you are looking for a good Qt based browser, try [Arora]("http://www.arora-browser.org/"). It uses webkit as a backend which is the same backend used by Safari.

---

### Post by dodle on 2008-07-30
thanks guys/gals, I tried that arora, but it looks like it has got a ways to go.  The only part that I don't like about Firefox on Linux, is when I download.  I think the gtk dialogue box (I guess that's what it would be called) is ugly.  Maybe I'll try that gtk-qt engine thingy.

---

