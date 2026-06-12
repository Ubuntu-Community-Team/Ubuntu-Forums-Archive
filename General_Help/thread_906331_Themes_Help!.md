---
title: "Themes Help!"
date: 2008-08-31
forum: General Help
---

### Post by tmcw33 on 2008-08-31
I added a theme using emerald themes, but when I started using it, the minimize, maximize and close disappeared. How can I get them back? I deleted the theme thinking things would revert back but no such luck. Also, I'm new to Ubuntu.

---

### Post by tmcw33 on 2008-08-31
Ok, I was able to get the min, max, and close back and it seems as though the theme will only work as long as terminal is open. Once I close terminal the theme disappears and the min, max, and close vanish too.

---

### Post by benerivo on 2008-08-31
Why is there a terminal open in the first place. Do you manually start emerald with emerald --replace. If you do, then just add a startup entry for emerald using System > Preferences > Sessions.

---

### Post by deicidist on 2008-08-31
If you are starting emerald in the terminal, then closing the terminal will close any application that was started using that terminal. It's kind of like starting your car, turning up the radio and then turning the car off...radio won't run if the car doesn't have power. Same thing goes for commands started in the terminal.

However, if you insist on starting applications in the terminal follow it with the '&' symbol. For example:

> user@userpc:~$ gcalctool &For more info, hit this [link]("http://www.watchingthenet.com/ubuntu-tip-how-to-launch-programs-in-the-background-from-a-terminal-window.html").

---

### Post by tmcw33 on 2008-09-01
I was using Terminal because that was what I found to make the themes work in Emerald. Is there an easier way to make themes work? also, I'm new to Ubuntu and don't know how to use the sessions, please explain this further.

---

### Post by sayakb on 2008-09-01
Press Alt+F2 and type in **emerald --replace**
Use an **& **corresponding to a terminal command to run it in background so that you have it running even if you close the terminal. For example, try **emerald --replace & **at the terminal.

---

### Post by billgoldberg on 2008-09-01
In "system -> preferences -> session" you can specify the programs you want to start on boot.

Make a new entry for Emerald.

You can make up what you fill in those boxes, except the "command" box. There you will have to put 

```
emerald --replace
```

Now, if you start your pc those borders will be there. No need to start it manually.

--

If you want to start an app, either use "alt +f2" or add a "&" behind it if you want to use the terminal.

---

