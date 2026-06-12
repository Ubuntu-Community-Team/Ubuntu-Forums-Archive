---
title: "Xconf..."
date: 2008-09-08
forum: General Help
---

### Post by CasiXtreme on 2008-09-08
Okey, so I changed from XP back to Ubuntu once again, but this time I cant seem to be able to use the "Seperate X screen" as easily as last time...

I am using this program/driver called "EnVy" to install my Nvidia driver, after that I am able to put my screens to TwinView using the Nvidia X Server Settings (Its a think that installed with EnVy, which I bet all of you already know...)

When I try to put this one to use "Seperate X screen" it wont do it, because it wont save it to the xconf file oO

And now I cant fix this problem, last time I used ubuntu I just logged in as root and it worked like a charm from there, but seeing as I am not allowed to login as root anymore... I dont know what to do oO

Help anyone?

---

### Post by fooman on 2008-09-08
run the following in a terminal:

```
gksudo nvidia-settings
```

make your changes for seperate xscreen or twinview under "x server display configuration".  click apply,  then "save to x-configuration file".  log out and back in again.

hope that helps.

---

### Post by skullmunky on 2008-09-08
Hi, I know how frustrating and mysterious that problem is :)

Yes, you cannot log in as root.  This is a security thing so you don't accidentally break things.  Instead, log in normally, and use the "sudo" command.  For the nvidia-settings control panel, you're precisely right, it can't save your xorg.conf file when you run it as a normal user, because only root can write to xorg.conf.  That makes it a pretty useless program, actually, and though in general nvidia are pretty swell with their linux support, that's something they could fix that would be a big help.

Here's how to solve it in the meantime:

```

sudo nvidia-settings

```

that gives you temporary root privilege for that program, so it can save your xorg.conf.

I got fed up with this, and did this:

```

sudo chmod a+w /etc/X11/xorg.conf

```

so now anyone, namely me, can save to that file.  That's probably a Bad Idea from a security standpoint, though, so I don't really recommend it.

I guess a smarter fix would be to set suid on nvidia-settings ...

---

### Post by CasiXtreme on 2008-09-08
Now it actually did let it save, so il try logout and in again now...

edit: That actally worked, thanks!

The only annyoing part is that the one screen is slower reacting then the other -.-"

Thanks again!

---

