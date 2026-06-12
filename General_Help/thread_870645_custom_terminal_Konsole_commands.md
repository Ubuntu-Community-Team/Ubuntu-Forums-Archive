---
title: "custom terminal/ Konsole commands"
date: 2008-07-26
forum: General Help
---

### Post by f1ff134 on 2008-07-26
Everyone knows that if you type "exit" in Konsole, it will, well, exit the program.  But who wants to just be able to type "exit" why not "exunt" or "close"?  That is my question for you.  How to be able to change/ write custom commands in terminal/ Konsole.

Thank you, and remember to eat your :popcorn:

Fluffy

---

### Post by pauper on 2008-07-26
```
alias exunt='exit'
```

[edit:] Make it permanent:

```
 echo "alias exunt='exit'" >> ~/.bash_aliases
```

---

### Post by iaculallad on 2008-07-26
> **f1ff134 said:**
> Everyone knows that if you type "exit" in Konsole, it will, well, exit the program.  But who wants to just be able to type "exit" why not "exunt" or "close"?  That is my question for you.  How to be able to change/ write custom commands in terminal/ Konsole.

Thank you, and remember to eat your :popcorn:

Fluffy

Had you tried doing it with the alias terminal command?

i.e:

To change the "exit" to "exunt"

```
alias exunt="exit"
```

---

### Post by f1ff134 on 2008-07-26
Thank you pauper, but the command to make it permanent didn't work for me.  Also is there a way so that exit _and_ exunt will close the program?

---

### Post by aktiwers on 2008-07-26
Both already works..   the alias works like a shortcut.

If the permanent command did not work, you can add it manually:
```
gedit ~/.bashrc
```and copy/paste this into the new text document and save:
```
alias exunt='exit'
```

---

### Post by f1ff134 on 2008-07-26
Where in the text document do I add it?

---

### Post by pauper on 2008-07-26
How come? 

After adding alias to ~/.bash_aliases update it

```
bash
```

If you are after some root commands. You need to add aliases to
/root/.bash_aliases. [highlight]But[/highlight] I never tested that myself.
So I don't guarantee that it'll work.
Read up "man bash", search "/ALIASES".

> Where in the text document do I add it?

Any new line.

---

### Post by aktiwers on 2008-07-26
Im not on Ubuntu right now, but I think that file is normally empty? 
Just add it to the end of the file and save it. 

Maybe you need to restart X to make it take affect.  You can also have a look here:
[http://ubuntuforums.org/showthread.php?t=264917](http://ubuntuforums.org/showthread.php?t=264917)

---

### Post by f1ff134 on 2008-07-26
Thanks, I will try it in the morning, it is 130 [edit] AM here

---

