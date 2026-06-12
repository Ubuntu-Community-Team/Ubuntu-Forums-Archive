---
title: "Open windows in different workstation from terminal"
date: 2008-08-12
forum: General Help
---

### Post by sdlynx on 2008-08-12
I would like to know if there is a command in the terminal that I can use to open a program in a specific workspace.  I'm looking to use this because normally I run audacious in desk 2 and I just set it so it will start automatically on boot up (under System -> Preferences -> Sessions) and I would like it to start up on desk 2.  This is not all that important but I like to use desk 1 for instant messaging, so I want audacious on a different one.

---

### Post by sonofusion82 on 2008-08-12
you can try to SSH into desk 2 from desk 1 with X tunneling then launch your application:

ssh -X username@desk2IP command_to_run_audacious

---

### Post by sdlynx on 2008-08-12
Oh sorry no I was talking about workspaces I got the words mixed up.

---

### Post by jtreach on 2009-07-16
Did you ever figure this out because I would love to be able to do this.

---

### Post by franklid on 2009-08-07
I'm also interested in the answer to this problem (as I want to do the same thing). Is there perhaps some type of script file that can be written that can use terminal commands to launch certain applications, place them in a specific workstation, and assign that script to run on startup from System>Preferences>Startup Applictions?

That's one possibility that I've thought of, but, being quite new to Ubuntu/Linux in general (I've had it installed for about a week) I'm not entirely sure how to go about executing this solution, if it even works.

---

### Post by lykwydchykyn on 2009-08-07
Have a look at wmctrl (it's in the repositories, I don't think it's installed by default).  It's a non-DE-specific tool that allows you to script window management activities.  I use it all the time in shortcuts, key bindings, and mouse bindings for more efficient window management.

In your case you could do something like (and don't quote me on the syntax here):
```

audacious && wmctrl -r audacious -t 2

```

Which would open audacious and move it to workspace 2.  

There may be a GNOME command or environment variable to launch stuff directly to a workspace, but if you don't find that wmctrl is great for hacking such capabilities in.

---

