---
title: "Editing the Power Button shortcut key"
date: 2008-07-12
forum: General Help
---

### Post by bharat411 on 2008-07-12
Hi there, I've just recently switched to KDE from Gnome, and I can't seem to find a place where I can assign the shutdown command to the power button. I want to be able to skip the menu asking me for what to do, and directly shut it down. 

So, in summation, I want to just press the power button (the external on/off button), close to laptop lid, and go away while my computer is shutting down.

Any Ideas? I know it's a minor if not nitpicky problem, but I've gotten used to doing this :)

---

### Post by happyhamster on 2008-07-12
- Open a terminal and run:

gconf-editor

- Choose apps-->gnome-power-manager-->buttons and right-click the "power" entry in the right window. Choose "Edit Key" and change "interactive" into "shutdown" (without the quotes).

- Close gconf-editor. Perhaps you'll need to re-login (ctrl-alt-backspace) for any change to show. Good luck.

[edit: crap, I misread your post. You went from gnome to kde, not the other way around. So disregard anything I just wrote.]

---

### Post by bharat411 on 2008-07-12
haha, yeah, well thanks for the help anyway... not a KDE expert then?

anyone else?

---

### Post by happyhamster on 2008-07-12
> **bharat411 said:**
> haha, yeah, well thanks for the help anyway... not a KDE expert then?
No, I'm all Gnome :)

Anyway, I did some digging, and I think I found the solution. I can't test this myself though. Pressing the powerbutton runs a small script: /etc/acpi/powerbtn.sh. All you have to do is make a slight change. First make a backup of the script:

sudo cp /etc/acpi/powerbtn.sh /etc/acpi/powerbtn.sh.bak

- Open the script with a text-editor (as root), and search for these lines:
```

# single KDE session -> ask user
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0
        exit 0
```
- The "logout 1 ..." part means that the user will have to choose what to do, changing that 1 into a 0, will cause immediate shutdown (while still making sure all applications are terminated gracefully). So, it should look like this:

```

# single KDE session -> ask user 
# modified by user, july 2008; default value is "logout 1 2 0"
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0
        exit 0
```
 
- Save and exit. See these links for a bit more info:
[http://andrejserafim.wordpress.com/2008/05/16/kde-shutdown-logout-restart/](http://andrejserafim.wordpress.com/2008/05/16/kde-shutdown-logout-restart/)
[http://ubuntuforums.org/showthread.php?t=36291&highlight=kde+powerbutton](http://ubuntuforums.org/showthread.php?t=36291&highlight=kde+powerbutton)
[http://www.dbe.cc/?page_id=32](http://www.dbe.cc/?page_id=32)


Good luck, and keep us informed.

---

### Post by bharat411 on 2008-07-12
Brilliant, it works like a charm...

Thanks a ton for digging that up, apparently I need to upgrade my googling skills... :)

And thanks for the non-mindless solution and the external links... I'm now going to go to /acpi and fiddle around with other stuff :) The opportunities seems endless...

---

