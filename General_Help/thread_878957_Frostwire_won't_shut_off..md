---
title: "Frostwire won't shut off."
date: 2008-08-03
forum: General Help
---

### Post by Roasted on 2008-08-03
omgosh another frostwire won't shut off thread!

I did a search, and every single one was solved by realizing that you must have everything cleared in your que to close frostwire.

okay, great, did that. Frostwire still won't go away.

Even if I "end process" and "kill process" of frostwire, it won't go away.

I just did a ps -A. 10207 is frostwire.

kill 10207.

Frostwire is still here. And it's not frozen... if I open it, I can still use it and look up stuff. It just won't fricken close.

---

### Post by rEbyTer on 2008-08-03
Did you tried with xkill ?

---

### Post by Diabolis on 2008-08-03
This must work;
```
kill -9 10207
```

---

### Post by Roasted on 2008-08-03
what is xkill?

Diabolis - nope. :( It takes it off of the processes running list, yet, frostwire is still at the bottom of my screen. When I maximize it, I can tweak with it accordingly.

I'm heading out for a few minutes, so I'm gonna let this run and see if it magically shut itself off sometime throughout the duration I'm gone.

---

### Post by Diabolis on 2008-08-03
Next time run it from a terminal, to see if it throws an error message or maybe you could see what is doing when is supposed to be closed.

---

### Post by Roasted on 2008-08-03
I did run it from terminal. It gave me no errors.

When I ran ps -A again, it wasn't in the process list. That's how I knew it was off the list when I mentioned it earlier.

---

### Post by HyperHacker on 2008-08-03
> **Roasted said:**
> what is xkill?Read the manual, i.e. 'man xkill':
> NAME
       xkill - kill a client by its X resource

SYNOPSIS
       xkill  [-display  displayname] [-id resource] [-button number] [-frame]
       [-all]

DESCRIPTION
       Xkill is a utility for forcing the X server  to  close  connections  to
       clients.   This  program  is very dangerous, but is useful for aborting
       programs that have displayed undesired windows on a user’s screen.   If
       no  resource identifier is given with -id, xkill will display a special
       cursor as a prompt for the user to select a window to be killed.  If  a
       pointer button is pressed over a non-root window, the server will close
       its connection to the client that created the window.Also, try "sudo kill -9 10207", to run the command as root.

---

### Post by lisati on 2008-08-03
Right-click on the frostwire icon on the panel....there should be a couple of shutdown options.

---

### Post by Roasted on 2008-08-03
> **lisati said:**
> Right-click on the frostwire icon on the panel....there should be a couple of shutdown options.

It disappears from the panel (assuming you mean the upper right corner by the clock). However, it remains at my taskbar.

I'll try the other options in a few minutes. Trying to fix an old eMachines tower at the moment. 

:guitar:

---

### Post by InspiredIndividual on 2008-08-03
I read in some other thread somewhere else that Frostwire automatically shuts down only after all downloads are complete. I don't know where exactly, found it with google when i had the same problem. You should be able to find this option in the preferences of the application or something like that, I believe.

EDIT: This is where I read it originally. The solution mentioned in the last post solved the issue for me: [http://sudan.ubuntuforums.com/showthread.php?t=429614](http://sudan.ubuntuforums.com/showthread.php?t=429614)

---

### Post by Roasted on 2008-08-03
Then explain this:

I just opened Frostwire. I didn't search for anything, download anything, nadda... I simply OPENED it. That's it. Nothing more. Didn't even click on anything.

I hit X. Doesn't close.
I kill the resource. It takes it off of the process list, yet it remains in my bottom taskbar.

How's that work?

---

