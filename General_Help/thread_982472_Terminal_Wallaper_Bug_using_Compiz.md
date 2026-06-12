---
title: "Terminal Wallaper Bug using Compiz"
date: 2008-11-14
forum: General Help
---

### Post by PherricOxide on 2008-11-14
Okay, so on my Gentoo machine with Fluxbox I have aterm running transparently on my background with no window decorations and always the back window. I thought setting something like that up with Ubuntu 8.10 and Compiz would be easy, but I'm having some strange issues.

I opened a new terminal profile and called it trans, made it transparent, turned off the scrollbar and menu buttons, set the title to always be trans. Then I went into Compiz and set the following in the Window Rules plugin to "title=trans",

Skip Taskbar, Skip Pager, Below, Sticky, Non Movable Windows, Non Resizable Windows, Non Minimizable Windows, Non Maximizable Windows, Non Closable Windows.

Next I went to the Size Rules tab and added a new one with "title=trans" and the size I wanted.

Finally I went to Window decorations and set both decorated windows and shadowed windows to "!title=trans".

I run the terminal, and everything looks fine. However, when I Google anything with the word transparent in it, my Firefox window decorations go away, it becomes stuck to the desktop with no moving or resizing, and becomes the size of my terminal window... For some reason Compiz thinks title=trans is the same as title=*trans*. 

Does anyone have a solution to make it stop doing this, other than setting my title to something really weird that I'll never have in another window's title?

---

### Post by binbash on 2008-11-14
Instead of window title did you try with window class?

---

### Post by PherricOxide on 2008-11-14
Yes, but then I can't open a gnome-terminal and have it normal instead of part of the background. I tried setting it up with aterm too, but that had even more issues. When I give aterm the -geometry command, it seems Compiz ignores it and sets the size/location to wherever it wants, ignoring aterm's command. When I use the window placement plugin to move aterm, it messes up the transparency...

---

### Post by binbash on 2008-11-14
I will try to find a way to do this tomorrow (for my box : )))) )

---

### Post by loomsen on 2008-11-14
You can match the exacr string with

title=^trans$

---

