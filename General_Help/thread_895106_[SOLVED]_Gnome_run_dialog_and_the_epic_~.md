---
title: "[SOLVED] Gnome run dialog and the epic ~/"
date: 2008-08-19
forum: General Help
---

### Post by unca.paka on 2008-08-19
Maybe it's just me, but ive been searching for about 3days now, and cannot find and answer anywhere.

Im wondering if theres a way to use ~/ in the gnome run dialog(alt+F2).
Not a big deal, I know, just more of a convenience than having to use /home/user/whatever.

---

### Post by krsmit0 on 2008-08-19
do you want to run a program from your home directory or do you want have a program access a file in your home firectory?

~/program    or
gedit ~/somefile.txt

---

### Post by apetresc on 2008-08-19
You do not need to include the "~" at all; in the absence of a leading "/", the gnome run dialog interprets the path as starting from your home directory anyway. Thus, if you have an executable "test" in your Desktop directory, typing "Desktop/test" in the run dialog works already.

For opening files in your home directory in other programs, however, you need ~ the way krsmit had it in his second example (but NOT his first)

---

### Post by unca.paka on 2008-08-19
I want to be able to open my home folder by using ~/ in the run dialog. Whenever I try, I get the error "Cannot Open /home/user/~/Downloads for example. What I'm wanting is an alias to my home directory, such as in a terminal 'cd ~/' takes you to the home directory.

Sorry for not being more specific in the op.

---

### Post by cariboo on 2008-08-19
In a script ~/ will not work, you need the full path eg:

```
/home/user/downloads
```

~/ is actually just a shortcut for /home/user.

Jim

---

### Post by apetresc on 2008-08-19
Oh, sorry, I understand now.

To open the home directory in the gnome run dialog, just type '.' (a single period, no quotation marks).

To open a folder "foo" placed in the home directory, just type 'foo' (no quotation marks)

Hope this helps

---

### Post by apetresc on 2008-08-19
> **cariboo907 said:**
> In a script ~/ will not work, you need the full path 

This is not true:
```
adrian@gauss:~$ echo "echo ~" > test.sh && chmod +x test.sh && ./test.sh
/home/adrian

```
However, he wasn't asking about scripts, he was asking about the Gnome run dialog, which does indeed behave differently.

---

### Post by unca.paka on 2008-08-19
Dear god, its soooo simple. My google-fu is lacking apparently. Thanks for the help.

---

