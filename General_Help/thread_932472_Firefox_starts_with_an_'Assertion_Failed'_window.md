---
title: "Firefox starts with an 'Assertion Failed' window"
date: 2008-09-28
forum: General Help
---

### Post by bobofdeath9 on 2008-09-28
Hello all,

I've been having a problem with Firefox whenever i start a new window. It opens and fine but also opens another error box saying 'Assertion Failed', and when i try to type a URL in the main search box, it comes up with a slightly different message script but with the same name, 'Assertion Failed'. The google search engine as my homepage works fine but the quick search in the corner also gives the same response. 

If it helps here is a copy of the message that pops up.

I have tried completely removing firefox and then reinstalling it, but to no avail.

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
11:([object XULElement],2)


Thanks for any help

---

### Post by bobofdeath9 on 2008-09-28
Whoops

well the smiles arent supposed to be there so whatever the trigger for them is is what showed up on the window.

---

### Post by bcn17 on 2008-10-04
I'm personally not having the problem but 2 family members are- Any fixes??

EDIT: Fix found- RESTART!! :)

---

### Post by deathlikechaos on 2009-03-29
I beleive it was from an update it happened to me after i updated... restart fixed it for me as well.

---

### Post by gmalecha on 2009-04-29
this is likely due to a update of firefox that updated the configuration files, but there is still a firefox process running so when you start firefox you are running old firefox with new config files.

if you don't want to restart, you can just kill the firefox process:

```

ps aux | grep firefox
kill -9 <firefox process id>

```

---

### Post by jeyno on 2010-08-15
restart?  seems Linux caught the Windows disease ... ?

---

