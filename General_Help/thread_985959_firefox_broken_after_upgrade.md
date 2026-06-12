---
title: "firefox broken after upgrade"
date: 2008-11-18
forum: General Help
---

### Post by mixmaster on 2008-11-18
I've just taken the latest automatic upgrade of firefox 3 on Hardy and now when start it I get this: (the home pages do display)

> 
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0: ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1: ()
2: ()
3: ()
4: epsGetAttr([object Object],hidden)
5: ()
6: ()
7: currentEngine()
8: get_currentEngine()
9: updateDisplay()
10: init()
11: ([object XULElement],4)


When I try to access another page (eg ubuntuforums) I get:
> 
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0: ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1: ()
2: ()
3: ()
4: epsGetAttr([object Object],alias)
5: ()
6: SRCH_SVC_getEngineByAlias([http://www.ubuntuforums.org/](http://www.ubuntuforums.org/))
7: getEngineByAlias([http://www.ubuntuforums.org/](http://www.ubuntuforums.org/))
8: getShortcutOrURI([http://www.ubuntuforums.org/](http://www.ubuntuforums.org/),[object Object])
9: canonizeUrl([object KeyboardEvent],[object Object])
10: handleURLBarCommand([object KeyboardEvent])
11: ()
12: ([object KeyboardEvent])
13: anonymous(textentered,[object KeyboardEvent])
14: fireEvent(textentered,[object KeyboardEvent])
15: onTextEntered()
16: handleEnter(false)
17: onKeyPress([object KeyboardEvent])
18: onxblkeypress([object KeyboardEvent])


And yes, I have restarted firefox.  Twice.
And reinstalled it from the package manager.

Suggestions would be appreciated.

-----------------------

Never mind.  There was some firefox related process hanging around.
"sudo killall firefox" cleaned it out and things work properly now.

---

### Post by gabril on 2008-12-04
Purge it and install it again... might be dependecies thats broken?

$ sudo aptitude purge firefox && aptitude install firefox

---

### Post by Yuki_Nagato on 2008-12-04
Here is a link to creating new Firefox Profiles:

_[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)_

Try creating a new, clean profile, and see if that fixes it.  If not, we know it is not a user setting error.

---

