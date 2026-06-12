---
title: "Set double-clck action"
date: 2008-09-12
forum: General Help
---

### Post by mfeltman on 2008-09-12
Hey folks.  How can I configure Ubuntu (gnome/nautilus) to ALWAYS open, say, executable text files rather than run them on a double click?  I'll never run a PHP file by double-clicking it, for example, but rather I always want it to open in gedit without prompting me to ask which to do.  How can I do this?

Thanks!

---

### Post by todak on 2008-09-12
Double-clicking on the file should bring up a dialog asking if you want to run or view the file and I believe it gives you the option to make either action the default behavior.

---

### Post by mfeltman on 2008-09-12
I get the dialog but not that option.  I'm running Hardy.

---

### Post by mc4man on 2008-09-12
In file management -> behavior it should be able to be set, see screen

In system -> preferences ( if not there then enable from edit menus or home folder -> edit -> preferences

Individual files can be set in properties -> permissions  (horizontal bar = ask, ck. = execute, blank= open

---

### Post by todak on 2008-09-12
OK. Right-click on the file and choose **Properties**. Got to the **Permissions** tab and uncheck the **Allow executing file as program** box. Then go to the **Open With** tab and choose the **Text Editor** selection. That will allow you to open that file with a text editor always.

---

### Post by mfeltman on 2008-09-12
I found it in the Behavior tab.  Thanks!!  I wish I could have a per extension rule, but oh well.

---

