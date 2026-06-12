---
title: "adjusting environment variables temporarily using export"
date: 2008-07-10
forum: General Help
---

### Post by mkrahmeh on 2008-07-10
Am trying to adjust environment variables in a single shell session using export, but the issue is that export command is not working as expected. for instance
```
export PS1="\d \@ $LOGINAME$ "
```
causes the prompt to change in the top level shell, and when invoking another shell again as in
```
*new prompt$ *bash
```
the default prompt is displayed 

trying the same with setting $EDITOR works differently
```
EDITOR="/usr/bin/kate"
```
now invoking a program that requires consulting with the EDITOR variable like
```
crontab -e
```
operates using the default editor (which is nano in my case)
though 
```
echo $EDITOR
/usr/bin/kate
``` 
the kate editor is not invoked unless the modified variable is exported 
```
export EDITOR="/usr/bin/kate"
``` 
any explanation gurus..

---

### Post by sdennie on 2008-07-10
Remember that when you start a new shell, it will re-read .bashrc and override the parent shell variables.  That's probably why the prompt is resetting.  $EDITOR isn't resetting because by default it isn't set in the environment.

---

### Post by mkrahmeh on 2008-07-14
thx
it makes sense for the prompt thing, but the $EDITOR is modified as appears by the echo, i went through the man page of the crontab and i learned that unless it finds a variable named EDITOR (which is not declared in my environment), nano will work..
in general it seems that declaring a variable without export is useless..though tutorials have differnet opinions..

---

