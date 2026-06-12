---
title: "AWN Launcher Troubles"
date: 2008-08-05
forum: General Help
---

### Post by SlalomMan on 2008-08-05
I have AWN and I would like to put in a "launcher" that runs "vncviewer xxx.xxx.x.xxx:xxxx" which connects me to my desktop computer. I got this part, but whenever I click the icon, it acts as if a program opens. The VNC program opens in a separate icon, and even if I close the viewer, the launcher I made still has a task arrow under it, so I can't press it again without restarting AWN. Any ideas?

---

### Post by DagMan on 2008-08-06
you can have the lancher run a helper script, instead of the command, and have the helper script run the command. 
So for example.
```
sudo nano /usr/local/bin/helper-script
```
then making the file just the command to open the vnc session, and disown it from the script so that it runs on its own and the script exits by putting & disown at the end of the command.
```
#!/bin/bash

vnc command & disown
```

make it executable
```
sudo chmod +x /usr/local/bin/helper-script
```

and then have the launcher call /usr/local/bin/helper-script

Hopefully this will unbind it from the launcher icon and force it over to the right, as if it didn't have a launcher icon, and maybe that will solve the problem if it works like that.  It's worth considering  that your vncviewer isn't exiting properly also, and you can take a look by doing this when the described problem happens
```
ps -e |grep vnc
``` 
and if it outputs the name of the program then indeed it is still running, and that would then be the problem to investigate first instead.

---

### Post by SlalomMan on 2008-08-06
Thanks for the help; I don't think it worked; I'll just add a launcher for the VNC Viewer and then I can just quick connect to the pc.

---

### Post by moonbeam on 2008-08-06
> **SlalomMan said:**
> Thanks for the help; I don't think it worked; I'll just add a launcher for the VNC Viewer and then I can just quick connect to the pc.

It's a known problem when the following occurs.

launcher -> script -> binary

Awn launches the script but the PID of the binary doesn't match the PID of what was lauched...  so it doesn't always identify the new task as associated with the launcher.

We'll be dealing with this situation as cleanly as possible in the  0.4 - 0.6 timeframe.  There is an experimental applet called standalone-launcher available that can deal with this but it really isn't for the faint of heart at this time:-)

---

### Post by SlalomMan on 2008-08-06
Alright; I don't mind if avant opens up a new icon for the VNC, just that it won't let me re-launch VNC after I close it; just give me a shout when the standalone-launcher gets better or less buggy.

I have the bzr version of AWN installed; how buggy is the applet?

---

### Post by moonbeam on 2008-08-06
> **SlalomMan said:**
> Alright; I don't mind if avant opens up a new icon for the VNC, just that it won't let me re-launch VNC after I close it; just give me a shout when the standalone-launcher gets better or less buggy.

I have the bzr version of AWN installed; how buggy is the applet?

Try using a middle click instead of a left click to launch it after you've closed it.  (though it definitely sounds like a bug from the description).

Standalone-launcher isn't _extremely_ buggy as such though it does need some additional work for Vala 0.3.x.  It's more a case of it being finicky and somewhat idiosyncratic to configure.  It's really a testbed/POC where I've tested various ideas/approaches, many of which will probably end up in the standard launcher and taskmanager when we rewrite that.  If you're interested my best suggestion is to read (all) this thread:  [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1495](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1495)   Honestly, most people probably find the core peculiarities don't bother them enough to read 4 or 5 pages from the forum... a perspective I can understand :-)

---

### Post by SlalomMan on 2008-08-07
I'm using a laptop, so no middle click for me; I'm going to read some of the link you gave me; hopefully you can get it working!

---

