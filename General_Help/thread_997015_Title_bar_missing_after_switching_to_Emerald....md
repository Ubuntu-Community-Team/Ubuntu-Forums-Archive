---
title: "Title bar missing after switching to Emerald..."
date: 2008-11-29
forum: General Help
---

### Post by Jshaw on 2008-11-29
Hey everyone,

My problem is that when I select an Emerald theme in the Emerald Theme Manager, and then type "emerald --replace" in the terminal, while it does switch it to the theme I want, the second I close the terminal window, the Theme disappears, along with the title bars on all my windows.

I have attached a picture of what it looks like, for some reason the picture came out jagged, pay no attention to that, just note that the Title bar is gone.

[IMG]http://i13.photobucket.com/albums/a277/bowser60/Screenshot-2.png[/IMG]

I don't have direct access to my Ubuntu PC, I had to head back to college on the day I noticed the problem. I'm using 8.04.

---

### Post by binbash on 2008-11-29
use emerald --replace & 

or you can use gnome to autorun it when you start pc : 

system > preferences > sessions 

add new and write emerald --replace

OR

Open CompizConfig Settings Manager (System Preferences)
go to window decoration plugin.at that window at command section write : 

emerald --replace


PS : I suggest using last one

---

### Post by Jshaw on 2008-11-29
I already tried using the last one, it did nothing at all. I have an nvidia geforce 4. Very old. I'll be sure to try the other options when I get the chance, thanks.

---

### Post by amit.la on 2008-12-19
Hey Binbash.

can you please explain the difference between "emerald --replace" and "emerald --replace &"?


i had the same problem, and it was fixed with your advice using the second command (the one with the "&" at the end).

---

