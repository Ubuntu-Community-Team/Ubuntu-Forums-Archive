---
title: "A script to toggle your KDE Desktop Icons..."
date: 2008-10-05
forum: General Help
---

### Post by zansatsu0 on 2008-10-05
This post is intended to serve as a place to give this script to the community, your comments are always welcome. My method is included for the curious. 

_**The short:**_

This command will allow you to toggle your Desktop icons in KDE. Create  New > Link to Application on your Desktop and copy and paste the line below in the command field.

**NOTE:** You may want to drag the icon to your task bar and use it from there. ;)

```
dcop kdesktop KDesktopIface setIconsEnabled "$(dcop kdesktop KDesktopIface isIconsEnabled | grep -c "false")"
```


**_The long:_**

I wanted the ability to toggle my Desktop icons in KDE at will, without having to right click > Configure Desktop > Behavior > Show icons on Desktop. I first did a little research into the 'dcop' and 'kdcop' commands and was able to come up with this basic script.

```
#!/bin/bash
# First iteration. Pedantic fun.

# If 'isIconsEnabled' is true, disable. Else enable.
if [ "$(dcop kdesktop KDesktopIface isIconsEnabled)" ]; then
dcop kdesktop KDesktopIface setIconsEnabled false
else
dcop kdesktop KDesktopIface setIconsEnabled true
fi
```

But being a Slackware user too, I wasn't satisfied. I had created an application link to the Bash script, but why have a command that calls multiple lines of commands, when you can have a single line that does it all?

I hit a brick wall when I exhausted research into an 'in-line' method for 'flipping' or 'NOTing (!)' a bool value in Bash. If anyone knows the proper Bash syntax to make the below failure work, please let me know.

```
# Bash needs in-line evaluation or I needs sum learnin.
dcop kdesktop KDesktopIface setIconsEnabled "$(test ! $(dcop kdesktop KDesktopIface isIconsEnabled))"
```

Finally, after a eureka moment, I took the 'grep' command out of context and used it to flip the 'isIconsEnabled' status to the opposing binary. When true, it returns 0. When false, it returns 1. In this case, all 'grep' is doing is counting (-c) the number of occurences in the pipe (|) of the string "false". When it is "true", it cannot count "false" and therefore returns 0. It's a trick, but it worked. When fed into the toggle command the 0 and the 1 are adequate for the icons to change state accordingly.

Toggle me this, Bash!
```
dcop kdesktop KDesktopIface setIconsEnabled "$(dcop kdesktop KDesktopIface isIconsEnabled | grep -c "false")"
```

Now I have a single command line (albeit a hack of sorts) that I can copy and paste into a Desktop Link to Application. It was a fun little script to write, so I thought I would share. Enjoy!


**EDIT:** > # Bash needs in-line evaluation or I needs sum learnin.

I got some learn on and found an alternative... I personally like 'grep' doing the magic because it seems more elegant. There is always 'awk'. 
```
dcop kdesktop KDesktopIface setIconsEnabled "$(dcop kdesktop KDesktopIface isIconsEnabled | awk '{$1=($1=="false")?"1":"0";print}')"
```

It's a little obscure for my taste... you can always type it all out.
```
dcop kdesktop KDesktopIface setIconsEnabled "$(dcop kdesktop KDesktopIface isIconsEnabled | awk '$1=="false" {print "1"} $1=="true" {print "0"}')"
```

Awk is geared for the explicit. You know 100% what you are looking at, if you understand the syntax that is. Grep is implied and just works. Meh. Use whatever works best for you. :)


**To the Moderators, if I have posted in the wrong section I apologize. I figured this would fall under customization.**

---

### Post by Denestria on 2008-10-07
This will help me out with Conky since it doesn't work properly in KDE with the background if desktop icons are turned on.  Got to make myself a little script to run on login.

---

### Post by zansatsu0 on 2008-10-07
> **Denestria said:**
> This will help me out with Conky since it doesn't work properly in KDE with the background if desktop icons are turned on.  Got to make myself a little script to run on login.

I'm glad I could help. Happy monitoring. :D

---

