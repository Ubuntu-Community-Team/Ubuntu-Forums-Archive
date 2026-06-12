---
title: "[SOLVED] Scripts not showing Terminal windows"
date: 2008-10-03
forum: General Help
---

### Post by weasello on 2008-10-03
Hey everyone,

I'm making my first "batch files" in Ubuntu/Gnome (hardy). After some searching I got a lot of great tips - I've created the launcher, I'm calling

```
gksudo sh myscript
```

(Which apparantly calls a script with sudo so that I don't have to use sudo before each command in the script)...

But the script calls a bunch of command line options which doesn't seem to echo anything to screen (even if I put "ECHO" before them in the code), and one of the last apps I run in the script is a persistant app that has streaming output. 

But no window is created!

I have no idea how to tell if it's even running in the background somewhere, or if it didn't run at all, or what!

Where am I going wrong?

My script is something like:

```
#!/bin/bash/
echo copy this
echo copy that
echo streaming_output_app
pause
```

but double clicking on the launcher just gives me the briefest flash of an hourglass icon before disappearing to the ether.

---

### Post by Agent ME on 2008-10-04
My guess is that you need to change
#!/bin/bash/
to
#!/bin/bash

---

### Post by weasello on 2008-10-04
Woops, my bad. It is indeed without the trailing slash.

---

### Post by cariboo on 2008-10-04
If you run your script in a terminal you will see the output. Also remove the trailing / from #!/bin/bash/

Jim

---

### Post by weasello on 2008-10-04
How do I launch the terminal window from a desktop shortcut? I'm trying to avoid having to open terminal and typing anything to get this started. Just a double click.

---

### Post by Sorivenul on 2008-10-04
> **weasello said:**
> How do I launch the terminal window from a desktop shortcut? I'm trying to avoid having to open terminal and typing anything to get this started. Just a double click.

Are you running the GNOME desktop?  If so, right-click a panel you would be comfortable creating a launcher button on. select "Add to Panel", select "Custom Application Launcher", select "Application in Terminal". input the path to your script, and click OK.  Should do the trick.

---

### Post by weasello on 2008-10-04
Perfect! thanks so much.

---

