---
title: "Hiding Sidebar In xpdf"
date: 2008-11-17
forum: General Help
---

### Post by Nosophorus on 2008-11-17
I have downloaded xpdf and I can't hide the sidebar in PDF files (see the picture attached).

I tried to do it through mouse, but there is no mouse option available for that. Then I realized I should configure my xpdfrc file located at /etc/xpdf. I did it. I put the following lines in that file (the lines with "#" are comments):

#bind cntrl-l toggle the outline
#command
bind cntrl-l any toggleOutline

That is, when I pressed CNTRL+L the sidebar should hide, but nothing happens at all.

I would like to add that feature in xpdf, since it would be much more useful to me.

Any help?

Thank You!

---

### Post by Th3Professor on 2008-11-18
^L = redraw (by default)
Have you tried another command?

---

### Post by Nosophorus on 2008-11-19
Hi!

I was not aware CNTRL+L would redraw.

I tried CNTRL+Y and nothing is happening. The sidebar does not hide. Unless CNTRL+Y is another default command which I am not aware of.

Thank you!

---

### Post by Th3Professor on 2008-11-20
I don't see Y as a default control- command (checking "?" button within xpdf).

Have you tried configuring it with ^ instead of CNTRL?

Perhaps ^L or ^+L... though I'd suspect ^L would work first.

...I mean ^Y (instead of L).

---

