---
title: "Screwed my display - - - Help Please"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Fazer4463 on 2009-06-02
Hi all,
I'm fairly new to Linux and the only thing that was wrong was my display was really slow.
I decided I needed the right drivers for it and went searching, I found the ATI Catalyst Control Center and installed that, stupidly I didn't install the right Graphics card drivers first. When I ran CCC for the first time it said "No compatible card installed"

Now when I try to boot into Linux I can see the Ubuntu logo loading but then my display just gets garbled up and I can't log in. I think I need to uninstall the CCC and hopefully it will work.

Only problem is, I can get to the command line ok, but I don't know how to remove it, or worse still, what the app is actually called. :(

Any help is GREATLY appreciated.

THANKS

---

### Post by djuliette on 2009-06-02
This command might help.

sudo dpkg-reconfigure xserver-xorg

Hopefully that will get you back to a basic graphics setting and then you can install your new drivers.

---

### Post by Fazer4463 on 2009-06-02
Thanks for that, I have now managed to get back to the basic settings, so I think i'll leave it there for now....LOL


CHEERS :D

---

