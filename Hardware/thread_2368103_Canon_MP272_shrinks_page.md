---
title: "Canon MP272 shrinks page"
date: 2017-08-07
forum: Hardware
---

### Post by freesitebuilder on 2017-08-07
I have a Canon MP272 scanner/printer on Ubuntu 16.04. Recently it has started printing pages much smaller than in the preview - that displays fine, but when I print I get a two inch margin at top, bottom, and right of page. Left margin is OK. The whole page prints, but much smaller than I want.

I've tried different programs, I've tried starting with a new page in Libre Office, but same problem.

It has happened before, but fixed itself. I've looked at CUPS, printer settings in individual programs, and the system settings, but I can't track down the cause. I did change a cartridge just before the problem started, but I can't think that would cause it.

Where else can I look?
Thanks.

---

### Post by ajgreeny on 2017-08-07
How did you change the printer settings?

If you used a Canon application only, it may be worth trying **localhost:631** in a web browser to see what page layout is set there in the CUPS system.

Like you, I can see no reason why a change of cartridge should have affected this, but others may have something to say about this.

---

### Post by wyliecoyoteuk on 2017-08-07
You may have accidentally changed the paper sizes.
EU A4 metric and US Letter sizes are slightly different.
The paper sizes can be changed from within the menus on the printer, and the rear feed can be changed by pressing a combination of buttons.
manual here:
[http://files.canon-europe.com/files/soft35401/Manual/Canon%20MP270%20_MP250%20series%20EN.pdf](http://files.canon-europe.com/files/soft35401/Manual/Canon%20MP270%20_MP250%20series%20EN.pdf)

---

### Post by freesitebuilder on 2017-08-18
After experimenting in my spare time, it seems it may be Libre Office causing the problem. PDF files created by other people print OK (using Evince doc viewer) but anything produced as .doc files by myself or others (who mostly use Windows) reproduce the problem.

I'm thinking of trying out Open Office - I've used it in the past, switched to Libre Office simply because it was pre-installed with Ubuntu and my needs are fairly basic. I recently upgraded LO to 5, so that may be the problem.

---

### Post by freesitebuilder on 2017-08-31
I had the same problem on my other laptop, which I don't usually use for printing. So I removed LO and replaced with AOO which has cured the problem. Now to try it on my main laptop, and apologise to my dear old printer. An extreme solution - and I'm surprised I haven't found anyone else having the same issue. :eek:

---

