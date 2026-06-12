---
title: "Assertion Failed"
date: 2008-11-19
forum: General Help
---

### Post by Ian Lawther on 2008-11-19
This morning on logging into Ubuntu I got a software update message and installed the the upgrades. SInce doing so I get teh following message when I try to use Google in the tool bar or open URLs:-
ASSERTION FAILED
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://www.guardian.co.uk/](http://www.guardian.co.uk/))
7:getEngineByAlias([http://www.guardian.co.uk/](http://www.guardian.co.uk/))
8:getShortcutOrURI([http://www.guardian.co.uk/](http://www.guardian.co.uk/),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(true)
15:onPopupClick([object MouseEvent])
16:onxblmouseup([object MouseEvent])

What is this and how do I fix it?

Ian

NB The message contained parenthesis not the emoticons that the forum is converting them to.

---

### Post by Titan8990 on 2008-11-19
I don't have a solution but I am dropping in to say that the emoticons can be omitted by wrapping that info in code tags.

---

### Post by Ian Lawther on 2008-11-19
The problem seems to have gone away after I restarted the computer and Firefox......

Ian

---

