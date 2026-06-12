---
title: "[SOLVED] compiz - no window border."
date: 2008-09-25
forum: General Help
---

### Post by tacticalbread on 2008-09-25
whenever I use the Compiz Fusion Icon to switch the Window Manager from Metacity, to Compiz, the window border completely disappears.

I was following a tutorial, and it told me to remove all previous versions of compiz-fusion, so I did, and rebooted my PC, but now this happens.

[img]http://img214.imageshack.us/img214/6333/screenshotaq6.png[/img]

---

### Post by anotherdisciple on 2008-09-25
You just need to run the window decorator.... Hit Alt+f2 and type:

```
gtk-window-decorator --replace
```


Or, if you are using Emerald:
```
emerald --replace
```

---

### Post by tacticalbread on 2008-09-25
I tried it, but I still get the same thing.

---

### Post by jualin on 2008-09-25
Which one have you tried, Emerald or GTK-Windows decorator?

---

### Post by tacticalbread on 2008-09-25
I have both of them installed, but I get the same thing, even if I switch to the other.

---

### Post by jualin on 2008-09-25
Have you checked out [this thread?]("http://ubuntuforums.org/showthread.php?t=611311")

---

### Post by tacticalbread on 2008-09-25
[quote=Word]I installed xserver-xgl restarted and it worked. Dont ask me how[/quote]

I did that, and it did, and it didn't work. The window border shows up, but I can't move windows, and I also can't change the number of workspaces I have. I have three right now, but when I switch to compiz, it shows two, but I can't change how many there are.

---

### Post by jualin on 2008-09-25
For the number of wallpaper, you can right click on the Deskspace applet on the panel and select properties and change it through there. Or you can give [this post]("http://ubuntuforums.org/showpost.php?p=3510110&postcount=7") a try. For the "I can't move windows" issue, check on Compiz that you have the "move windows" plugin enabled, [this thread]("http://ubuntuforums.org/showthread.php?t=620120") explains it a little bit better. Hope this helps!

---

### Post by tacticalbread on 2008-09-26
thanks a lot! I got it all working. most of this was enabled by default when I installed the settings manager last time.

one last thing, whenever I open a new window, regardless of what it is, it opens in my top bar, so I can't get to the border to move it, and I have to move it a different way.

---

### Post by jualin on 2008-09-26
You can always use "Alt+Left mouse click" (holding both at the same time) to move the window when you don't see the border. I don't know if that's what you wanted. Feel free to ask more. I am glad compiz works now for you.

---

### Post by tacticalbread on 2008-09-26
well, yeah. I know I can do that, but I was just wondering why it always opens a window in my top bar. It never did that before. oh well.

thanks for all your help. (:

---

### Post by jualin on 2008-09-27
> **tacticalbread said:**
> well, yeah. I know I can do that, but I was just wondering why it always opens a window in my top bar. It never did that before. oh well.

thanks for all your help. (:

What do you mean by "opens a window in my top bar"? 
Can you post an screenshot of it?

Do you mean that the "window list" which is usually on the bottom panel bar is now on the top panel bar?

---

### Post by tacticalbread on 2008-09-28
whenever I open a window, the bar with file and whatnot, is behind my top bar that has the applications menu and whatnot on it, and the only way I can move it is by holding Alt and clicking it. It's not horrible, but it is kind of annoying.

---

### Post by jualin on 2008-09-28
Make sure that Compiz has the "Place Windows" plugin enabled. Check under System, Preferences, Advanced Desktop Appearance. Maybe that could help.

---

### Post by tacticalbread on 2008-09-29
gah, I feel like such a noob. -_-

all these easy fixes for problems that annoyed me to no end.

thanks for all your help. (:

---

### Post by jualin on 2008-09-30
Glad you got your problem solved!

---

### Post by matmatician on 2008-09-30
hokay, so... i had the same problem but got it to work by doing the following:

alt + f2

type into the box: gnome-session-properties

This will bring up system preferances. Click Add

Type in Run Application in the top box.

Type emerald --replace in the second box

hit ok.

It will work when you restart.


Im using ubuntu hardy heron
emerald themer 0.7.2.

---

