---
title: "/usr/bin/gnome-schedule"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by hlmindustries on 2009-02-20
I just installed gnome-schedule through synaptics (im using ubuntu 8.10 intrepid x86)

and when I try to run it as $currentuser it will instantly close, I tried running through terminal and got the following output...

```
hlm@hlm-linux:~$ /usr/bin/gnome-schedule
/usr/share/gnome-schedule/mainWindow.py:393: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.xml = gtk.glade.XML (config.getGladedir() + "/gnome-schedule.glade", domain="gnome-schedule")
/usr/share/gnome-schedule/atEditor.py:363: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.spin_month.set_range (month, 12)
/usr/share/gnome-schedule/atEditor.py:384: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.spin_day.set_range (day, days)
/usr/share/gnome-schedule/atEditor.py:404: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.spin_hour.set_range (hour, 24)
/usr/share/gnome-schedule/atEditor.py:424: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.spin_minute.set_range (minute, 59)
/usr/share/gnome-schedule/atEditor.py:114: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.spin_year.set_range (year, year + 5847) # TODO: Year +5847 compatability
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 259, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 303, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 404, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/crontab.py", line 518, in parse
    minute, line = self.get_exp_sec (line)
  File "/usr/share/gnome-schedule/crontab.py", line 653, in get_exp_sec
    if line[i] in string.whitespace:
IndexError: string index out of range

```

and when I try running it as $superuser through terminal it fails to load still...

I would show a screenshot, but theres nothing worth looking at...

please help

---

### Post by rugburns499 on 2009-07-26
Hey I had the same problem and fixed it by deleting crontab.

---

### Post by monkman on 2009-12-20
i got the same problem with the "out of range" thing. what exactly did you delete?

i did a "locate crontab" and deleted everything, but noch change. still "out of range".

thx!

ubuntu 9.10(64bit)

---

### Post by floborg on 2010-03-13
I can't get it to start either.  Here's what's output in my terminal:

```
/usr/bin/gnome-schedule
/usr/share/gnome-schedule/gnome-schedule.py:72: Warning: g_set_prgname() called multiple times
  pr = gnome.program_init ("gnome-schedule", config.getVersion(), properties=props)
/usr/share/gnome-schedule/mainWindow.py:158: DeprecationWarning: Use the new widget gtk.Tooltip
  tip = gtk.Tooltips ()
/usr/share/gnome-schedule/mainWindow.py:159: DeprecationWarning: Use the new widget gtk.Tooltip
  tip.enable ()
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 304, in schedule_reload
    data = self.crontab.read ()
  File "/usr/share/gnome-schedule/crontab.py", line 438, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/crontab.py", line 604, in parse
    success, ver, title, desc, output, display, command_d = self.get_job_data (job_id)
  File "/usr/share/gnome-schedule/crontab.py", line 690, in get_job_data
    return True, ver, title, desc, output, display, command_d
UnboundLocalError: local variable 'display' referenced before assignment

```

---

