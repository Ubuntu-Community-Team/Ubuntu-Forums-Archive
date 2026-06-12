---
title: "tried to change keyboard,error pops up when i log in"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by dalert0140 on 2007-02-04
Does your Caps Lock key worK? Mine doesn't. When I tried to fix it, I went to System> Preferences>keyboard>Layouts and tried to change the Model to see if that would work--it didn't and Know every time I log in I get this:
[[IMG]http://img255.imageshack.us/img255/6331/screenshotwc8.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshotwc8.png)
Anybody know what I can do to make the error go away? and what I can do to
 get Cap Locks to work?

I have a Logitech EX110 wireless keyboard by the way if it helps.

---

### Post by dalert0140 on 2007-02-04
I fogot to say that I get the same error if I try to change the keyboard layout while using the system.

---

### Post by dalert0140 on 2007-02-04
Here is what I get when I do 
[FONT="Courier New"][SIZE="3"]xprop -root | grep[/SIZE][/FONT]
```
XKB_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "pc104", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "pc104", "lv3:ralt_switch"

```

Doing this:

[FONT="Courier New"][SIZE="3"]gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/SIZE][/FONT]

```
layouts = []
 model = 
 options = [lv3 lv3:ralt_switch]
 overrideSettings = true

```

It seems though that /desktop/gnome/peripherals/keyboard/kbd doesn't exist.

---

### Post by dalert0140 on 2007-02-04
I found the answer. For some reason Afer much googling I found this thread here in the forums and was givenn by KlineD:

> Ok, for anyone having the same error message when starting gnome here's how to fix it:
First, open Configuration Editor. It's in Applications / System Tools (if you don't have that menu entry you can get it using the menu editor in System / Preferences / Menu Layout / Go to System Tools and place a checkmark on Configuration Editor.

Now, in Configuration Editor navigate to desktop / gnome / peripherals / keyboard / kbd / double click on "layouts" and remove any entry in the Values list. Same goes for "options" (double click, remove entries from list)

Restart X and there's no more error.

Just for future reference.[Here is the thread.]("http://www.ubuntuforums.org/showthread.php?t=323327") It's the last post in there.

---

