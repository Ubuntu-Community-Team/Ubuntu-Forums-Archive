---
title: "[SOLVED] Firefox won't reopen...it says it's already open, but it's not"
date: 2008-09-09
forum: General Help
---

### Post by fiddler616 on 2008-09-09
Hey,
So everytime I close Firefox, do whatever in my session, and then try to open Firefox again, I get an error about how only one instance of Firefox can be running, and would I please close it in order to let the new one open.
The thing is--Firefox is closed. I hit the big ol' X in the corner, and it disappeared from view.
So then I'll hit the power button=>logout.
Nothing happens.
I wait a while.
Nothing happens.
Ctrl-Alt-Backspace
Nothing.
Wait.
Nothing.
Hard boot.
Reboot.
Log back in.
Open Firefox
Browser Internet.
...I feel like there's gotta be a better way...
Thanks in advance.

---

### Post by EvilRobotDrew on 2008-09-09
I am not an Ubuntu veteran, but i have encountered this problem occasionally myself, normally when firefox crashes on me. To fix it, open terminal and type:

killall firefox

then you should be good to open the browser again.

---

### Post by fiddler616 on 2008-09-09
Thanks.
(That's a *much* better workaround!)
Update: I guess the bug doesn't happen always, just sometimes. Weird...
-------
I'm marking this as solved, but I'm still wondering how to *fix* the problem, not work around it...

---

### Post by Red-Shield on 2008-09-09
in the command prompt you should first try to completly remove firefox and then reboot and reinstall you can use lynx to do this if you don have it installed you can **_apt-get install lynx_** see if that helps i bet is just a bad instalation it happens

---

### Post by fiddler616 on 2008-09-10
I did sudo aptitude install lynx last week, it was succesful, and installed a package. I checked Synaptic and it said I had it....but Lynx is in no menu :(
Will reinstall this weekend.

---

