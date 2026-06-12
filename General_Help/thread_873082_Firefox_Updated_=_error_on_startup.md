---
title: "Firefox Updated = error on startup"
date: 2008-07-28
forum: General Help
---

### Post by rfair404 on 2008-07-28
Edit bodhi.zazen : Duplicate thread, see post #2 (smiles disabled from text).

---

### Post by rfair404 on 2008-07-28
I recently installed Ubuntu 8.04. I'll admit that I am a Linux Nube so beginner directions would be greatly appreciated. Everything was running fine until some updates were installed. I am running Firefox and it suddenly started throwing the following error message at launch.

> ASSERT: *** Search: _installLocation: engine has no file!
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
11:([object XULElement],-2)

Then if I type a url in the browser, I get 
> ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(http://ubuntuforums.org/)
7:getEngineByAlias(http://ubuntuforums.org/)
8:getShortcutOrURI(http://ubuntuforums.org/,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()


The good news is that Google is my home page, and I can search from Google and click links etc.

Any help would be appreciated. Should I try to remove in Synaptic and reinstall?:popcorn:

---

### Post by aysiu on 2008-07-28
It's a bug, but apparently there's a workaround/solution.

Read more here:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/252008](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/252008)

---

### Post by ilovelinux33467 on 2008-07-28
try reinstalling firefox - do this in terminal


```
sudo apt-get remove firefox-3.0
```

Then after that:
```
sudo apt-get update
```

Then:
```
sudo apt-get install firefox-3.0
```

---

### Post by gunashekar on 2008-07-28
i am keen to know which of these posts helps fix the problem
this....

> **aysiu said:**
> 
Read more here:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/252008](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/252008)

or this...?

> **ilovelinux33467 said:**
> try reinstalling firefox - do this in terminal.......


---

### Post by aysiu on 2008-07-28
> **gunashekar said:**
> i am keen to know which of these posts helped fix the problem *help**ed*** - past tense? As far as I know, the OP hasn't acknowledged the problem as fixed yet.

---

### Post by gunashekar on 2008-07-28
> **aysiu said:**
> *help**ed*** - past tense? As far as I know, the OP hasn't acknowledged the problem as fixed yet.

LOL ayisu... pardon my grammar. Just wanted to know which of the two posts help**s** fix the problem.

---

