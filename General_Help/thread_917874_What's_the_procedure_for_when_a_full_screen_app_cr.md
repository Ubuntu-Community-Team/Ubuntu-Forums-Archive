---
title: "What's the procedure for when a full screen app crashes?"
date: 2008-09-12
forum: General Help
---

### Post by badgaz1 on 2008-09-12
When I am running a full screen application and it stops responding how do I close it? The lack of ctrl + alt + del confuses and disorientates me.

---

### Post by benjick on 2008-09-12
You can try ctrl + alt + backspace to restart X, that should help

---

### Post by badgaz1 on 2008-09-12
That also makes me lose all other running applications though?

---

### Post by Vivaldi Gloria on 2008-09-12
Press ctrl+alf+F1 and log in tty1 terminal.

Give the command

```
psgrep <appname>
```  

to find the pid of the appname. For example,

```
psgrep firef
```

will give a number which is the pid of firefox (if ff is running). Then use the command

```
sudo kill <pid>
```

to kill that app. Here <pid> is the result of psgrep command you used above. To return to desktop use ctrl+alt+F7.

EDIT: Also you can try

```
sudo killall <appname>
```

to kill the app directly without bothering with its pid. (Oops. WRDN beat me to it.)

---

### Post by WRDN on 2008-09-12
An alternative way to exit (though longer) is to press Ctrl, Alt and F1 to drop to the shell. Now, login and type:

```
killall [process]
```

If you are unsure of the process, type:

```
top
```

Now, press Ctrl, Alt and F7 to return to the GUI.

EDIT: Vivaldi, its "pgrep", not "psgrep". I entered the latter command, and the output was "bash: psgrep: command not found".

---

