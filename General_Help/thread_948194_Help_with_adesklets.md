---
title: "Help with adesklets"
date: 2008-10-15
forum: General Help
---

### Post by mzh4ng17 on 2008-10-15
I am new to Ubuntu and I have been trying to install adesklets by following this guide: [http://www.linux.com/feature/55510](http://www.linux.com/feature/55510)  

However, when I try to test calendar, I get this error message: 

Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./Calendar.py", line 14, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - Configuration file parsing error `syntax error', stopped at line 8.

Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x82697cc>> ignored


Does anyone know why this happens?

---

### Post by eternalnewbee on 2008-10-15
I don't know why this happens, but why didn't you install adesklets from Add/Remove programs?

---

### Post by mzh4ng17 on 2008-10-15
If you search for it under add/remove programs it doesn't show up.

---

### Post by eternalnewbee on 2008-10-15
Try to search for it from Main Menu > System > Synaptic Package Manager

---

