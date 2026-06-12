---
title: "wnck_window_unminimize(timestamp)"
date: 2008-10-19
forum: General Help
---

### Post by Greg T. on 2008-10-19
I'm stuck. I'm writing a python script that, among other things, invokes wnck to unminimize windows. My goal is to attach this to a gnome launcher. This code serves as an example:

```
#!/usr/bin/env python
import wnck
screen = wnck.screen_get_default()
screen.force_update()
for window in screen.get_windows():
    if window.is_minimized():
        window.unminimize(0) 
```

The problem is that when I execute it, the minimized windows do not unminimize. Instead, they begin to slowly blink in the taskbar, demanding attention. The reason for this is that wnck's unminimize() requires an x server timestamp. If I fail to provide one, I get the error message: "Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly." If I pass a made-up timestamp of 1 or some other number other than 0, it suppresses the error message but doesn't solve the underlying problem. 

As an experiment, I mixed the code above with a hello world pygtk application, so that it was invoked upon a click button gtk event, and used gtk.get_current_event_time() for the timestamp. That worked perfectly. However, it's not a fix because I'm trying to run this script without having to create pygtk windows.

I also can use os.popen('wmctrl -a....') instead of unminimize(), but I'd prefer for this to be a 100% wnck solution.

Any suggestions?

---

