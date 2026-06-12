---
title: "gedit not allowing me to save"
date: 2008-09-10
forum: General Help
---

### Post by jijin on 2008-09-10
When I run gedit from the applications menu it won't let me save. So I run it from terminal and I get this error:

```
(gedit:17273): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/jijin/.recently-used.xbel', but the parser failed: Error reading file '/home/jijin/.recently-used.xbel': Is a directory.

(gedit:17273): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

```

Running it under sudo works fine. No error.

---

### Post by NoReflex on 2008-09-10
Hello!

If it works fine with sudo you might want to check the file permissions for : /home/jijin/.recently-used.xbel

Best wishes,
NoReflex

---

### Post by jijin on 2008-09-10
I didn't find a ".recently-used.xbel" but I did find a ".recently-used"

I gave .recently-used.xbel full permissions including execute, but I still get he same error message

Should I rename ".recently-used" to ".recently-used.xbel"?

---

### Post by iaculallad on 2008-09-10
Try reading this [launchpad page]("https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/178694"). Problem could be related.

---

### Post by jijin on 2008-09-10
> **iaculallad said:**
> Try reading this [launchpad page]("https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/178694"). Problem could be related.

Possibly. Would it be possible to fix but removing it and adding it back?

Or is renaming .recently-used a good idea?

---

### Post by hyper_ch on 2008-09-10
the error says you tried to edit a directory.

---

### Post by jijin on 2008-09-10
Ok well I found the xbel folder. I gave it 777 perms. No luck.

I can't reinstall it because synaptic wants to also remove ubuntu-desktop

---

### Post by jijin on 2008-09-10
Ok update.. I just deleted the ".recently-used.xbel" folder and the ".recently-used" file.

I get no more error message, and it looks likeit created what it needed.

but now gedit is telling me "The system administrator has disabled saving" on exit, and all save options are greyed out.

---

### Post by iaculallad on 2008-09-10
> **jijin said:**
> Ok well I found the xbel folder. I gave it 777 perms. No luck.

I can't reinstall it because synaptic wants to also remove ubuntu-desktop

The .recently-used.xbel and .recently-used folders are where Ubuntu keeps your recently opened documents.

Try logging out and log back in then retry gedit.

---

### Post by Gazah[RAGE] on 2008-12-21
i am having the same problem except that it has not allowed me to save anything since i installed ubuntu. it comes up with the same message every time i try to save and i have edited all the permissions to allow everything and still no luck please help me as i need to be able to save in this program for my college course.

---

### Post by nlz on 2008-12-21
try another text editor like vim, nano, scite if you really think it's a problem that is caused by gedit (which I doubt).

---

### Post by Gazah[RAGE] on 2009-02-08
well i buggered the install so i had to restart surpriseingly gedit now lets me save after i reinstalled ubuntu

---

### Post by nlz on 2009-02-09
reinstalling because gedit won't let you save is like shooting with an houwitser on a mosquito, but he, if it works for you ;)

good luck

---

