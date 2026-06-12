---
title: "Help with Keyboard Layout"
date: 2008-10-17
forum: General Help
---

### Post by dremanu on 2008-10-17
Hi Everyone!

Hopefully someone can help me with this situation. I use a US keyboard, and I need to regularly write both in English and Portuguese. Under any version of windows, I can choose US International and it gives me all the keys combinations I need to write in Portuguese. With Ubuntu, I choose US Alternative International, and all the same key combinations work with the exception of one, the accented C, which looks like this: **[SIZE="5"]ç[/SIZE]**...so the question is, is there any way for me to edit this keyboard layout to add this key to it? 

In addition, I  noticed that another layout, the "USA Group toggle on multiply/divide key", does have this character in it, however, I cannot figure out what the key combination is to get it, so perhaps if somebody can clue me in on what to do, then I could use that one instead.

Thanks in advance!

---

### Post by Bucky Ball on 2008-10-17
Open a terminal from Applications ->Accessories and paste in this:

```
sudo nano /etc/X11/xorg.conf
```Then make sure the section that looks like this, looks like this (!) where I have made it bold:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     **"us"**
```

You could add a comma after 'us' and add whatever the abreviation for Portugal is and see how that goes. In 'System->Preferences->Keyboard' you should be able to choose (add) several layouts and that will create a drop down menu near your clock. Hope this helps.

---

### Post by dremanu on 2008-10-17
That was fast, thank you! I'll try your suggestion and see how it works.

Cheers!

---

