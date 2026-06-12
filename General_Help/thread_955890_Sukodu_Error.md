---
title: "Sukodu Error"
date: 2008-10-22
forum: General Help
---

### Post by nameless01 on 2008-10-22
Hello,
I'm receiving the following error when I open sudoku. Can anyone help me fix the error?

Distribution: Ubuntu 8.04 (hardy)
Gnome Release: 2.22.3 2008-07-09 (Ubuntu)
BugBuddy Version: 2.22.0

System: Linux 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10400090
Selinux: No
Accessibility: Disabled
GTK+ Theme: Human
Icon Theme: Human

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors ---------------------
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 64, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 214, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 191, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 76, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 151, in make_saved_game_model
    sudoku.sudoku_grid_from_string(g['game'].split('\n')[1].replace(' ','')).grid,
  File "/var/lib/python-support/python2.5/gnome_sudoku/sudoku.py", line 232, in sudoku_grid_from_string
    assert(len(s)<=GROUP_SIZE**2)
AssertionError
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 55, in <module>
    start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 1039, in start_game
    u = UI()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 200, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 64, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 214, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 191, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 76, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 151, in make_saved_game_model
    sudoku.sudoku_grid_from_string(g['game'].split('\n')[1].replace(' ','')).grid,
  File "/var/lib/python-support/python2.5/gnome_sudoku/sudoku.py", line 232, in sudoku_grid_from_string
    assert(len(s)<=GROUP_SIZE**2)
AssertionError


I greatly appreciate the help.
-Nameless01

---

### Post by phidia on 2008-10-22
There's a bug report [here]("https://bugs.launchpad.net/gnome-games/+bug/270644") with additional links/info.

---

### Post by nameless01 on 2008-10-22
Thank you very much for the help!

---

