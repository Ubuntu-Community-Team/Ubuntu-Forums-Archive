---
title: "some app settings don't stick"
date: 2008-11-08
forum: General Help
---

### Post by a_toff on 2008-11-08
Hi there, 
I'm pretty new to linux, but have 8.10 up-and-running on my hp tx2617... thanks to some help from some great folks around these parts. 

I'm a program called CellWriter to input text with the wacom stylus. It works very well, except that every time I reboot, CellWriter asks to re-start the handwriting recognition training, as though my settings from the previous session were not saved. 

I have the same problem with the Wacom Control Panel application, which must be run after each start-up in order to re-map the stylus buttons and calibrate the pointer.

Are these items related? How do I fix this?

Thanks kindly,

s.

---

### Post by gali98 on 2008-11-08
I do not know about cellwriter, but for wacomcpl, open the terminal and do:
chmod +x ~/.xinitrc
then go to System->Preferences->Sessions
and add a new one with the command /home/yourusername/.xinitrc
and then restart and you should be good to go...
Kory

---

### Post by a_toff on 2008-11-09
ahh.. I get it... we have to give the .xinitrc file the right permissions to allow it to be written to, correct?

Anyhow... I added a startup item as you suggested, but the result was not quite what I expected. After reboot, I log in as normal, but then the "welcome" sound plays repeatedly and new instances of Notification Area kept loading into the top panel... After removing the startup item I had created with the command "/home/(my username)/.xinitrc", things are now back to normal. weird...

---

### Post by gali98 on 2008-11-10
woops.. I forgot something.. sorry :( You probably need to open up the .xinitrc and remove any lines not starting with 
xsetwacom

Basically the line probably giving you trouble is
. /etc/X11/xinit/xinitrc
delete that or comment it out and you should be good to go..

also are you having a problem with permissions or something?

Kory

---

### Post by a_toff on 2008-11-14
> **gali98 said:**
> woops.. I forgot something.. sorry :( You probably need to open up the .xinitrc and remove any lines not starting with 
xsetwacom

Basically the line probably giving you trouble is
. /etc/X11/xinit/xinitrc



Actually, my .xinitrc (in etc/X11/) is completely empty...

---

### Post by gali98 on 2008-11-14
Its actually /etc/X11/xinit/xinitrc... That is the problem. In it it points to another file.
Basically just comment out those lines I told your, then add it back to the the session and everything should be okay.
Kory

---

### Post by a_toff on 2008-11-15
It would seem that my /etc/X11/xinitrc file is also completely blank...

---

### Post by gali98 on 2008-11-15
No... :)
/etc/X11/xinit/xinitrc

Kory

---

### Post by a_toff on 2008-11-16
Oops! That was just careless reading on my part... anyway, my wacomcpl settings still aren't sticking after restart.
s.

```
#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
# . /etc/X11/Xsession
```

---

### Post by Niva on 2008-11-25
I'm having a problem which this thread is trying to address it seems.

Running on ubuntu 64.  Other threads are hinting at potential driver problems and a possible solution using an expresskeys download.  I'm not convinced this is what I need...

I have the tablet installed, pressure sensitivity works just fine.  The pad also works.  For example the strips scroll up and down just fine.  I've been trying to use wacomcpl to configure the touchstrip to + and - keys so GIMP would allow instant zoom in and out.  All of this works until I reboot and I must run wacomcpl again.

The file /home/username/.xinitrc exists and I can see the +/- definitions there, however this file doesn't seem to be executed on system restart.  It's making me question what exactly wacomcpl does when I run it again, it's like those settings are going elsewhere and in some way telling the system to do what I need it to do but then the system forgets when it reboots.

Any help would be greatly appreciated.

---

### Post by Favux on 2008-11-25
Niva,

It sounds as if you haven't added .xinitrc to Sessions.  The following example is from [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")#5 gali98:

"To make the wacomcpl settings stay after you reboot you need to:
```
chmod +x ~/.xinitrc
```
Then go to System->Preferences->Session
click on add and for the command write "~/.xinitrc" (without the quotes) title it whatever.....

This will only work for the user though. So before you log in it is still uncalibrated."

Hope this helps.

---

### Post by Niva on 2008-11-25
Favux, thanks a lot for the help.  I'm almost there.

I made the file executable and created the session as described.  Here's a screenshot.

[ATTACH]94222[/ATTACH]

Unfortunately after I log on it does not automatically execute.  You can see the edit window in that screenshot so just tell me if something isn't right there.

However, simply running the ~/.xinitrc command from the terminal immediately works as you can see the results from the screenshot.  Those +++--- signs are produced by the touchstrip which was not working prior to running the file.

---

### Post by Favux on 2008-11-26
Niva,
Looks like you've got everything right, your "~/.xinitrc" in the Sessions command box looks just like mine, and that's the only important entry.  And you've checked the check box to make it active.

Probably a pointless detour but does your xinitrc in /etc/X11/xinit look OK.

If a command operates in terminal but not in Sessions what could be the reason?  A permission problem would be my guess.  But you did "chmod +x ~/.xinitrc".

Sorry Niva.  We'll have to wait for someone more knowledgeable to bail us out.

---

### Post by Niva on 2008-11-26
Thanks once again for the quick response, I have some more ideas to track this down when I get home tonight after talking to one of our sys admins here at work today. 

The file is definitely executable now because prior to sending the chmod command like you said I couldn't run it as a script.  After doing the chmod I could do what you see on the screenshot w/o errors.

Once again thanks for the help!

---

### Post by Niva on 2008-11-28
Ok, after some more testing and experimenting I figured out how to make the settings stick.

In the /home/username/.bashrc file I added the lines from the .xinitrc file defining the custom wacom expresskeys.  Upon logon I no longer need to manually execute .xinitrc as a script.

Thanks for the help once again!

---

### Post by Favux on 2008-11-28
Congratulations, an interesting solution, I'll have to keep it in mind.  Glad you worked it out and thanks for letting me know.

---

### Post by Niva on 2008-11-28
Yeah, I'm not sure it's the best solution.  I searched a bit and tried some other methods but settings wouldn't stick.  I remember working this out in opensuse a while back for some other reason but couldn't quite track it back to an elegant solution.  Guess this will work for now.

---

