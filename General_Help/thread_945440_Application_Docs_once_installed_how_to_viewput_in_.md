---
title: "Application Docs: once installed how to view/put in menus ?"
date: 2008-10-12
forum: General Help
---

### Post by Browser_ice on 2008-10-12
I have just installed the apache2 docs but I cannot find it anywhere in my menus. So I assume I have to manually add it somewhere but I have no idea how.

So for any application docs that I will install, how do I add a menu option to view it just like an application?

---

### Post by Julius1988 on 2008-10-12
Right click applications, click on edit menu,Select a category to which you want to insert the application,Click on New Item, give a name for the application and type the command for starting the application.

---

### Post by Browser_ice on 2008-10-12
> **Julius1988 said:**
> Right click applications, click on edit menu,Select a category to which you want to insert the application,Click on New Item, give a name for the application and type the command for starting the application.

But what's the command ?

Using apache2-doc says it cannot execute the application. So I guess it has to use a different command name or something. I whish when installing application docs, it would all do this automatically.

---

### Post by Julius1988 on 2008-10-12
the command u use to start the app from the terminal.

---

### Post by lswb on 2008-10-12
> **Browser_ice said:**
> I have just installed the apache2 docs but I cannot find it anywhere in my menus. So I assume I have to manually add it somewhere but I have no idea how.

So for any application docs that I will install, how do I add a menu option to view it just like an application?

I'm not running apache but I've had the same problem with some other documentation I've installed. If you've installed from the repositories or a .deb package the standard location is an appropriately named subdirectory of /usr/share/doc

Look for /usr/share/doc/apache and see if there is an index.html file, (possibly in a subdirectory of .../apache) If so you can add a menu item with the command 

firefox file:///usr/share/doc/apache/index.html

substituting the correct names as required.

---

### Post by Browser_ice on 2008-10-12
> **Julius1988 said:**
> the command u use to start the app from the terminal.

>apache2-doc
bash: apache2-doc: command not found


Can I get the streight answer ?

Exactly, how do I start the apache2-doc ?

---

### Post by Julius1988 on 2008-10-12
In commands type:
```

 firefox /usr/share/doc/apache2-doc/manual/en/index.html

```

---

