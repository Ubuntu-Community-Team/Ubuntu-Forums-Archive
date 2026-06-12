---
title: "[SOLVED] opening an application in a specific virtual desktop"
date: 2008-11-30
forum: General Help
---

### Post by cb951303 on 2008-11-30
How do I open an application (i.e: gnome-terminal) in a virtual desktop other than I'm currently in?

Thanks

---

### Post by fragos on 2008-11-30
This may not be what you want but you can drag a window between workspaces or scrool wheel on the desktop to select a workspace before opening terminal. The window icon in the left of the title bar also provides a couple of options for moving the active window.

---

### Post by cb951303 on 2008-12-01
> **fragos said:**
> This may not be what you want but you can drag a window between workspaces or scrool wheel on the desktop to select a workspace before opening terminal. The window icon in the left of the title bar also provides a couple of options for moving the active window.

Thanks, I already know that, What I'm trying to achieve is to automatically open a terminal window in workpsace 2 when I login :confused:

---

### Post by fragos on 2008-12-01
Workspaces are a metacity function. Perhaps you can build a keyboard macro that does what you want since there are keyboard commands to change workspace.

---

### Post by chewearn on 2008-12-01
There might be other ways, but here is how I would do it:

1. Create an entry in System > Preferences > Sessions
For the command, enter:
gnome-terminal --title=workspace2

This will automatically open a terminal upon login.

2. Add an entry in Compiz "Place Windows" plugin
Under: Fixed Window Placement > Windows with fixed viewport
Choose detection of "title=workspace2"

This will force that particular terminal to open in your specified workspace.

---

### Post by cb951303 on 2008-12-01
> **chewearn said:**
> There might be other ways, but here is how I would do it:

1. Create an entry in System > Preferences > Sessions
For the command, enter:
gnome-terminal --title=workspace2

This will automatically open a terminal upon login.

2. Add an entry in Compiz "Place Windows" plugin
Under: Fixed Window Placement > Windows with fixed viewport
Choose detection of "title=workspace2"

This will force that particular terminal to open in your specified workspace.

that's great but unfortunately I don't use compiz :(

> **fragos said:**
> Workspaces are a metacity function. Perhaps you can build a keyboard macro that does what you want since there are keyboard commands to change workspace.
I don't think keyboard macros can be run automatically :confused:

I'll tag this as solved, cause there is one other thread about the same issue and people are pretty sure that there is no way of doing this

Thanks all for your time :popcorn:

---

### Post by chewearn on 2008-12-01
> **cb951303 said:**
> I'll tag this as solved, cause there is one other thread about the same issue and people are pretty sure that there is no way of doing this

Thanks all for your time :popcorn:

Ah, but that's not quite true. :)

Before compiz, when metacity ruled, there was [Devilspie]("https://help.ubuntu.com/community/Devilspie").  It didn't have the convenience of a GUI, but it got the job done.

---

### Post by DAE51D on 2009-03-31
I had this same issue, and here's the "hacky" work around I did...
```

#!/bin/sh

wmctrl -s 0
gnome-terminal --title="workspace 1"

wmctrl -s 1
gnome-terminal --title="workspace 2"

```
you get the idea. but yeah, it's absolutely lame that gnome-terminal has all these command line options but you can't specify a workspace.

[http://tripie.sweb.cz/utils/wmctrl/](http://tripie.sweb.cz/utils/wmctrl/)

---

