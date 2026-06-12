---
title: "How can I develop GTK applications?"
date: 2008-08-19
forum: General Help
---

### Post by Sycron on 2008-08-19
I want to develop some GUIs for my applications but i don't know how to start.

I want for example to build a window with two buttons OK & Cancel. How can I do that ?

---

### Post by renzokuken on 2008-08-19
I believe the GTK+ gui builder is called Glade....it should be in the repos

```
sudo apt-get install glade
```

also check the official site for help [http://glade.gnome.org](http://glade.gnome.org)

---

### Post by amitkher on 2008-08-19
renzokuken is right but just in case you have extremely simple requirements like your example, zenity might be enough for you. It is pre-installed. 
Read the man page:
man zenity

---

### Post by Sycron on 2008-08-19
Thank all of you.

---

### Post by Sycron on 2008-08-19
Also I wish to know if the programs developed with glade are using gcc .. when compiling them... Can applications developed with glade run in windows?

---

### Post by apoth on 2008-08-19
I found this a useful, simple starting point:

[http://zetcode.com/tutorials/gtktutorial/firstprograms/](http://zetcode.com/tutorials/gtktutorial/firstprograms/)

> **Sycron said:**
> Also I wish to know if the programs developed with glade are using gcc .. when compiling them... Can applications developed with glade run in windows?

I know you can compile GTK applications for Windows, I've seen Pidgin and the GIMP running on them. How though, I don't know.

---

### Post by ByteJuggler on 2008-08-19
> **Sycron said:**
> Also I wish to know if the programs developed with glade are using gcc .. when compiling them... Can applications developed with glade run in windows?

Not neccesarily.  You can for example write your program in Python (which is a VM based, bytecode based language), and use wxGlade for the GUI.  Incidentally, the "[SPE]("http://pythonide.blogspot.com/")" Python IDE integrates with 2 GUI designers emitting Python bindings, (wx)Glade and XRCed. Perhaps worth a look as a total environment for what you want to do.) What language are you using/writing in though?

---

### Post by Sycron on 2008-08-19
> **ByteJuggler said:**
> Not neccesarily.  You can for example write your program in Python (which is a VM based, bytecode based language), and use wxGlade for the GUI.  Incidentally, the "[SPE]("http://pythonide.blogspot.com/")" Python IDE integrates with 2 GUI designers emitting Python bindings, (wx)Glade and XRCed. Perhaps worth a look as a total environment for what you want to do.) What language are you using/writing in though?

I want to be a cross-platform programmer. I like alot C / C++ but I can easily acomodate at every language i'll need to use.

---

### Post by ByteJuggler on 2008-08-19
> **Sycron said:**
> I want to be a cross-platform programmer. I like alot C / C++ but I can easily acomodate at every language i'll need to use.

Well then Python is a good choice to add to your toolbox, it is available and usable on pretty much every PC/x86 platform of note you care to mention (Windows, Linux, BSD, OS X) and a bunch of others no doubt.  It is for that very reason that I've taken up learning Python recently as my latest language, since it's a extremely capable cross platform language and one that is used extensively in Ubuntu as well, which enhances its value in that context further.

---

