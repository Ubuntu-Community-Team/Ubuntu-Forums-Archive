---
title: "Had to force quit computer during Jaunty upgrade, now I can't log in"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Dingbats on 2009-04-24
I just upgraded to Jaunty from Intrepid.  I went away from the computer for a couple of hours (why oh why???), and when I came back, the mouse wouldn't move and only the volume and eject keys on the keyboard worked.  I tried everything I could think of, but in the end I couldn't do anything else than to force quit it.

When I boot Ubuntu, I get to the login prompt and I enter my username and password, but afterwards the screen just goes black.  The mouse pointer is still there and it moves, but nothing happens.  The computer doesn't even sound like it's doing anything.

When I shut down the computer during the upgrade, it had gotten to a dialog prompt asking me if I wanted to replace some php config file with a new version, if that's any indication how far through the upgrade I was.

I suspect it might just be X that's broken or something like that (I hope so), but I don't know how to make sure or how to fix it.

Anyone?  I'm completely lost.

---

### Post by Dingbats on 2009-04-24
Bump.

---

### Post by tchalvakspam on 2009-04-24
Try:
Ctrl-alt-F4 (should bring up the TTY terminals)
lsb_release -r (should tell you whether you're now on 8.10 or 9.04)

sudo upgrade-manager -d (attempts to do the upgrade)

---

### Post by Dingbats on 2009-04-25
> **tchalvakspam said:**
> Try:
Ctrl-alt-F4 (should bring up the TTY terminals)
lsb_release -r (should tell you whether you're now on 8.10 or 9.04)

sudo upgrade-manager -d (attempts to do the upgrade)
"lsb_release -r" said that I was on 9.04.  Then I tried "sudo upgrade-manager -d", which said "sudo: upgrade-manager: command not found".

So I ran "sudo shutdown now", which took me to a prompt asking me if I wanted to try a normal boot, repair broken packages, and other things.  I chose the option "xfix", to try and repair X.  It said something like "xorg-xconfig is not fully installed".

What do I do now?

---

### Post by Dingbats on 2009-04-25
I fixed it :D

I chose "repair broken packages" in the shutdown prompt and it all worked out!

---

