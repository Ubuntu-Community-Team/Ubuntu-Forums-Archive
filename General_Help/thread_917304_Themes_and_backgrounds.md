---
title: "Themes and backgrounds"
date: 2008-09-11
forum: General Help
---

### Post by jkc2103 on 2008-09-11
Well  i know  the backgrounds come with the theme but  i have downloaded some themes..  how would i  apply them?

---

### Post by wolterh on 2008-09-11
If I am not wrong, open "System > Preferences > Appearance" and just drag what you've just downloaded into the application.

---

### Post by jkc2103 on 2008-09-11
lol im on kde though...   its kinda diffrent

---

### Post by wolterh on 2008-09-11
oh...

---

### Post by jkc2103 on 2008-09-11
its cool. but thanks =] how long have you been with linux?

---

### Post by wolterh on 2008-09-11
I've been using it like for one consecutive month. Maybe a little less...
I had used it long ago, when I had a dual boot. Later on, I found out that i just needed ubuntu and wine to run my windows applications.

---

### Post by jkc2103 on 2008-09-11
whats wine?

---

### Post by milasch on 2008-09-11
> **jkc2103 said:**
> whats wine?

Its a set of windows APIs written by 3rd parties to make windows APPs work with linux...

Don't call it an emulator, you may awake deadly zombies that will hunt you until you become one of them.

a little more here if you are interested in the subject:

[http://en.wikipedia.org/wiki/Wine_(software)]("http://en.wikipedia.org/wiki/Wine_(software)")

---

### Post by jkc2103 on 2008-09-11
> **milasch said:**
> Its a set of windows APIs written by 3rd parties to make windows APPs work with linux...

Don't call it an emulator, you may awake deadly zombies that will hunt you until you become one of them.

a little more here if you are interested in the subject:

[http://en.wikipedia.org/wiki/Wine_(software)]("http://en.wikipedia.org/wiki/Wine_(software)")

oh cool thanks.  how would i  get it?

---

### Post by milasch on 2008-09-11
```

sudo apt-get install wine

```

then configure it with

```

winecfg

```

don't forget to visit [http://www.winehq.org/]("http://www.winehq.org/") to find out if the application is known to work in their database.

then to install the application, just do:

```

wine /path/to/installer.exe

```

most likely your applications will install under /home/your_user/.wine/drive_c/Program Files

not all programs work with wine though... or even, they need some tweaking to work properly...

---

### Post by jkc2103 on 2008-09-11
> **milasch said:**
> ```

sudo apt-get install wine

```

then configure it with

```

winecfg

```

don't forget to visit [http://www.winehq.org/]("http://www.winehq.org/") to find out if the application is known to work in their database.

then to install the application, just do:

```

wine /path/to/installer.exe

```

most likely your applications will install under /home/your_user/.wine/drive_c/Program Files

not all programs work with wine though... or even, they need some tweaking to work properly...


I downloaded wine. got that..    do i just  put  in   wine/path/to/installer.exe after?   or how does that work?

---

### Post by milasch on 2008-09-11
lets say you've downloaded a program from the internet in your desktop...

so to install it you'd do:

```

cd /home/your_user/Desktop
wine file_you_just_downloaded.exe

```

if it just works, it'll open the installer. 

Remember you need to understand things and read a little in order not to get very frustrated with trying new things in linux... the learning curve may not be very steep, and it's easy to give up just like I did several times.

---

### Post by jkc2103 on 2008-09-11
lol yeah im still learning.. lol  but im in kde.  what if you have adobe photoshop c2 on a cd?

---

### Post by jkc2103 on 2008-09-11
bump.

---

### Post by milasch on 2008-09-12
In this case you have to google it, there are some guides showing how to do it. Basically you have to copy a few files from a working windows installation into your wine directory.

You can copy from a guide that show how to do it with Dreamweaver.

---

