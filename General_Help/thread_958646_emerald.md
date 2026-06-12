---
title: "emerald"
date: 2008-10-25
forum: General Help
---

### Post by threatrix on 2008-10-25
when I load up a theme with emerald then close the termanal the theme goes away and so does the old one I cant figure out how to get this working right.

---

### Post by Afkpuz on 2008-10-25
Whenever you run a program in the terminal, it continues to run until the terminal is closed.  You just need to execute the program and let it run.


press alt+f2 and enter any command you want.  It will run until you log out.  In your case, you'll enter the command 
```
emerald --replace
```

Now, to get really fancy, you can run that command on boot-up without having to think about it.



Settings>Preferences>Sessions
Click add and give it a name.  Then, type in your command where it says "command".  The comment line is optional.  Then, it will run at every login.  Hope that helps!

---

### Post by threatrix on 2008-10-25
thanks that fixed it for me

---

