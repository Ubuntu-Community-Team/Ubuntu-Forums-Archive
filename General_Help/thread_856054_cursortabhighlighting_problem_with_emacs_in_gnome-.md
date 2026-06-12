---
title: "cursor/tab/highlighting problem with emacs in gnome-terminal"
date: 2008-07-11
forum: General Help
---

### Post by Nycticorax on 2008-07-11
I'm using emacs22 in a gnome-terminal under ubuntu hardy. My problem
is that I'm experiencing strange and apparently unpredictable cursor
problems. One thing is that sometimes a 'ghost' cursor will get left
behind. It goes away if you run the real cursor over it, but that's
annoying. Another problem is that sometimes all the space representing
a tab will get highlighted (at least in emacs-lisp mode). It seems
like it may all be related to tabs. For example, I'm in Fundamental
mode now, as I type I'm sometimes getting a ghost cursor
left behind. In fact it just happened. Now if I select the guilty text and do

```
~> cat -A
## paste in selected text
## <ctrl>-d
getting     a ghost curso
getting^Ia ghost^Icurso$

```
So where have those tab characters come from?

This only occurs in gnome-terminal; not in emacs22-gtk, or in an xterm. I haven't noticed it in other applications running under gnome-terminal.

Thanks,

Dan

update: It's a [URL="http://bugzilla.gnome.org/show_bug.cgi?id=514632"]bug in gnome-terminal
[/URL]

---

