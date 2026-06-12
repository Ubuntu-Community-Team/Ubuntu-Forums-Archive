---
title: "Adesklets not working"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by akernan on 2009-09-06
I just upgraded to 9.10 and now adesklets is not working.  I realize 9.10 is still in alpha.  Adesklets worked fine with 9.04.

Can anyone help?

---

### Post by akernan on 2009-09-07
I get the following from when I run any desklet.

> Traceback (most recent call last):
  File "./weatherforecast.py", line 337, in <module>
    Events(dirname(__file__)).pause()
  File "./weatherforecast.py", line 98, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.6/dist-packages/adesklets/events_handler.py", line 158, in __init__
    self._alarm()
  File "/usr/lib/python2.6/dist-packages/adesklets/events_handler.py", line 296, in _alarm
    timeout=self.alarm()
  File "./weatherforecast.py", line 144, in alarm
    self._display()
  File "./weatherforecast.py", line 248, in _display
    adesklets.context_set_font(adesklets.load_font('Vera/%d' % self.config['location_font_size']))
  File "/usr/lib/python2.6/dist-packages/adesklets/commands.py", line 706, in load_font
    return comm.out()
  File "/usr/lib/python2.6/dist-packages/adesklets/commands_handler.py", line 103, in out
    raise ADESKLETSError(4,message)
adesklets.error_handler.ADESKLETSError: adesklets command error - font 'Vera/10' could not be loaded


---

### Post by akernan on 2009-09-10
Can anybody help me?

---

