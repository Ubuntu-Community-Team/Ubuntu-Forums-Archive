---
title: "reset keyboard / mouse shortcuts to default?"
date: 2008-08-23
forum: General Help
---

### Post by medusaorange on 2008-08-23
I am very new to Ubuntu and I made a mistake while changing the shortcuts for zoom in compiz config settings manager. Now the shortcuts for both of keyboard and mouse are so messed up... As I move my mouse pointer, it pulls the activated window about instead of moving the pointer about. I cannot click the links in normal way! 

How do I reset the shortcuts to default?

---

### Post by Loaded.len on 2008-08-23
```
sudo apt-get install compizconfig-settings-manager
```

System->Preferences->Advanced Desktop Effect Settings

Click the section you want to modify and then click the broom icon beside whichever value you would like to set to default.

---

### Post by medusaorange on 2008-08-23
I have already tried that and it did not work. =/ Hope there is a way to fix it without having to reinstall the whole thing.

---

### Post by Loaded.len on 2008-08-23
Stand on your head and look in the mirror while you do it? :) 



But seriously, can't you TAB through the Advanced Desktop Effect Settings to accomplish what you want without the mouse?

---

### Post by Loaded.len on 2008-08-23
On second thought... why not open a terminal and type

```
killall compiz.real
```When you're desktop stops hemorrhaging, you should be able to use your mouse as normal in order to reset all your stuff.

---

### Post by medusaorange on 2008-08-23
I had to use CTRL while using my mouse to move about.. ugh. I did get to the advanced desktop effect and turned all of brooms to defaults, but it did not change at all. I had restarted my computer in hopes that everything would go back to normal, but it did not. There must be a way somewhere that can help me to change the setting to default.

---

