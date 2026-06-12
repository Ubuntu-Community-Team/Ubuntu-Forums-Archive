---
title: "[SOLVED] What should be done when Ubuntu crashed?"
date: 2008-07-30
forum: General Help
---

### Post by Pidgin on 2008-07-30
The crash of Ubuntu just now set me into confusion. On Windows, the unresponsiveness of system can probably be resolved by pressing Ctrl + Alt + Del and terminating the problematic application. But on Ubuntu, what can be done when the system does not respond to avoid cold reset?
And after cold reset, unlike Windows, the scan of disk is not performed. Does Ubuntu realized that the computer has been previously improperly shutdown? Or is it unnecessary for Linux to scan the disk as it is better than Windows?
Thanks!

---

### Post by iaculallad on 2008-07-30
For Ubuntu's unresponsiveness issue, try pressing Ctrl+Alt+Backspace key combo.
For windoze scandisk-like utility, try reading this [thread]("http://ubuntuforums.org/showthread.php?t=874614") (w/c as of this time, the discussion is on-going).

---

### Post by kesman on 2008-07-30
There's a bunch of stuff I usually do when Ubuntu(or just Xorg) crashes. First I try to access the command line with ctrl+alt+F2 or whatever F-key different than F7 since that's the one you just crashed. If I manage to access it, I usually see command
```

top

```
to see if any process takes 100% of CPU, and then kill it. Otherwise, I run command
```

sudo /etc/init.d/gdm restart

```
to restart Xorg and go back to login screen.

If I fail to access the command line, I try ctrl+alt+backspace, and as this usually fails too, I open up my second PC and try to access my ubuntu box via ssh. From there, I can restart my xorg with the command above. If this fails, then there's not much to do but a hard-reset. Sometimes I just push the powerbutton once and ubuntu starts the normal shutdown-process.

---

### Post by caljohnsmith on 2008-07-30
Keep in mind that Ctrl-Alt-Backspace is not the same as Ctrl-Alt-Delete in Windows, because Ctrl-Alt-Backspace logs you out of X windows (and kills all your open apps) and puts you back at the login screen. 

As kesman said, probably the equivalent of Ctrl-Alt-Delete is Ctrl-Alt-F2 (or F3-F6 work too), which gives you a console login. Note your X windows session hasn't been killed, so all your apps are still running. Then you can do something like kesman said like "top" to find the offending process and kill it. If that works, once you are done in the console, type "exit" to get back to the console login screen, and then hit Ctrl-Alt-F7 to get back to your normal X windows session (assuming you have only one X windows session running, otherwise use F8-F12 for other sessions).

And if all else fails, the last thing to try before a hard reset would be to do the "[COLOR="Blue"]R[/COLOR]aising [COLOR="Blue"]S[/COLOR]kinny [COLOR="Blue"]E[/COLOR]lephants [COLOR="Blue"]I[/COLOR]s [COLOR="Blue"]U[/COLOR]tterly [COLOR="Blue"]B[/COLOR]oring" routine:
left Alt+SysRq+[COLOR="Blue"]r[/COLOR]
left Alt+SysRq+[COLOR="Blue"]s[/COLOR]
left Alt+SysRq+[COLOR="Blue"]e[/COLOR]
left Alt+SysRq+[COLOR="Blue"]i[/COLOR]
left Alt+SysRq+[COLOR="Blue"]u[/COLOR]
left Alt+SysRq+[COLOR="Blue"]b[/COLOR]
In other words, hold the left Alt botton and the "Sys Rq" button at the same time (Sys Rq is same as "PrtScrn" button up above delete), and then type all those letters in order, pausing a bit between them. That will attempt to shutdown Ubuntu as well as it can and reboot without a simple hard reset/shutdown.

---

### Post by lanzailan on 2008-08-03
is there any solution to prevent it from crash..
:confused:

---

### Post by kesman on 2008-08-04
> **lanzailan said:**
> is there any solution to prevent it from crash..
:confused:

Find out what's crashing, and fix it. When does your Ubuntu crash?

---

