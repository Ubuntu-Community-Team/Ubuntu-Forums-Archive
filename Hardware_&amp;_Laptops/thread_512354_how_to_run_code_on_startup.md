---
title: "how to run code on startup?"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by gamefreak863 on 2007-07-29
I need my comp to run the code

```
compiz --replace -c emerald &
```

on startup...otherwise my borders don't show up around my windows...and it's really annoying to have to go to terminal everytime I logon...

any help?

---

### Post by kevinlyfellow on 2007-07-29
If your using gnome, go to System -> Preferences -> Sessions and add it as a startup program

---

### Post by gamefreak863 on 2007-07-29
nope, didn't think that would work...I need that code to be run, in terminal...on startup.

sorry for not being as specific.

---

### Post by kevinlyfellow on 2007-07-29
Now, I'm confused.  Why would you need to put it in a terminal specifically?

If you really want, you can put in
```
gnome-terminal --execute "compiz --replace -c emerald &"
``` into the sessions manager, but I don't really see the point in using a terminal to do so (and I'm not sure how well that would work).  A new startup program will let you run any command you want after you login.

After you put in the compiz --replace under the startup, make sure that metacity isn't in the "current session".

---

### Post by gamefreak863 on 2007-07-29
I have no idea...haha..all I know is I have to run that code in terminal everytime I log on to get my borders to show up on my windows.

---

### Post by kevinlyfellow on 2007-07-29
Try this.

In the sessions manager, add a new startup program, with a command of just "emerald --replace" (name it whatever you want of course).

---

