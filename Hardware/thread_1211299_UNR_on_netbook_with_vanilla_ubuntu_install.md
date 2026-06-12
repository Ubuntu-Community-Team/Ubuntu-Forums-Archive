---
title: "UNR on netbook with vanilla ubuntu install"
date: 2009-07-12
forum: Hardware
---

### Post by earthpigg on 2009-07-12
so, my little dell mini 9 had 8.10 installed -> dist upgraded to 9.04.

regular ubuntu, not dell's abomination.
```

sudo apt-get install ubuntu-netbook-remix
```

aaaaand i restart.


and get the attached.

if a window or app is open, it looks like the attachment.

if a window or app is not open, the panel cannot be seen at all.... or maybe part of it can be - the networking applet on the right side of the gnome panel, for example, likes to pop up all by itself leaving the rest of the panel invisible.

when i can see the panel, it has clearly been changed a bit by the ubuntu-netbook-remix package -- but remains buggy. this reminds me of AWN from the repos of 7.10 ubuntu :P


thinking something i may have done earlier to customize the panel might be the culprit, i removed /.gconf/apps/panel and tried restarting... no dice.

this is what i was expecting:

notice the *functional* and *visible* and non-buggy gnome-panel at the top. the *whole* panel is visible, not just one little part of it flashing momentarily. 
[IMG]http://www.techdigest.tv/assets_c/2009/04/ubuntu-netbook-remix-thumb-500x375-87951.jpg[/IMG]

the image attached is what i got.

anyone have any ideas?

---

### Post by earthpigg on 2009-07-12
solved it myself.

had underestimated the buginess of compiz. i should know better.


```
metacity --replace
```

fixed it. turning off visual effects in system -> preferences -> appearance is the permanent fix.

---

