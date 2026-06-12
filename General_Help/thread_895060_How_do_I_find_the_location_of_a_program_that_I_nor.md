---
title: "How do I find the location of a program that I normally launch from the desktop?"
date: 2008-08-19
forum: General Help
---

### Post by tc101 on 2008-08-19
How do I find the actual location of a program that I normally launch
from an icon on the desktop.  For example gedit.  If I right click the
gedit icon and select properties it gives me a command "gedit %U" but
not the actual location.

I need to know the location.  I am using the firefox ftp add on
FireFTP.  If I right click a file in FireFTP that I want to open it
asks me to add the program to open the file with.  Using just "gedit
%U" does not work.  I need the location of gedit and other programs,
such as my html editor.

---

### Post by tamoneya on 2008-08-19
continuing with the gedit example you can find out where it is installed like this:```
tamoneya@tamoneyat61:~$ which gedit
/usr/bin/gedit

```

---

### Post by JawsThemeSwimming428 on 2008-08-19
Most applications are located in /usr/bin

---

### Post by tuxxy on 2008-08-19
> **JawsThemeSwimming428 said:**
> Most applications are located in /usr/bin

+1 

or you could try the locate command
```

locate gedit
```

---

### Post by tc101 on 2008-08-19
Thanks for your help.

---

### Post by sdennie on 2008-08-19
Taking this already good advice even further, to locate binaries installed by a particular package:

```

dpkg -L name_of_package | grep bin/

```

To open a random file as if you'd double clicked it in nautilus:

```

gnome-open name_of_file

```

And, the command line tab completes commands.  So, if you have a vague idea of what a command might be named, start small and keep hitting tab until you find the command you want.  For example:

```

gnome<Tab>-power<Tab>m<Tab>

```

Will run gnome-power-manager.

---

