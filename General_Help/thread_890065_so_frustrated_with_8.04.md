---
title: "so frustrated with 8.04"
date: 2008-08-14
forum: General Help
---

### Post by JettRink on 2008-08-14
I am so frustrated and disgusted with 8.04 I could scream...

here is my story:

I had 6.06 installed on a new dev server I was building. Clicked on the'upgrade to 8.04' button. After the install finished (with no errors), system would NOT boot into the graphical environment. Posted to the forums. No solutions worked.

reinstalled 8.04 fresh, wiping out existing HD.
It took tons of time to get everything working (terminal window was white, windows didn't work right, etc), including a new nvdia video card. everything was working great.

performed the regular updates per synaptic package manager. 
now my system is totally screwed up as follows:

1) termimal window is white again
2) I can't 'unlock' any admin functions that require root/sudo, get a 'could not authenticate' error message.
3) the borders on all of the windows are gone, can't double click to minimize, etc. switching themes doesn't fix
4) can't change monitor resolution, get a 'can't write backup' error'

system is reasonably powerful: AMD athlon 1100 mhz with 1G mem, nvidia fx5200.

I don't know what I did that would cause all these problems
I have now spent/wasted about 30 hrs to get to this point... 

This is 'supposed' to be easier and more reliable than windoz

I am close to reinstalling 6.06 which has been a breeze to use.

---

### Post by os.getlogin on 2008-08-14
> **JettRink said:**
> including a new nvdia video card. everything was working great.

1) termimal window is white again
3) the borders on all of the windows are gone, can't double click to minimize, etc. switching themes doesn't fix



I had exactly this, and just fixed it here:
[http://ubuntuforums.org/showthread.php?t=889881]("http://ubuntuforums.org/showthread.php?t=889881")

I have no idea what it was, but I too was using the admin gui right before it happened.  I added the fix:
```
Option "AddARGBGLXVisuals" "True"
```
to xorg.conf, restarted X (ctl-alt-backspace) and it worked.

Good luck!

---

### Post by colobix on 2008-08-14
The reason is Compiz.
You have to disable some compiz plugins.

gksudo nautilus will enable root access to your directories and files.
Security reasons.

---

### Post by JettRink on 2008-08-14
I added Option "AddARGBGLXVisuals" "True" to the X11.conf file. that fixed the white terminal window, but I still can't unlock functions requiring root, the windows aren't 'decorated' and the (I forgot to mention) the synaptic package manager is missing from the admin menu. when I go into menus and check it, it unchecks itself ?

Are these problems caused by the nvidia card/driver ? or is it something else as well ?

---

### Post by JettRink on 2008-08-17
> **colobix said:**
> The reason is Compiz.
You have to disable some compiz plugins.

gksudo nautilus will enable root access to your directories and files.
Security reasons.
what compiz plugins do I need to disable ?

---

### Post by os.getlogin on 2008-08-19
> **JettRink said:**
> I added Option "AddARGBGLXVisuals" "True" to the X11.conf file. that fixed the white terminal window, but I still can't unlock functions requiring root, the windows aren't 'decorated' and the (I forgot to mention) the synaptic package manager is missing from the admin menu. when I go into menus and check it, it unchecks itself ?

Are these problems caused by the nvidia card/driver ? or is it something else as well ?

I had the admin problems also and needed to do a full reboot.  I wonder if something else had a lock on root functionality.  I'm not sure.  But after I rebooted I was indeed able to.

good luck.  frustrating, I know.

Nate

---

