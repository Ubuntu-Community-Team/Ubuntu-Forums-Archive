---
title: "[SOLVED] Shortcut a command"
date: 2008-08-08
forum: General Help
---

### Post by nikio on 2008-08-08
I have a program (amule) that accasionally occupies all the memory, almost freezing up all the system, when this happens finding the process ID and then sending a kill request takes really a long time. I found out that the command
kill -9 $(ps -C amule -o pid=)
should do the work without having to find out the PID before.
Anyway, when the computer is freezed, opening a terminal takes several minutes, so

my question is:
is there a way to execute this command just pressing (let's say) the "F12" key, even if the terminal window is not open?

---

### Post by llama320 on 2008-08-08
> **nikio said:**
> 
my question is:
is there a way to execute this command just pressing (let's say) the "F12" key, even if the terminal window is not open?

Yup! here's how you do it (on ubuntu, not sure about kubuntu)
1) alt+F2 to open up a run prompt
2) type gconf-editor
3) go into apps > metacity > global_keybindings
4) select one of the run_command_# and type your desired key stroke..so you can just type "F12" to set the command to F12.
5) now go back one level and go to keybinding_commands
6) find the command_# from step 4 and type kill -9 $(ps -C amule -o pid=) or whatever you want the command to be

That should be it
Good Luck

---

### Post by brujoand on 2008-08-08
Also..
a nice key binding would be to bind f.x F11 to "xkill" which will just let you "point and press" to kill whatever process is freezing.

Global keybindings are great :)

---

### Post by nikio on 2008-08-08
> **llama320 said:**
> 

That should be it
Good Luck

I'm afraid I've had bad luck:
something doesn't work, the command is fine (it works from a terminal and from the "Run Application" window), but the "F12" remains responseless, on the step 4) I've tried to change it to F8 and to <Alt>F12 , but didn't help...
any suggestions?

---

### Post by eentonig on 2008-08-08
try the xkill approach. Assigning xkill to a keybinding.

---

### Post by nikio on 2008-08-08
Now I'm really confused!
xkill works perfectly (with F11), although if amule is minimized xkill won't work on the panel's tab, because it kills the panel instead of the program.

maybe keybinding doesn't support the command expansion "$(...)"?

I don't know if alias would help, could someone tell me how to set an alias??

EDIT:
maybe the idea of the alias was nonsense:
I've tried to put the alias "killamule" in the ~/.bashrc file, it works from the terminal but not for the keybinding, that returns the message:
There was an error running "killamule":
Failed to execute child process "killamule" (No such file or directory).

---

### Post by x1a4 on 2008-08-08
Hi,
Create a script and bind the script to a key.
For example, create the file ~/bin/killamule with the following contents:
```

#!/bin/bash
kill -9 $(ps -C amule -o pid=)

```
set the execute bit on it
```
chmod +x ~/bin/killamule
```
then bind ~/bin/killamule to a key.

---

### Post by nikio on 2008-08-08
YESSSSS!!!
binding the script works perfectly, I thank you all for help, I find myself hoping that my amule will freeze again soon!

Am I abusing your patience asking why should the command work through a script but not directly? :biggrin:

---

### Post by x1a4 on 2008-08-09
Commands mapped to a key aren't being processed (that's by design).  There is no command processor like a shell to parse the command, as a result your system didn't know what to do with $(ps -C amule -o pid=).  When you run it from as script, the specified shell (in this case bash) processes the command.

EDIT: Be sure to mark the thread as solved and remember to click the 'thank you' icon ;)

---

