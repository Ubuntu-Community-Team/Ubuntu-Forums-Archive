---
title: "Does not shutdown"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by harishg on 2007-11-06
I had been using Gutsy for a while and it was working fine until a few days back when the system did not shutdown . When I pressed shutdown the screen goes black and it stays like that and the system does not shutdown. This does not happen everytime but happens now and then. Also when I tried restart it gave the same problem now and then. It happened to me when using both Gnome and Xfce.

Anyone else faced similar problems ?

---

### Post by henklaak on 2007-11-06
Hi,

When you log out, one of the first things that gets switched off is the nice GUI (Graphical User Interface).

When you are looking at the black screen you should be able to switch to text mode.

Ctrl-Alt-F1 through Ctrl-Alt-F6 are simple text terminals (Ctrl-Alt-F7 normally gives you the GUI).

While the system is shutting down, it still prints a lot of information to the text terminals.

Try these key combinations to find the terminal where the system prints its information, so you can look at the messages to see where the shutdown process stops...

Greetings,
Henk.

---

