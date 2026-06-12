---
title: "[SOLVED] Cairo-Dock Issue"
date: 2008-11-08
forum: General Help
---

### Post by stat30fbliss on 2008-11-08
I am havung a hard time getting my Cairo Dock to launch.  I followed the steps from here: [https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

And cannot seem to be able to get it to launch.  The app shows up in my Apps/System Tools/Cairo, but when I select it, it does not launch.  

I am like 95% sure I did everything correctly while installing, and did it all in order. 

Anyone have any tips?

---

### Post by eternalnewbee on 2008-11-08
Press ALT-F2 and paste this command: ```
cairo-dock
```

---

### Post by stat30fbliss on 2008-11-08
I tried alt+f2, snd still nothing.  here is a snap of what happens when I try in the terminal.

```
stat30fbliss@stat30fbliss-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

```

:confused:

---

### Post by eternalnewbee on 2008-11-08
OK. That's not how I did it.
I went to **Main Menu > System > Administration > Synaptic Package Manager**, and entered **cairo** into the search bar and chose the relevant packages.
Maybe this helps.

---

### Post by stat30fbliss on 2008-11-08
OK. I searched in the Package Manager, Below is an image of what it looks like.

Both selection boxes only gave me the option to remove cairo...

---

### Post by eternalnewbee on 2008-11-08
OK. What you could try is to reinstall the packages and take it from there.

---

### Post by stat30fbliss on 2008-11-10
Ok, I have re-installed the packages, run the updates, and yet the program still isn't launching.  The icon is still there in My 

Applications>System Tools>Cairo Dock menu. 

I click on it, and it starts to load, then nothing.  

How can I run a good clean uninstall?  I would like to remove everything, then start from scratch, but I am not too familiar on how to do that in Ubuntu.

Thanks

---

