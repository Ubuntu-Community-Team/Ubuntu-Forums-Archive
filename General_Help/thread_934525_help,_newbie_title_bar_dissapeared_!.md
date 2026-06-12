---
title: "help, newbie title bar dissapeared !"
date: 2008-09-30
forum: General Help
---

### Post by LeitoSR on 2008-09-30
hey guys, im new to ubuntu but i've heared alot about it and today was my first experience..

i installed Feisty and then i wanted to install compiz as well,, the system asked me to download some updates to the system about 200 mega when i was in the terminal i think it downloaded it while i was writing the commands for downloading compiz

and now my problem is i can't find the title bar !!!
see what i mean in the pic

[http://img244.imageshack.us/img244/9894/screenshot0vu9.png](http://img244.imageshack.us/img244/9894/screenshot0vu9.png)

[http://img219.imageshack.us/img219/518/screenshot2aw3.png](http://img219.imageshack.us/img219/518/screenshot2aw3.png)

something may someone help me and tell me how to uderstand the command lines i type in terminal,, and how to open an application after installing it.. cuz i cant find anything anywhere,,

thnx.

---

### Post by bmw4l1f3 on 2008-09-30
I had the same issue.  I cannot remember how i fixed it.  but I will think of it and let you know.

---

### Post by bmw4l1f3 on 2008-09-30
try this:

nm wrong thing

---

### Post by Lindarose84 on 2008-09-30
the same thing happened to me when i was playing around with compiz. somehow, my visual effects settings in the appearance section reset itself to "none" so i lost all of my window borders. they came back when i set it to "extra". that may not be the solution to your problem, but it worked for me after endless hours of trying to fix this thing.

---

### Post by davidryder on 2008-09-30
```
compiz --replace
```

You can also log out and back in. I know there is a way to get them back without having to keep the terminal window open but I don't remember how.

---

### Post by robindemey on 2008-10-01
I have the same problem.

---

### Post by anotherdisciple on 2008-10-01
> **davidryder said:**
> ```
compiz --replace
```

You can also log out and back in. I know there is a way to get them back without having to keep the terminal window open but I don't remember how.

Putting an "&" after the command will make it to where you can close the terminal window.

```
compiz --replace &
```

---

### Post by anotherdisciple on 2008-10-01
You probably don't need to replace compiz though... just the window decorator.

For the default window decorator:

```
gtk-window-decorator --replace &
```

If you installed Emerald, and are using that for your window decorations.

```
emerald --replace &
```

---

### Post by robindemey on 2008-10-01
For me this worked:

Go to System/Preferences/Visual Settings

Go to the tab Visual effects

Chose none

---

### Post by anotherdisciple on 2008-10-01
> **robindemey said:**
> For me this worked:

Go to System/Preferences/Visual Settings

Go to the tab Visual effects

Chose none


That's fine if you don't want the desktop effects. That will disable them.

---

### Post by bmw4l1f3 on 2008-10-01
> **anotherdisciple said:**
> You probably don't need to replace compiz though... just the window decorator.

For the default window decorator:

```
gtk-window-decorator --replace &
```



This is what I did.  I was just coming to post that.

---

