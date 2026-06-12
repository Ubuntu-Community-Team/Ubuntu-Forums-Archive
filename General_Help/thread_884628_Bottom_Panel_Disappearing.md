---
title: "Bottom Panel Disappearing"
date: 2008-08-09
forum: General Help
---

### Post by uzzo2 on 2008-08-09
I'm having a problem with my wife's user account. the bottom panel keeps disappearing, i finally was able to just add a new panel. but am still having a problem when trying to minimize a pane.  instead of minimizing to the bottom panel, it's just disappearing. have tried reinstalling xfce to no avail. anyone got any other ideas, thanks in advance.



p.s. my side is working fine, no problems, it's just on my wife's side

---

### Post by plucky on 2008-08-09
> **uzzo2 said:**
> I'm having a problem with my wife's user account. the bottom panel keeps disappearing, i finally was able to just add a new panel. but am still having a problem when trying to minimize a pane.  instead of minimizing to the bottom panel, it's just disappearing. have tried reinstalling xfce to no avail. anyone got any other ideas, thanks in advance.



p.s. my side is working fine, no problems, it's just on my wife's side

Right click on bottom panel and select **Add new Item**
Search for **Task List** and select **Add**

You should now see a window on the bottom panel when you open an application.

Good Luck

---

### Post by uzzo2 on 2008-08-09
> **plucky said:**
> Right click on bottom panel and select **Add new Item**
Search for **Task List** and select **Add**

You should now see a window on the bottom panel when you open an application.

Good Luck
thanks, i tried that and "task list" is not an option in the add to panel list for some reason.

---

### Post by uzzo2 on 2008-08-13
Bump.

---

### Post by uzzo2 on 2008-08-15
one more bump. anyone???

---

### Post by plucky on 2008-08-15
> **uzzo2 said:**
> thanks, i tried that and "task list" is not an option in the add to panel list for some reason.

Are you running Hardy?

If you are then:-

You could try re-installing the panel with ```
sudo apt-get install --reinstall xfce4-panel
```

Does the task list show up in the "add to panel" GUI for your account?

You could try to add another user and see if it works there.

Open a terminal and ```
cd /usr/lib/xfce4/panel-plugins
ls -l
``` and see if **libtasklist.so** is there.

Good Luck

---

### Post by uzzo2 on 2008-08-15
> Are you running Hardy?

If you are then:-

You could try re-installing the panel with
Code:

sudo apt-get install --reinstall xfce4-panel


yes, i am running hardy and that didn't work.
> Does the task list show up in the "add to panel" GUI for your account?

it doesn't show up on my account either, but i'm not having any trouble with my side for some reason.
> Open a terminal and
Code:

cd /usr/lib/xfce4/panel-plugins
ls -l

and see if libtasklist.so is there.

chere@phillip-desktop:~$ cd /usr/lib/xfce4/panel-plugins
chere@phillip-desktop:/usr/lib/xfce4/panel-plugins$ ls -l
total 204
-rw-r--r-- 1 root root 13292 2008-03-13 15:26 libactions.so
-rw-r--r-- 1 root root 15156 2008-03-13 15:26 libclock.so
-rw-r--r-- 1 root root 18452 2008-03-13 15:26 libiconbox.so
-rw-r--r-- 1 root root 53260 2008-03-13 15:26 liblauncher.so
-rw-r--r-- 1 root root 11376 2008-03-13 15:26 libpager.so
-rw-r--r-- 1 root root  9076 2008-03-13 15:26 libseparator.so
-rw-r--r-- 1 root root  7036 2008-03-13 15:26 libshowdesktop.so
-rw-r--r-- 1 root root 11200 2008-03-13 15:26 libsystray.so
-rw-r--r-- 1 root root 14708 2008-03-13 15:26 libtasklist.so
-rw-r--r-- 1 root root 30828 2008-03-13 15:26 libwindowlist.so
chere@phillip-desktop:/usr/lib/xfce4/panel-plugins$ 

it's there, thanks for trying to help me i was just about ready to give up.

---

### Post by plucky on 2008-08-15
Open the "add to panel" GUI and in the search box type in task,see what shows up.It is there so it should be in the box.

Other than that I don't know what to suggest.

Good Luck

---

### Post by uzzo2 on 2008-08-15
> **plucky said:**
> Open the "add to panel" GUI and in the search box type in task,see what shows up.It is there so it should be in the box.

Other than that I don't know what to suggest.

Good Luck
no results with that search, i'm wondering if i need to just delete the user account and redo it. also i've noticed that the text and everything on the panel and toolbars on her side is much larger than mine.

---

### Post by poliltimmy on 2008-08-19
Mine is gone too now. I removed Evolution and now the gnome desktop is gone. Probably my mistake, a dependency, got lost. Is there a why to open teminal with the key board, so I can try to get it back? And ......does anyone know the code
?

---

