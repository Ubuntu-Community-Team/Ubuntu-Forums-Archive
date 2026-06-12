---
title: "Router homepage reload-cycling"
date: 2008-07-13
forum: General Help
---

### Post by echo314 on 2008-07-13
When I view 192.168.0.1, the page just gets stuck in a reload cycle. If I disable adblock plus, it seems to work temporarily, in that I can at least go to other tabs in the config menus. 

However when I go to the status page (where all the info is, IP, DNS, dhcp status, etc.) it still goes into reload cycles where all the info is 0.0.0.0 (or some similar default), every once in a while running smoothly and correctly displaying info before going back to reloading.

Also, in the port forwarding tab, when I click the 'select machine' button, no IP addresses show up (normally mine would, as well as the other comp thats connected to the router.)

---

### Post by ghost_ryder35 on 2008-07-13
what type of router is it?  Linksys, D-Link etc...

what browser u using? if firefox try opera

Flash installed? if not try installing it

---

### Post by echo314 on 2008-07-13
Its a D-link router, using Firefox 3, with flash installed. Maybe this is an FF3 issue...this has not always been a problem, I just have not nailed down when the issue started.

EDIT: I installed FF2, but whenever I go to the about section, it shows it to be running 3.0. I've selected 2.0 from the Internet menu, and running firefox-2

---

### Post by ghost_ryder35 on 2008-07-13
did you check out Opera yet to see if it is a FireFox issue?

```

sudo apt-get install opera

```

---

### Post by echo314 on 2008-07-13
Hmm, no installation candidate, and does not show up with the gui method. Is there a special repo I should enable?

---

### Post by echo314 on 2008-07-15
lump

---

### Post by coffeecat on 2008-07-15
Opera doesn't show up for me either and I wouldn't know where to get it. I must admit I haven't a clue what might be the problem here, but if you want to try another browser to see if this is a firefox issue, why not install konqueror and try that?

I'm presuming you are using Ubuntu/Gnome or Xubuntu here. If you don't know already, konqueror is the file browser for KDE, but it's a good web-browser too. It works fine in Gnome, but it will drag a load of KDE libraries in if you install it. Worth a try anyway, I would have thought.

---

### Post by echo314 on 2008-07-17
The router seems to work fine in Opera and correctly displays network information. I just installed the .deb from Opera's site.

What are some steps I can try with Firefox to get it working correctly? The router page is the *only* page where this reloading occurs, and I visit lots of other pages where I have no new issues, secure and non-secure, different layouts, etc.

---

