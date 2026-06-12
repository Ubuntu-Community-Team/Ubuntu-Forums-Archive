---
title: "[SOLVED] Chmod Acting Weirdly"
date: 2008-10-23
forum: General Help
---

### Post by blazingpie on 2008-10-23
[edit] don't mind me, I missed the obvious[/edit]

Hi all,

This is probably a newbie mistake, but anyway.

I'm using Ubuntu 8.04..1

I have a directory which apache (www-data) is unable to access. If I use chmod -R 0777, it can access it fine as www-data:

$ ls -alh h
total 280K
drwxrwxrwx  5 bpie bpie 4.0K Oct 23 11:51 .
drwxr-xr-x 17 bpie bpie 4.0K Oct 23 11:51 ..
-rwxrwxrwx  1 bpie bpie   25 Oct 23 11:51 .htaccess
-rwxrwxrwx  1 bpie bpie  55K Oct 23 11:51 1.html
-rwxrwxrwx  1 bpie bpie  49K Oct 23 11:51 2.html
-rwxrwxrwx  1 bpie bpie  45K Oct 23 11:51 3.html
-rwxrwxrwx  1 bpie bpie  44K Oct 23 11:51 board.html
drwxrwxrwx  2 bpie bpie 4.0K Oct 23 11:51 res
-rwxrwxrwx  1 bpie bpie 4.3K Oct 23 11:51 rss.xml
drwxrwxrwx  2 bpie bpie  16K Oct 23 11:51 src
drwxrwxrwx  2 bpie bpie  32K Oct 23 11:51 thumb

However, the minute I chmod -R 0776 the directory (what I want to be for the meantime), I can't access is as www-data

$ ls -alh h
ls: cannot access h/thumb: Permission denied
ls: cannot access h/res: Permission denied
ls: cannot access h/board.html: Permission denied
ls: cannot access h/rss.xml: Permission denied
ls: cannot access h/3.html: Permission denied
ls: cannot access h/.htaccess: Permission denied
ls: cannot access h/1.html: Permission denied
ls: cannot access h/..: Permission denied
ls: cannot access h/src: Permission denied
ls: cannot access h/.: Permission denied
ls: cannot access h/2.html: Permission denied
total 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
-????????? ? ? ? ?            ? .htaccess
-????????? ? ? ? ?            ? 1.html
-????????? ? ? ? ?            ? 2.html
-????????? ? ? ? ?            ? 3.html
-????????? ? ? ? ?            ? board.html
d????????? ? ? ? ?            ? res
-????????? ? ? ? ?            ? rss.xml
d????????? ? ? ? ?            ? src
d????????? ? ? ? ?            ? thumb

Can someone shed light on this? I mean, 775 works, but www-data then can't write to the dir, which it needs to do...

---

