---
title: "Setting environment variables"
date: 2008-08-28
forum: General Help
---

### Post by Zalbor on 2008-08-28
I need to set some environment variables, and I'm having problems with it...

The way I know of is to enter a line like this in the .bashrc file:
```
export TESTVAR="Yohoho"
```

While that does work in terminal windows, the variables aren't set for programs that aren't launched with one. For example, I wrote this script:
```
#!/bin/bash

zenity --info --text="Variable is $TESTVAR"
```

When I run the script through a terminal, the window that appears does indeed say "Variable is Yohoho". But if I run the script by double-clicking it in Nautilus, it only says "Variable is" which means it's not set. Same after a reboot.

(Of course there are more important reasons why I need to set a variable, the above is only an example).

---

### Post by aloshbennett on 2008-08-28
This is about the mythical .profile file. Legend has it that the file is executed everytime user logs in (and not when the shell is created).

Can you try adding the lines to ~/.profile and reboot?

---

### Post by Zalbor on 2008-08-29
Thanks! I didn't know about that one :)

By the way, logging out and in was enough.

---

