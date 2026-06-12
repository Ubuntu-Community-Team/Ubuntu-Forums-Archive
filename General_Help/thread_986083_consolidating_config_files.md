---
title: "consolidating config files?"
date: 2008-11-18
forum: General Help
---

### Post by jerremy-tamlin on 2008-11-18
Hi, I'm just starting to figure out how to configure gnome to my liking, namely mime types and default applications.

The [GNOME Desktop System Administration Guide]("http://library.gnome.org/admin/system-admin-guide/2.24/mimetypes-registering.html.en") says to put changes in the defaults.list file either in the users directory ~/.local/share/applications/ for user specific changes or in /etc/gnome/ or /usr/local/share/applications/ for system wide changes.

My question is this: Why are there two system wide configuration files for the same thing and should I consolidate them to make system maintenance easier?

I read somewhere that /etc/gnome/defaults.list is a symlink to /usr/local/share/applications/defaults.list

Well, on my system it's not...
```
:/etc/gnome$ ls -l
total 12
drwxr-xr-x 2 root root 4096 2008-09-18 22:13 config
-rw-r--r-- 1 root root 7242 2008-05-29 20:23 defaults.list
```
Should it be?

I love the way Ubuntu just works, but I'd like my system to be neat and tidy. That way it's easier for me to understand, and in tidying it I will learn how it works. This is my only computer though and it only has ubuntu installed. I can't afford to break it.

Thanks for your help.

P.S.
If anyone knows of any really good introductions to system administration for single user computers I'd love to hear about them.
Cheers

Edit: Just found that /etc/gnome/defaults.list IS symlinked to /usr/local/share/applications/defaults.list at least when I edit one the other is changed at the same time. Why doesn't 'ls' show that it's a link?

---

### Post by jerremy-tamlin on 2008-11-18
Ahhh, solved my own problem.

/etc/gnome/defaults.list is a not symlinked to /usr/local/share/applications/defaults.list

/usr/local/share/applications/defaults.list is symlinked to /etc/gnome/defaults.list

Well there we go, at least I don't have to feel as dumb as I would if someone else had had to point it out to me. :rolleyes:

---

### Post by jerremy-tamlin on 2008-11-20
Now I HAVE found another one that's not symlinked.

I have /usr/local/share/applications/default.list->/etc/gnome/defaults.list and /usr/share/applications/default.list

```
:~$ ls -l `sudo locate defaults.list`
[B]-rw-r--r-- 1 root  root  7242 2008-11-19 00:11 /etc/gnome/defaults.list
[/B]
-rw-r--r-- 1 jesse jesse  107 2008-11-20 20:31 /home/jesse/.local/share/applications/defaults.list
[B]-rw-r--r-- 1 root  root  2817 2008-07-14 01:32 /usr/local/share/applications/defaults.list
[/B]lrwxrwxrwx 1 root  root    24 2008-09-18 21:26 /usr/share/applications/defaults.list -> /etc/gnome/defaults.list
```

These two files are different.
Should I consolidate the two?

---

