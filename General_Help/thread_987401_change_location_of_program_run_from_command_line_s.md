---
title: "change location of program run from command line shortcut"
date: 2008-11-19
forum: General Help
---

### Post by matt_wood87 on 2008-11-19
Hi guys,

i use a text editor called Jedit for programming. i recently had it installed and working, since then i've uninstalled it and reinstalled it in a different location.


now when i type jedit on the command line i get the error message
"Unable to access jarfile /home/matthew/jedit/4.2/jedit.jar"

i know where the new location of jedit.jar is,
"/usr/share/jedit/jedit.jar"

but i dont know how to tell the command line to look there when i type jedit, as apposed to the old location.

any help would be much appreciated.

thanks

Matt

---

### Post by KeyserSoze93 on 2008-11-19
a quick fix: 
```

mkdir -P ~/jedit/4.2
ln -s /usr/share/jedit/jedit.jar ~/jedit/4.2

```

In the long term, you might want to look in your home folder, or in /etc for files which such names as .jeditrc or other such configuration files which are still looking in the old locations.

Hey, heres an idea: try su'ing to root and running jedit, to see whether it's a system wide issue or tied to a config file in your home dir...

---

