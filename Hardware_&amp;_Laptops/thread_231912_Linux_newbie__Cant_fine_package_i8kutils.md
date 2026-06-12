---
title: "Linux newbie : Cant fine package i8kutils"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by vanilla.gorilla on 2006-08-08
Ok guys, Ive have looked through the forum and found out pretty much every error with i8kutils, save this one.  I have no idea and keep in mind I am a linux newbie.

When trying to install i8kutils i get::

Reading package lists... Done
Building dependency tree... Done
E: Couln't find padckage i8kutils

All the other errors people have come up with I think I can handle, since there is about 8 threads concerning each error they have with i8kutils.  Do I not have the package? Or how do I find out if I do?

Thanks

---

### Post by louis_nichols on 2006-08-08
Did you enable the extra repos? The package is in Universe:  [http://packages.ubuntu.com/dapper/utils/i8kutils](http://packages.ubuntu.com/dapper/utils/i8kutils)

[Here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html") is how to enable the extra repos.

---

### Post by vanilla.gorilla on 2006-08-08
Thanks! I will try it when I get home(lol I don't have laptop with me).

---

### Post by vanilla.gorilla on 2006-08-10
OK, I added the binary and source for the universe option(I still kinda dont get what all that is about).  Then I installed i8kutils from the 386 deb file I dl'ed.  For the past 2 hours doing nothing my comjputer hovered at 47 C and now dropped to low  40's.  So my guess is that i8kutils is working, but I cannot add it to a panel.  I will search the forums and see what is up, but I can't even run it from any of my menus?  LOL I know this is newbie but how do I make it run?

---

### Post by PCalitrack on 2006-08-12
did you ever figure it out?

---

### Post by PCalitrack on 2006-08-12
Ok, here is the way to get it running.

Try the command
> lsmod | grep i8k
If nothing appears, then your module is not loaded, so load the module
> sudo modprobe i8k
If it is working it should display something similar to this
> patrick@patrick-laptop:~$ i8kctl
1.0 (null) 1BGZF51 57 2 2 94560 93960 0 2
Now, to learn how to use it, issue the commands:
> man i8kctl
> man i8kmon

Hope this helps.

---

### Post by vanilla.gorilla on 2006-08-17
ok, still getting some errors.  I really have never installed anything like this on Linux so again, apologies. 

I sudo su -->  sudo modprobe i8k

and I get ::

FATAL: Error inserting i8k (some horrible path): No such device


I didn't install it? But I ran the rotten installer I dl'ed from the site... What am I doing wrong?

---

