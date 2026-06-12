---
title: "[SOLVED] Package name for Ubuntu's user management program?"
date: 2008-08-10
forum: General Help
---

### Post by Alucard-sama on 2008-08-10
Okay so I've been fiddling around with building a Fluxbox based Ubuntu installation from the Server disc for Hardy Heron and everything was going sweet until I started trying to edit users and groups from the command line and broke my whole system.
So I'm wondering what the package name for the Ubuntu GUI program for editing group/user settings is?

---

### Post by sdennie on 2008-08-10
```

$ dpkg -S /usr/bin/users-admin 
gnome-system-tools: /usr/bin/users-admin

```

So:

```

sudo apt-get install gnome-system-tools

```

---

### Post by Alucard-sama on 2008-08-10
Sweet thanks.
Shame it comes lumped in with a bunch of other stuff, oh well I'm not too bothered.

---

### Post by cariboo on 2008-08-10
If you are building a sever I would suggest using a web based server administration suite like webmin to save the overhead of a gui and all the associated problems if you video card isn't supported. Check out Webmin, they even have a demo you can try out online webmin is available here:

[http://www.webmin.com/](http://www.webmin.com/)

You look at a howto here:

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

About half way down the page is the webmin howto, it is for an older version, but it still works.

Jim

---

