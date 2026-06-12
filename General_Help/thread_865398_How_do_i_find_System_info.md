---
title: "How do i find System info?"
date: 2008-07-20
forum: General Help
---

### Post by acidblue on 2008-07-20
Ubuntu 8.04/Gnome
Looking for system info screen.
In Suse it would be  Yast.
What is it in Ubuntu?
Looking for my ethernet chipset info.
Looked under 'System>Preferences' and 'System>Administration' found
nothing useful
please help.

---

### Post by kdcoetzee on 2008-07-20
there is a few apps you can use.

Under System -> Administration -> System Monitor , the first tab

the one is ```
lspic
``` which you type in the terminal

then there is two you need to install to use which is very handy one is a text based, and the other is GUI based.

```
 sudo apt-get install hwinfo 
```

you just need to run it in root

```
 sudo hwinfo 
```

the GUI one is sysinfo (the one I think you want)

```
 sudo apt-get install sysinfo
```

it should be under Applications -> System Tools -> Sysinfo

---

### Post by acidblue on 2008-07-20
Thank you, thats very helpful

---

### Post by fragos on 2008-07-20
"lspic" is a typo. It should be "lspci".

---

