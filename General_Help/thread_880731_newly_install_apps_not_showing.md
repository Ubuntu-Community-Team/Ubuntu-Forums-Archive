---
title: "newly install apps not showing"
date: 2008-08-05
forum: General Help
---

### Post by lohtse on 2008-08-05
Hi all

Some what new to ubuntu... So for give the question..

any way have installed lastest version of ubuntu and am now installing other applications to run on my laptop. But after downloading and installing these apps only about half show up in the applications menu.. how do I get them to display there???

regards
Lohtse

---

### Post by ChumleyEX on 2008-08-05
Ah welcome to the command line. There are apps that can only be used via a terminal.

---

### Post by Shazaam on 2008-08-05
It depends on the "app" that you installed. Some do not have a menu entry. You can open a terminal and type in the name of the program and see if it starts. As an experiment, open terminal (Applications>Accessories>Terminal) and type in ....
```
firefox
```
This should open Firefox.
Now try that with one of the "apps" that you installed.
If it works, go to System>Preferences>Main Menu. Hunt around in the list for your app. If it isn't there you can use the "New Item" button to add it as long as you know the command to start the program.

---

### Post by lohtse on 2008-08-05
> **ChumleyEX said:**
> Ah welcome to the command line. There are apps that can only be used via a terminal.

Surely not nearly half of the apps installed are command line base!!!!!!!!

How ancient is that.... Am trying to introduce kids to linux looks like will just reinstall Windows at this rate...

regards
lohtse

---

### Post by lohtse on 2008-08-05
> **Shazaam said:**
> It depends on the "app" that you installed. Some do not have a menu entry. You can open a terminal and type in the name of the program and see if it starts. As an experiment, open terminal (Applications>Accessories>Terminal) and type in ....
```
firefox
```
This should open Firefox.
Now try that with one of the "apps" that you installed.
If it works, go to System>Preferences>Main Menu. Hunt around in the list for your app. If it isn't there you can use the "New Item" button to add it as long as you know the command to start the program.

Hmmm so there's no command like there was under gnome and kde to just refresh the menus to show the apps then?????

---

### Post by decoherence on 2008-08-05
> **lohtse said:**
> Hmmm so there's no command like there was under gnome and kde to just refresh the menus to show the apps then?????

Yes. This command is run when appropriate after you install a piece of software via Ubuntu's package management system.

Which apps are you trying to install and how are you installing them? This is the main determining factor as to whether or not something shows up in the menu (on a normally functioning system)

---

### Post by lohtse on 2008-08-05
> **decoherence said:**
> Yes. This command is run when appropriate after you install a piece of software via Ubuntu's package management system.

Which apps are you trying to install and how are you installing them? This is the main determining factor as to whether or not something shows up in the menu (on a normally functioning system)

Has been gps based such as gpsbabel and a few games etc and am installing via package manager...

---

### Post by hyper_ch on 2008-08-05
> **lohtse said:**
> How ancient is that....

It is quite "new". You keep to forget the newly introduced "Power Shell" on Windows. So, if Microsoft says it's new then it can't be ancient, right?

---

### Post by lohtse on 2008-08-05
> **hyper_ch said:**
> It is quite "new". You keep to forget the newly introduced "Power Shell" on Windows. So, if Microsoft says it's new then it can't be ancient, right?

agreed lol

---

### Post by hyper_ch on 2008-08-05
a lot of applications are made to run from the terminal. However the terminal is not your enemy. It's your friend :)

What kind of applications do you need?

---

### Post by decoherence on 2008-08-06
> **lohtse said:**
> Has been gps based such as gpsbabel and a few games etc and am installing via package manager...

I don't think gpsbabel is a graphical program. Command line programs don't generally get their own menu entry in Ubuntu because they're accessed from the command line or the run dialog.

I'm sure somebody can suggest some good graphical GPS software. I haven't got a GPS unit myself so I wouldn't know what to tell you.

Any other programs that you think should have menu entries but don't?

---

