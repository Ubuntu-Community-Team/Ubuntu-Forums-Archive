---
title: "Cant run ftpbox..please help"
date: 2005-11-27
forum: General Help
---

### Post by touser on 2005-11-27
*edit* wow..i managed to type ftpbox instead of ftpcube in the title..thats just great lol
Hello everyone, i am very new to linux in general and i am trying to run ftpcube as it has support for multithreaded downloading. The install seemed to go fine, but upon trying to execute thre program i get this error every time:

diablo@server:~/ftpcube-0.4.3$ ftpcube
/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wxPython/lib/floatbar.py:5: DeprecationWarning: \

################################################\
# This module is not supported in any way!      |
#                                               |
# See cource code for wx.lib.floatbar for more  |
# information.                                  |
################################################/


  import wx.lib.floatbar
Making main application window.
Making console window.
Making control window.
Traceback (most recent call last):
  File "/usr/local/bin/ftpcube", line 23, in ?
    main.main (sys.argv)
  File "/usr/lib/python2.4/site-packages/libftpcube/main.py", line 211, in main    app.createMainWindow ()
  File "/usr/lib/python2.4/site-packages/libftpcube/main.py", line 75, in createMainWindow
    self.main_window = mainwin.MainWindow (NULL, _("Ftpcube"))
  File "/usr/lib/python2.4/site-packages/libftpcube/mainwin.py", line 114, in __init__
    self.ctrlwin = ctrlwin.ControlWindow (csplitter)
  File "/usr/lib/python2.4/site-packages/libftpcube/ctrlwin.py", line 52, in __init__
    subsizer = self.makeStatusBar ()
  File "/usr/lib/python2.4/site-packages/libftpcube/ctrlwin.py", line 98, in makeStatusBar
    vsizer1.Add (0, 0, 1)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 11472, in Add
    return _core_.Sizer_Add(*args, **kwargs)
TypeError: wxWindow, wxSizer, wxSize, or (w,h) expected for item

---

### Post by INMCM on 2006-05-05
Bump for same issue. Can anybody get this to run on Breezy/Dapper?

---

