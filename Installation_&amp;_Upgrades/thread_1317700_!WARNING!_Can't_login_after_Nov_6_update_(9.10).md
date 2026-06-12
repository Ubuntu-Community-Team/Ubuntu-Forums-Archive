---
title: "!WARNING! Can't login after Nov 6 update (9.10)"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by gnugu on 2009-11-06
I was building my wife's machine today. Got update for both mine and hers after I installed brand new 9.10 on her machine.

Later I tried to get that Empathy thingy to work but it wouldn't connect to any accounts, so former windoze user I am I told her to reboot.

She clicks restart menu on the right corner and nothing happens. Same for Logout, Shutdown you name it.
So, here I am telling her open console and type "sudo reboot".

Comes to a login screen we type in a pwd and it goes through that shiny screen and comes back to login. NO WRONG pwd warning - I tested with wrong pwd and this is really different. I can also hit Alt+Ctrl+F1 and login in console session no prob, so it is NOT a forgotten PWD!!!

So I say, Honey, enough of this, lets have some wine. Now I'm going to shutdown my computer (the former windoze user I am) and the same symptoms. The menu DOES NOT react!

Lovely wife told me "You better don't shut that s*&^ down!". That's how I'm still writing...

So, WHAT IS GOING ON????

Thanks.

---

### Post by gnugu on 2009-11-06
Forgot to add that my computer was running 9.10 fine since Oct 29 and I was able to shut down and come back. So it must be something we caught today.

---

### Post by gnugu on 2009-11-07
Anybody please?

---

### Post by gnugu on 2009-11-07
Ok I must admit, I uninstalled, no, completely removed Evolution and everything with the name Evolution in it.

I came across this article: [https://lists.ubuntu.com/archives/ubuntu-users/2008-April/144074.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-April/144074.html)

Specifically:
> Just a note to other readers.  If you COMPLETELY UNINSTALL the packages
> suggested here, your gnome desktop will not load and you cannot run any
> programs and the only fix is a clean reinstall.
>
> You must chose to remove, not completely remove.

That sucks!

Any way to repair this other than complete reinstall?

Thanks.

---

### Post by gnugu on 2009-11-07
So, if you do the same mistake as I did and really do remove the evolution, then you will not be able to start your desktop which will look like you can't login.

To fix it get into a console and run:
sudo apt-get install ubuntu-desktop


Solved it thanks to this post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1309961](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1309961)

---

### Post by jheaton5 on 2009-11-07
```
$ sudo aptitude update
$ sudo aptitude install evolution
```
or if you don't like the command line use synaptics
just reinstall evolution

---

### Post by coldReactive on 2009-11-07
install xdm and remove gdm next time you have a problem with logging into gdm.

You'll be able to login then.

See also: [http://bugzilla.xfce.org/show_bug.cgi?id=5954](http://bugzilla.xfce.org/show_bug.cgi?id=5954)

---

### Post by cereal killer on 2009-11-24
Ugh. So what happens for those of us who restarted and can't log in? Clean install? Anyway to do this through live CD, or access terminal before bootup?

---

### Post by cereal killer on 2009-11-24
> **cereal killer said:**
> Ugh. So what happens for those of us who restarted and can't log in? Clean install? Anyway to do this through live CD, or access terminal before bootup?

WOOT! just fixed it.

For those who are wondering, at the GRUB menu, go to "recovery mode" option. There you have an option to do root command *with networking*. Once you can enter commands, type in the line mentioned earlier

sudo apt-get install ubuntu-desktop

---

### Post by gnugu on 2009-11-24
Or when sitting at the login screen simply hit Ctrl+Alt+F1. You have multiple console sessions running. X session is F7.

---

