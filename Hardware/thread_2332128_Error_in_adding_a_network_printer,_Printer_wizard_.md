---
title: "Error in adding a network printer, Printer wizard freezes"
date: 2016-07-28
forum: Hardware
---

### Post by tanwa2 on 2016-07-28
[COLOR=#111111][FONT=Ubuntu]I am trying to add a network printer that is connected to a Windows 7 machine, to Ubuntu 14.04. My linux box is up-to-date. I can connect to the windows machine to get files and what not through SMB. The "add printer" wizard found the printer connected to the windows computer. Clicking the "verify" button, I get "the printer is accessible." With all that, I'm pretty certain that the computers can see one another. Printer sharing is definitely on on the windows machine as another windows computer can connect to the printer. Upon clicking "Forward" to add the printer to Ubuntu, the following error was shown in the terminal

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]```
Traceback (most recent call last):
  File "/usr/share/system-config-printer/newprinter.py", line 900, in on_btnNPForward_clicked
    self.nextNPTab()
  File "/usr/share/system-config-printer/newprinter.py", line 1060, in nextNPTab
    stderr=file("/dev/null"))
  File "/usr/lib/python2.7/subprocess.py", line 710, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1327, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have also tried to install the driver of the printer prior to doing the add printer, same result.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The printer is HP LaserJet 1012, if it matters. Both "newprinter.py" and "subprocess.py" exist where they should.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]








[/FONT][/COLOR]

---

### Post by weatherman2 on 2016-07-28
I'd try booting a Ubuntu live USB of 14.04 and try adding the printer there.  If you get the same error in the terminal, then you've clearly identified a bug.  If you don't have the same problem, then maybe something in your installation is messed up.

Not sure if this issue is in Gutenprint or something else, but I know I have installed a newer version of Gutenprint (built from source, newer than what was in the repos) to fix issues with printing in Ubuntu.  If you have to...

---

