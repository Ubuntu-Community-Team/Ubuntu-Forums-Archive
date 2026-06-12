---
title: "Lock Mouse/Keyboard - But not screen"
date: 2008-11-26
forum: General Help
---

### Post by Izkata on 2008-11-26
I know this program exists, as I used to use it.  I thought it was xlock, but all searches for that result in a different program.

The one I have in mind, when ran, turned the mouse pointer into a blue lock, and mouse clicks and keyboard input were blocked until the user's password was entered.  The screen never blanked.

I can no longer seem to find it.  Anyone have any ideas?

---

### Post by Izkata on 2008-11-26
Found it.  The name of the program is 'xtrlock' in case anyone else wants to use it.

---

### Post by eraevous on 2010-01-24
Thanks, I was looking for exactly that program. Does anyone know how I could go about running that using a keyboard shortcut? I thought I knew, but I keep failing.

---

### Post by williamts99 on 2011-02-14
> **eraevous said:**
> Thanks, I was looking for exactly that program. Does anyone know how I could go about running that using a keyboard shortcut? I thought I knew, but I keep failing.

I just started using xtrlock(universe repositories) as my transparent screensaver so the kids could watch movies and shows without being able to change anything.  For some reason it couldn't be called directly, so I created a script called lockwithaview that calls xtrlock.

Install xtrlock if you haven't already(must have the universe repos enabled):
```
sudo apt-get install xtrlock
```

Lets create a new file in /usr/local/bin called lockwithaview and open it with gedit:
```

sudo gedit /usr/local/bin/lockwithaview
```

It should contain the following(cut and paste):
```
#!/bin/bash
sleep 1 && xtrlock
```

Save the file and close gedit.

Make it executable:
```
sudo chmod a+x /usr/local/bin/lockwithaview
```

Create a keyboard shortcut to execute lockwithaview(I used ctrl+alt+k) and you are finished.

Now if someone would fix the bug where you can change TTYs, let you customize the blue lock icon, and make it an option for gnome-screensaver it would be just about perfect.

---

### Post by pirka46 on 2011-05-02
[QUOTE=]Create a keyboard shortcut to execute lockwithaview(I used ctrl+alt+k) and you are finished.
[/QUOTE]


How do you do that?... i've tried to bind xtrlock using " gconf-editor " -apps - metacity and   editing " global_keybindings " and " keybinding_commands ".

No luck...

---

### Post by stinkeye on 2011-05-02
Open Keyboard Shortcuts and use this in  the command box.
```
bash -c "sleep 1 && xtrlock"
```

It seems to register the upstroke and stop xtrlock from starting without the sleep command.

---

### Post by fwendt on 2011-07-16
> **williamts99 said:**
> 
Now if someone would fix the bug where you can change TTYs...


This you can fix using the xorg.conf. Lookup the ```
"DontVTSwitch" "true"
``` option and you'll have this one nailed down. :)

---

### Post by williamts99 on 2011-11-07
> **fwendt said:**
> This you can fix using the xorg.conf. Lookup the ```
"DontVTSwitch" "true"
``` option and you'll have this one nailed down. :)

Thanks!  I will have to try that.

---

