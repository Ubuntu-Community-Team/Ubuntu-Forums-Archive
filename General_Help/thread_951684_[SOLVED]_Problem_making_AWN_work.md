---
title: "[SOLVED] Problem making AWN work"
date: 2008-10-18
forum: General Help
---

### Post by jlbr on 2008-10-18
I installed AWN using the Synaptic, when I try to start the AWN Manager from the System>Preferences menu, I see a window appear for a second, then disappear, so I went to the terminal and tried running it from there, this is what I got:

[PHP]juanluis@juanluis-laptop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue[/PHP]

Any ideas?

---

### Post by Zzl1xndd on 2008-10-18
Just wondering you do have desktop effects turned on correct?

AWN requires Compiz to work.

---

### Post by jlbr on 2008-10-18
mmmmh, I checked and I got compiz installed alright, but then when I go to Appeareance>Visual Effects and try to turn on the "Normal" mode, it refuses to do it... could it be because my laptop is a bit old and my graphics card is not so new? Its an ATI Mobility Radeon 9000IGP

---

### Post by overdrank on 2008-10-18
> **jlbr said:**
> mmmmh, I checked and I got compiz installed alright, but then when I go to Appeareance>Visual Effects and try to turn on the "Normal" mode, it refuses to do it... could it be because my laptop is a bit old and my graphics card is not so new? Its an ATI Mobility Radeon 9000IGP

Hi and that may be the issue, I just installed Hardy on a 7500 with the effects and compiz-check helped me 
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by tjwoosta on 2008-10-18
awn doesn't work without compiz


if you cant get compiz working, i believe cairo dock will work without compiz

---

### Post by Zzl1xndd on 2008-10-18
> **tjwoosta said:**
> awn doesn't work without compiz


if you cant get compiz working, i believe cairo dock will work without compiz

Cairo will work without compiz.

---

### Post by reahjw6 on 2008-10-18
hey
once you loaded AWN did you go to APPLICATIONS -> ACCESSORIES -> then click on AWN there.
Once that has been done awn should start.

---

### Post by jlbr on 2008-10-18
Thank you all, no, it seems I cant run compiz, but I will settle for Cairo, seems to be working just fine.

---

