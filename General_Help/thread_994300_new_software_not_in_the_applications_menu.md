---
title: "new software not in the applications menu"
date: 2008-11-26
forum: General Help
---

### Post by noobux on 2008-11-26
Hello all,
New to linux and after an amazingly smooth install of studio 8.1 i'm finding the learning curve a bit steep.

I've installed Semantik through the add/remove programs gizmo but it has disappeared.  I know it's there but how do i make it appear in the drop down menus?

Similarly i've installed Celtx (after alot of swearing) had it running after install but  that too has disappeared altogether.

Any help with these would be appreciated, i notice i'm not the only one with celtx troubles.

---

### Post by decard_pain on 2008-11-26
have you tried running it from a terminal.
if it runs just edit your menu and add a link for it

---

### Post by ohzopants on 2008-11-26
First of all, can you still run the programs from the command line?

All the items in your applications menu has a corresponding .desktop (I believe they are located in /usr/share, but I'm not sure).  If you find one of those and make a copy of it, you can edit it using gedit to point to the program you want.

---

### Post by noobux on 2008-11-26
thanks for the quick reply guys, haven't learnt the ubuntu cli yet.
found celtx in usr/local  but can't work out how to run it from there or anywhere, no executable

[[IMG]http://img92.imageshack.us/img92/619/celtxiw6.png[/IMG]](http://imageshack.us)
[[IMG]http://img92.imageshack.us/img92/celtxiw6.png/1/w1152.png[/IMG]](http://g.imageshack.us/img92/celtxiw6.png/1/)

can't find semantik at all though add/remove insists it's on the system, even un then reinstalled to try and see where it goes but it's too fast :-(

---

### Post by oldos2er on 2008-11-26
Type "celtx" or "semantik" into a terminal.

---

### Post by noobux on 2008-11-26
semantik works, celtx doesn't. Thanks for your help.

---

### Post by ohzopants on 2008-11-28
In order to run celtx from the command line you will need to ensure that it is in fact "executable" (from the looks of that screenshot it already is).  Then you will either need to specify the full path of the program:
```

/usr/local/celtx/celtx

```
or change to its directory and run:
```

cd /usr/local/celtx
./celtx

```

The ./ at the beginning of that second command tells the computer to look in the current directory.

You may want to do some reading about setting you're computer's $PATH variable and/or making a link to the program in a directory that is already in your $PATH.  Remember: google is your friend (by that I mean you're going to find better explanations through google than I could provide).

---

### Post by Mac Jingles on 2009-01-12
Thanks, that worked for me!

---

### Post by Turd Ferguson on 2009-01-12
You can also right click on the menu and click edit not all programs installed are visible in the menu such as "Document Viewer" but can be if checked in the menu edit. Not sure if this is the case but I figures it would be a good idea to mention

---

