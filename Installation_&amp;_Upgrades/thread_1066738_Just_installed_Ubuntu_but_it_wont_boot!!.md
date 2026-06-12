---
title: "Just installed Ubuntu but it wont boot!!"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by BarryO on 2009-02-11
I have just installed Ubuntu via a download. No problems but when I boot it just hangs. NOT impressed so far. Running XP Home on Dell Dimension 2400 with 1Gb RAM. HELP please.

---

### Post by revoohc on 2009-02-12
I'm having an issues with 8.10, in that it hangs on booting unless I hold a key down on the keyboard.  Really weird, I know, but if I don't, it won't boot.  I usually hold down the ctrl key since that is easy to reach and normally safe.

Try that.

---

### Post by whobunstu on 2009-02-12
I had the same issue at first.

Does it hang after the login? If so, try the following commands:

You can access the command line by hitting "ctrl-alt-F1" before you login. Then "sudo apt-get remove compiz" and "sudo apt-get remove compiz-core". This will take care of the problem.

Hope this helps.

---

