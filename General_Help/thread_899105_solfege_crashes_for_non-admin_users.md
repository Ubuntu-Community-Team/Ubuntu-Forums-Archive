---
title: "solfege crashes for non-admin users"
date: 2008-08-24
forum: General Help
---

### Post by TJP on 2008-08-24
Does anyone use the 'solfege' program, for music education? It works fine when the sys-admin opens it, but it crashes when anyone else tries it. Specifically, it begins by opening the normal windows, but then it mysteriously crashes, leaving no trace. If I try to run it from the command line I get the following python error message:
Traceback (most recent call last):
  File "/usr/bin/solfege", line 77, in <module>
    src.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/src/mainwin.py", line 802, in start_app
    w.post_constructor()
  File "/usr/share/solfege/src/mainwin.py", line 640, in post_constructor
    self.m_app.display_sound_init_error_message(self.m_app.m_sound_init_exception)
  File "/usr/share/solfege/src/app.py", line 158, in display_sound_init_error_message
    self.m_ui.display_exception_message(e)
  File "/usr/share/solfege/src/mainwin.py", line 497, in display_exception_message
    sourcefile, lineno, func, code = traceback.extract_tb(sys.exc_info()[2])[0]
IndexError: list index out of range

Can anyone help?

---

### Post by n3gbz on 2008-09-24
I just installed solfege and had problems.  This link [http://ubuntuforums.org/showthread.php?t=787881&highlight=solfege]("http://ubuntuforums.org/showthread.php?t=787881&highlight=solfege") solved the problem for me using Ubuntu. 

May be worth a try using Kubuntu!

---

