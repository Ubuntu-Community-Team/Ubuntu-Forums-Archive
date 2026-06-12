---
title: "[SOLVED] Terminal man pages"
date: 2008-08-02
forum: General Help
---

### Post by Ingenue on 2008-08-02
I was wondering if there is a way to print all of the man pages from the terminal. Or perhaps E-mail them to myself. I'm only about two weeks into my Ubuntu experience and it seems to me man is the best (free) resource I can get to expand my command line skills. 

Thanks.:grin:

---

### Post by collinp on 2008-08-02
The only way that i would know of would be to find out every package you have installed, and run the man command on each one.

---

### Post by coffeecat on 2008-08-02
This is not quite what you're after, but it's worth knowing about. It involves installing konqueror (the kde web and file browser). As you are running Ubuntu/Gnome, konqueror will bring in a lot of kde dependencies, but I still think it is worth installing.

Once you've got konqueror installed, open it and type 'man:cp' or man:wget' or whatever man page you want (no quotes). Much easier to read, isn't it? I've never tried to print any man pages out from konqueror, but if you do I would hope the output would retain the formatting.

But why print out all the man pages? Here are two links to get you going:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

And I'm sure others will suggest other things.

---

### Post by mike2357 on 2008-08-02
If printing of manual pages is what you really want to do, the commands follow.  However, there are well over 1000 commands involved, so see coffeecat's excellent advice, or buy a Linux or UNIX book at your local bookstore.

If you wanted to print out the manual pages for one command, such as "ls" for example, do the following:

cd /usr/share/man/man1
gunzip -c ls.1.gz | nroff -man | lpr -P <your_printer_name>

---

### Post by Ingenue on 2008-08-02
I see, thanks for the advice.

---

