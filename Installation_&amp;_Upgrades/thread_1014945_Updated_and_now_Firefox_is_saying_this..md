---
title: "Updated and now Firefox is saying this."
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Melwasul on 2008-12-18
**I fixed it.. Just reinstalled firefox and the errors disappeared. **


I use wubi, upgraded to 8.10 a while back. I just upgraded this morning and now i get this error when firefox starts up and when i go to certain websites. 

```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],6)
```

(Sorry if i put this in the wrong spot.)

Edit:

I get this error when i go to myspace.

```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(myspace.com)
7:getEngineByAlias(myspace.com)
8:getShortcutOrURI(myspace.com,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])
```

---

### Post by Mark Phelps on 2008-12-18
I got exactly the same thing last night. Firefox needs to be restarted a couple of time to reload itself. I rebooted and when I clicked FF, it popped up a window about need to be restarted.  Once I restarted it a couple of times, it started working again.

---

