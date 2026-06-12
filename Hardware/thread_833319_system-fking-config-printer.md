---
title: "system-f**king-config-printer"
date: 2008-06-18
forum: Hardware
---

### Post by Vivaldi Gloria on 2008-06-18
I am pissed off at system-config-printer. This thing crashes more than Windows ME for god's sake. During the time that I used ubuntu this is the only app that I had problems with and I had a lot of problems with it. When you upgrade your system it stops working, when you add a new printer it stops working. WTF? And for some reason reinstalling doesn't work either.

Here we go again. I have a lexmark e350d. Today somebody gave me a HP Photosmart C4100 and I was stupid enough to plug it in. I should have known better. The new printer balloon popped up and I can use the printer. But of course system-config-printer refuses to work. Here is the terminal output:


```

  ..... Lots of lines scrolling fast .....

  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
RuntimeError: maximum recursion depth exceeded

Original exception was:
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 4492, in <module>
    main(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 4466, in main
    mainwindow = GUI(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 528, in __init__
    self.populateList(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 709, in populateList
    self.on_tvMainList_cursor_changed(self.tvMainList)
  File "/usr/share/system-config-printer/system-config-printer.py", line 1610, in on_tvMainList_cursor_changed
    self.fillPrinterTab(name)
  File "/usr/share/system-config-printer/system-config-printer.py", line 1726, in fillPrinterTab
    self.chkPAccepting.set_active(not printer.rejecting)
AttributeError: Printer instance has no attribute 'rejecting'

```

Even though system-config-printer doesn't work, I can still print. This should be added to the feature list of Hardy:

> New in Hardy: system-config-printer will stop working as usual, but now in Hardy you can still print! 

OK. After blowing some steam off now I feel better. Does anyone know anything about this issue?

---

### Post by prshah on 2008-06-18
> **Vivaldi Gloria said:**
> I am pissed off at system-config-printer.  Does anyone know anything about this issue?

Why not use the CUPS admin page directly? system-config-printer servers as a front-end for a front-end for cups. (Yes you read that right). To access cups config directly (it's just as easy to use), open you favorite browser of choice, and give the address as ```
http://127.0.0.1:631
```

Apparently there are some known issues with Xubuntu and system-config-printer, pre-hardy. Don't know if it's applicable to you. Hope the above workaround helps.

---

### Post by Vivaldi Gloria on 2008-06-18
> **prshah said:**
> ... and give the address as ```
http://127.0.0.1:631
```

Wow, didn't know that. Thanks pal.

---

### Post by stchman on 2008-06-18
> **Vivaldi Gloria said:**
> I am pissed off at system-config-printer. This thing crashes more than Windows ME for god's sake. During the time that I used ubuntu this is the only app that I had problems with and I had a lot of problems with it. When you upgrade your system it stops working, when you add a new printer it stops working. WTF? And for some reason reinstalling doesn't work either.

Here we go again. I have a lexmark e350d. Today somebody gave me a HP Photosmart C4100 and I was stupid enough to plug it in. I should have known better. The new printer balloon popped up and I can use the printer. But of course system-config-printer refuses to work. Here is the terminal output:


```

  ..... Lots of lines scrolling fast .....

  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
  File "/usr/lib/python2.5/email/__init__.py", line 82, in __getattr__
    return getattr(mod, name)
RuntimeError: maximum recursion depth exceeded

Original exception was:
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 4492, in <module>
    main(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 4466, in main
    mainwindow = GUI(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 528, in __init__
    self.populateList(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 709, in populateList
    self.on_tvMainList_cursor_changed(self.tvMainList)
  File "/usr/share/system-config-printer/system-config-printer.py", line 1610, in on_tvMainList_cursor_changed
    self.fillPrinterTab(name)
  File "/usr/share/system-config-printer/system-config-printer.py", line 1726, in fillPrinterTab
    self.chkPAccepting.set_active(not printer.rejecting)
AttributeError: Printer instance has no attribute 'rejecting'

```

Even though system-config-printer doesn't work, I can still print. This should be added to the feature list of Hardy:



OK. After blowing some steam off now I feel better. Does anyone know anything about this issue?

All system-config-printer is is a graphical front end for CUPS.  You can install gnome-cups-manager and do the same thing.

---

### Post by Vivaldi Gloria on 2008-06-18
> **stchman said:**
> All system-config-printer is is a graphical front end for CUPS.  You can install gnome-cups-manager and do the same thing.

That works. Thanks.

---

