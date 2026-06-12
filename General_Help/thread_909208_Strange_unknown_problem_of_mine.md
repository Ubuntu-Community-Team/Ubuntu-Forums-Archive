---
title: "Strange unknown problem of mine"
date: 2008-09-03
forum: General Help
---

### Post by Tim0miT on 2008-09-03
after i logged of yesterday, i restared my Pc and went to logon as normal but i got this message

[[IMG]http://img180.imageshack.us/img180/9343/dsc00393ex1.th.jpg[/IMG]](http://img180.imageshack.us/my.php?image=dsc00393ex1.jpg)

sorry for the poor image quality

so who can help me fix this very random problem:lolflag:

btw, i can still login, i just get pi**ed off when i get random errors xD

---

### Post by arch0njw on 2008-09-04
Let's do what the message says.

After you login, open a terminal.
1. "cd ~"
2. "ls -l .dmrc"
2.a.  What are the permissions on the file, -rw-r--r--?  If the permissions aren't right "chmod 644 .dmrc"
2.b.  Who owns the file?  If not you, then "chown *your_user_name* .dmrc"
3. "cd /home"
4. "ls -l"
4.a. What are the permissions on your directory, drwxr-xr-x?  If the permissions aren't right, "chmod 755 *your-home-dir*"
4.b  Who owns the directory?  If not you, then "chown *your_user_name* *your-home-dir*"

Let me know if you find anything in performing those steps that is odd, or if those steps don't work for you.

---

