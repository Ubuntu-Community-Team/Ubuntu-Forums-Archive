---
title: "Wireless doesn't work at all, even with multiple adapters"
date: 2009-02-15
forum: Hardware
---

### Post by EddieRingle on 2009-02-15
Really, I just don't understand it. The last time I installed Intrepid on my laptop my internal wireless card (BCM4306 rev 03) worked out of the box, and that's what it says on the wiki as well. Now not only is that not working, but my Cisco 340 PCMCIA card doesn't seem to connect either.
The PCMCIA card worked at my house, but now I'm down with relatives in Indiana. I am hooked up via ethernet right now, and just can't figure out what's wrong.
I even updated the distro to the Jaunty alpha, and that didn't help. Is it a bad install? I really can't do anything about that until I get home later this week, so I'm hoping someone can help.
Here's the rundown: Both my internal Broadcom card and the Cisco PCMCIA card are detected. The problem is no networks are listed in the menu when I click the network icon. (And my uncle has confirmed that there are networks around us that don't hide their networks, including his, so I should be able to see them.) Further more, when I choose to add a hidden wireless network, I can do all that fine, but when it comes to connect it just sits there trying for a few minutes then comes back with nothing.

Help? :\

---

### Post by EddieRingle on 2009-02-16
Am I stuck like this? I'm getting ready to dump Ubuntu for Windows.

I'll download a 8.10 iso and try installing one more time, but if that doesn't work, I'll have to switch back to Windows.

Personally, I love linux, and I know it's not anyone's fault that it doesn't have awesome wireless support, but it'd still be nice to know that someone is at least listening to what I'm saying.

---

### Post by mlsquad on 2009-02-18
> **EddieRingle said:**
> Am I stuck like this? I'm getting ready to dump Ubuntu for Windows.

I'll download a 8.10 iso and try installing one more time, but if that doesn't work, I'll have to switch back to Windows.

Personally, I love linux, and I know it's not anyone's fault that it doesn't have awesome wireless support, but it'd still be nice to know that someone is at least listening to what I'm saying.

Do the following from a command line:
iwlist scan

Let us know if you get any results.

---

### Post by EddieRingle on 2009-02-19
During my trip, that command did not return any results (I think it produced a warning or something).

But the strangest thing happened, I got home from Indiana and when I went to show my dad what was wrong, everything magically worked.

As my buddy in the Netherlands put it: "Hurray for random errors!"

:)

EDIT:
Also read the following post for a discussion between me and another friend and how he was also unsure as to what it was. (Later on skype he told me to ask in Ubuntu's irc channel, which didn't work but I didn't really need it either at that point.)
[http://www.ferrousmoon.com/forums/viewtopic.php?f=55&t=1674](http://www.ferrousmoon.com/forums/viewtopic.php?f=55&t=1674)

---

### Post by mlsquad on 2009-02-19
I have an old laptop with a BCM4306 rev 02 driver and would have the same problem.  At home and most other places the connection was fine, but as some random places my wireless card wouldn't show any signal.  Every so often it would, but usually that place looked like a dead zone to my laptop.
I don't know what causes this, but the only solution is probably for the bcm line of cards to finally get an open source driver. :(

---

