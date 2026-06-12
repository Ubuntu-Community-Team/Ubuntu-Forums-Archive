---
title: "Shutting down shouldn't take ten minutes."
date: 2008-08-27
forum: General Help
---

### Post by SZF2001 on 2008-08-27
I've recently upgraded to the latest (Hardy or whatev) on my laptop and it was shutting down fine before but now when I messed with Hibernate options in System -> Preferences -> Power Management and turned off Sleep completely, well Hibernate works alright but if I ever want to completely shut down the laptop, first my two bars and whatever was on the desktop goes away; but then it will just show the wallpaper and won't shut down for a good ten minutes.

I dunno what to do about that. :(

I also realize there are threads about people trying to shut down and don't get the gnome shutdown options when they go to System -> Quit for like five minutes. No, that pops up just fine, it's the actual shutting down that takes forever and I don't even get any command text/prompt telling me the process.

---

### Post by SZF2001 on 2008-08-28
Update and bump.

So apparently it's just not logging me out for some reason. I have to press CTRL+ALT+BACKSPACE then the real shutdown sequence begins. Still mind boggling. I'd prefer to not have to do that...

---

### Post by Crafty Kisses on 2008-08-28
Have you checked your error logs?

---

### Post by unutbu on 2008-08-28
Perhaps try this:

Try to shutdown.
When it hangs, press Ctrl-Alt-F2.
Log in.
Type ```

pstree
```
The output will include something like this:
```

     |-gdm---gdm-+-Xorg
     |           `-gnome-session-+-devilspie
     |                           |-fvwm-+-FvwmAuto
     |                           |      |-emacs-snapshot----bash---pstree
     |                           |      `-firefox---run-mozilla.sh---firefox-bin---8*[{firefox-bin}]
     |                           |-gnome-panel
     |                           |-nautilus
     |                           |-seahorse-agent
     |                           |-ssh-agent
     |                           |-update-notifier
     |                           `-{gnome-session}
```
You should have fewer processes listed because most of them should have quit when you pressed the shutdown button.

It sounds like one of the processes under gdm is refusing to quit. To test this hypothesis, type
```

pstree -p
```

to find the process ID number (PID), and then type
```

kill -9 PID
```

(substituting the real PID number for "PID").

If this causes the shutdown process to continue, then at least you'll know what process is holding everything up. 

If you can find out what process is causing the problem, post that info and then perhaps we can think about how to fix it.

---

