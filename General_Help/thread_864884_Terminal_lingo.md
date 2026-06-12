---
title: "Terminal lingo"
date: 2008-07-20
forum: General Help
---

### Post by epicbattle on 2008-07-20
Is there by chance, a complete terminal programming list anywhere? Something to just help figure out what I need to type to do certain things? (Exp. sudo...lspci -v....aplay...etc) I hope that makes sense.

---

### Post by lisati on 2008-07-20
One place to look is [http://ubuntuforums.org/showthread.php?t=846097](http://ubuntuforums.org/showthread.php?t=846097)

---

### Post by kuja on 2008-07-20
complete? No, of course not, seeing as every program you can install can be referenced this way. 

Lets see, where to send you for a good start ...  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ibutho on 2008-07-20
Its difficult to list all commands because some vary from distro to distro (and between Unix versions). If you just want to get to grips with the command line, take a look at [Linux Command]("http://www.linuxcommand.org").

---

### Post by coffeecat on 2008-07-20
I'll second Linux Command. Also, if you're a masochist, you could try [rute]("http://rute.2038bug.com/index.html.gz"). :twisted:

And if you want to spend some money, [this is worth having on your bookshelf]("http://oreilly.com/catalog/9780596100292/index.html"). Mine is well-thumbed. Make sure you get the right version. O'Reilly do one or two other Unix nutshells.

---

### Post by p_quarles on 2008-07-20
In addition to what others have said, I'll point out two very basic things that will help you answer your own question. To look up an unknown command's function:
```
man *commandname*
```
This will bring up the manual page for that command. Some of these are very complex, and not always well written. What they will almost always do, however, is give you a basic sense of what the command does.

You can search for commands related to a keyword by typing:
```
apropos *keyword*
```
This will search the entire manual page database and tell you which pages include that term.

---

### Post by hyper_ch on 2008-07-20
search for "foss ubuntu cheat sheet" and "foss command line cheat shee". The most common cli commands and their use are on those two cheat sheets.

---

### Post by coffeecat on 2008-07-20
> **p_quarles said:**
> In addition to what others have said, I'll point out two very basic things that will help you answer your own question. To look up an unknown command's function:
```
man *commandname*
```This will bring up the manual page for that command. Some of these are very complex, and not always well written. What they will almost always do, however, is give you a basic sense of what the command does.

**epicbattle**, what I do to make man pages somewhat more readable is to install konqueror (the kde file browser, but it runs OK in Gnome). Type 'man:*commandname*' in the address bar of konqueror. It doesn't turn a badly-written man page into a well-written one, but it makes it easier to navigate around a long one. And doesn't it look pretty? :)

---

