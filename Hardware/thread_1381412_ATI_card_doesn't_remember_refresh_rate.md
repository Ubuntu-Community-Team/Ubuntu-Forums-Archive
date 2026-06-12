---
title: "ATI card doesn't remember refresh rate"
date: 2010-01-14
forum: Hardware
---

### Post by mazz0 on 2010-01-14
I have a Radeon HD 5850 and am running Karmic.

OK, a little background.

The bundled proprietary ATI drivers include two menu items - "ATI Catalyst Control Center", which calls 'amdcccle' and "ATI Catalyst Control Center (Administrative)" which calls 'amdxdg -su -c amdcccle'.  I don't know the point in the first one, as you need root privileges to make changes, but the second one doesn't work because amdxdg-su is not found.

So anyway, you change that to 'gksu amdcccle' so that you can make changes, as discussed [elsewhere on the forum]("http://ubuntuforums.org/showthread.php?p=8666198#post8666198") and in [the bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/461839").

So, I've done that, I've set my resolution, refresh rate, all the other options, and it all looks good.  But then I reboot and the refresh rate has dropped down to 30 and everything looks pants (thick borders around everything and choppy movement) and I have to go in and set it back to 60 every time.

Any ideas?

---

### Post by DirtyNerd on 2010-01-18
Is it just your refresh rate settings or all settings that arent remembered...

because I am having the same problem

---

### Post by mazz0 on 2010-01-21
It seems to be just the refresh rate - I had to change the scaling to 0% to get rid of the black border around the outside of the screen, and it remembers that (the resolution defaulted to the correct value so I don't know if it's remembering that).

I've also upgraded to the latest drivers from AMD to see if it would fix my tearing (it didn't) and the problem still exists.

Do you get tearing as well?

---

### Post by jtheoof on 2010-02-28
Hello did you figure out how to fix this?

I'm having the same problem. I can set up the refresh rate and all, but after rebooting it's back to 30 Hz with, of course, a lot of flickering on the screen and thick black borders on the sides.

Can anyone help me?

---

### Post by mazz0 on 2010-02-28
Nope, I never did resolve this.  I figure we may have to wait for a later version of Catalyst.  Anyway, I figured since I spent all that money on a fancy graphics card it would be a crime not to play games on it, so I'm using Windows at the moment.  I've recently been ordered to use Windows at work too, it's very sad :(

---

### Post by jtheoof on 2010-02-28
Lol same for me :( It's very frustrating since ubuntu is so much more efficient to work. I was so used to my little gnome-do, docky and compiz that it's really hard not to work with it anymore :(

Concerning the refresh rate, I might have found a good way to take care of it, not completely though.

Instead of using ATI Catalyst Control Center (Administrative), I used the System -> Preferences -> Display application. From there I specified 60 hz (my optimal screen refresh rate) and it works. But I still some flickering inside the log on of ubuntu. After logging in, the new resolution kicks in so it's OK.

Let me know if it works for you :)

J

---

