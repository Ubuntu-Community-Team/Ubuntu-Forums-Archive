---
title: "Fork function not working when programming in c"
date: 2008-11-04
forum: General Help
---

### Post by scottyadam on 2008-11-04
Alright, so I started a lab at school the other day (dealing with the fork() function) only to realize that it had not been installed on my machine.  I took a few searches in google (who wouldn't) and then took a general search on the Ubuntu Help/Forums but I didn't see anything that could directly help me.  Maybe I wasn't using the 'correct' keywords.  I am trying to download the rest of the developer tools for ubuntu which I guess didn't get installed when I first installed ubuntu.  YES....I have run all the updates for ubuntu.  Is there some sort of link that is out there that would include the tool for fork() to get to download this to ubuntu?

Thanks!

Adam Scott

---

### Post by ju2wheels on 2008-11-04
I believe the standard C headers should include fork.

[http://linux.about.com/od/commands/l/blcmdl2_fork.htm](http://linux.about.com/od/commands/l/blcmdl2_fork.htm)

The following should do it:

```

sudo apt-get install build-essential gcc g++ libstdc++6

```

---

### Post by iponeverything on 2008-11-04
sounds like you need to:

sudo apt-get install build-essential

---

### Post by ju2wheels on 2008-11-04
Also you will find the following useful:

```

sudo apt-get install manpages-dev

```

This will allow you to use man to pull up documentation with explanation about common system calls as follows:

```

man fork

```

---

### Post by scottyadam on 2008-11-04
Thanks everyone!

Finally got fork to work with the installing what you said and installing the man pages...exactly what I wanted!

Adam

---

