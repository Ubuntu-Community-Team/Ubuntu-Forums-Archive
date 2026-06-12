---
title: "no sound after standby - how to get it back?"
date: 2008-10-31
forum: General Help
---

### Post by Bazon on 2008-10-31
hello!

after standby, my intrepid (on fujitsu siemens amilio m6453) looses it's sound. how can i get it back?
i tried killing the pulseaudio proces and restarting it (terminal: pulseaudio &), but that didn't help and only led to a high cpu usage by pulseaudio.

so what can i do to get my sound back after standby?

---

### Post by rudy.elgato on 2008-10-31
I lose sound after resuming from a Suspend.  I can get sound back by opening up a terminal and running:

sudo /sbin/alsa force-reload

I actually wrote a simple script that runs the 'alsa force-reload' and then plays a simple wav file afterwards, then placed an icon on my desktop.  Makes it real simple and quick to get back sound after a suspend, even my wife or daughter can restore sound now...

Hope this helps...

---

### Post by Bazon on 2008-10-31
Indeed, that helps, thanks! :-)

I added a starter with that command to my gnome panel and set it to run in a terminal. That works, but has 3 disadvantages:

1, I have to enter my password.
2. I have to confirm an alert considering restart of gnome volume panel control.
3. I have to hit this starter manually.

Is there a nice solution which even avoids some of this disadvantages?

---

### Post by rudy.elgato on 2008-10-31
To get around entering a password I added an entry into /etc/sudoers using visudo.  Not sure of the exact syntax I used (I'm at work and my Ubuntu system is at home), but a 'man visudo' should show you what need to do to bypass the password on a single command.

For the volume control, well, the volume control on my logitech multimedia keyboard still works great, so I don't miss not having the volume control on the panel.  If for some reason I do need it, it's easy enough to add back for the short time I might need it.

That's true about the third thing you list.  Pretty sure it's possible to add the script somewhere within your /etc/init.d or someplace that's run during a resume from suspend (take a look at [http://ubuntuforums.org/showthread.php?t=664515](http://ubuntuforums.org/showthread.php?t=664515) or [http://ge.ubuntuforums.com/showthread.php?t=891684](http://ge.ubuntuforums.com/showthread.php?t=891684)), but for me, having icon on the desktop works fine.  There are lots of times when I don't miss not having any sound.

Good luck...

---

### Post by rudy.elgato on 2008-10-31
And just a quick note, and you probably already know this but, be very, VERY cautious with 'visudo' and your /etc/sudoers file.  It's not unheard of some people getting it all tangled up so that 'sudo' stops working for them entirely and then they have to jump through hoops to correct it.  So, just be careful...

---

