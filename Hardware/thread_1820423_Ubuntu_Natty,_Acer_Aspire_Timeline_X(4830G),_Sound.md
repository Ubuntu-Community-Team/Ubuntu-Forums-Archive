---
title: "Ubuntu Natty, Acer Aspire Timeline X(4830G), Sound EAPD Permanant Solution??"
date: 2011-08-07
forum: Hardware
---

### Post by ahref on 2011-08-07
Hello running: Ubuntu Natty on a  Acer Aspire Timeline X(4830G)

Following this thread:
[http://ubuntuforums.org/showthread.php?t=1820080](http://ubuntuforums.org/showthread.php?t=1820080)

and more specifically this post:

[http://ubuntuforums.org/showpost.php?p=11128442&postcount=13](http://ubuntuforums.org/showpost.php?p=11128442&postcount=13)

I have manged to get sound working on this laptop, However it requires me to run HDA Analyzer ever boot to return on EAPD on Node 0x1B

I was wondering if there was a more permanant solution availible such as a script or a command that i could run on start up to enable this, or perhaps a configuration change.

I almost have this laptop running natty nicely and this is the one remaining thing thats still bugging me, any help would be greatly apreciated :D, thanks

---

### Post by scheibenlosen on 2011-08-07
> **ahref said:**
> Hello running: Ubuntu Natty on a  Acer Aspire Timeline X(4830G)

Following this thread:
[http://ubuntuforums.org/showthread.php?t=1820080](http://ubuntuforums.org/showthread.php?t=1820080)

and more specifically this post:

[http://ubuntuforums.org/showpost.php?p=11128442&postcount=13](http://ubuntuforums.org/showpost.php?p=11128442&postcount=13)

I have manged to get sound working on this laptop, However it requires me to run HDA Analyzer ever boot to return on EAPD on Node 0x1B

I was wondering if there was a more permanant solution availible such as a script or a command that i could run on start up to enable this, or perhaps a configuration change.

I almost have this laptop running natty nicely and this is the one remaining thing thats still bugging me, any help would be greatly apreciated :D, thanks

Open a terminal and type "alsamixer" (no quotes). You should see a graphical display, or sorts. Look to see where the volume for Speaker is set, or if there's MM in the little box below the vertical bar associated with Speaker. If it shows 00 (2 zeros), use the right, or left, arrow key to highlight Speaker. The word should turn [COLOR=DarkRed]red[/COLOR]. If MM shows, hit the M key to unmute it, and then the up arrow key to increase the volume.

If that works for you, hit Esc to quit that, once you've adjusted the volume sufficiently to make a difference. Then, while still in the terminal, type "sudo alsactl store" (again, no quotes). Enter your password and hit Enter. That'll save what you did before.

Hope that works for you.

---

### Post by ahref on 2011-08-08
It worked thanks :D

---

### Post by scheibenlosen on 2011-08-08
Good to hear. I had the same thing happen when I installed 10.10. It took me a few minutes to remember what I did to fix it, though. :)

---

