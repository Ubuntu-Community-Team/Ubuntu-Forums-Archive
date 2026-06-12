---
title: "Brother MFC 7340"
date: 2014-04-19
forum: Hardware
---

### Post by jonathan71381 on 2014-04-19
Hello All

I am trying to completely void windows out of my life.  Unfortunately, I can't seem to get my Brother MFC 7340 printer to work.  I have tried installing similar drivers as mentioned, but it only shoots through infinite blank pages.  Has anyone actually gotten this one to work?  

Thanks in advance

---

### Post by pdc on 2014-04-20
Hi Jonathon; welcome to the forums;

If we see what you have installed first; if you click on this link, [http://localhost:631/printers/](http://localhost:631/printers/) it opens CUPS (the linux printer admin screen)

how many printers are listed? Left hand column is called Queue name and if you copy and paste back here? .........try to include the right-hand column called Make and Model

are you familiar with opening a terminal? [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) .............the guide suggests typing terminal in the Dash Search function..........

when opened, if you paste this command into the terminal (I suggest using the mouse to copy; and also paste: in the terminal look for the top line: start at Menu at the left and move to Edit and down to Paste ..........)

> [COLOR="#FF0000"]dpkg -l | grep Brother[/COLOR]    ...........so this command is talking to the debian package management system (dpkg) and asking it to list (-l) any files that have Brother in them ............ and report it back to you!!

If you copy and paste here what you get please .....it may be we suggest deleting what you have already; as it seems not to work for you .............

___________________________________________________

if you subscribe to a thread; (it is about five paragraphs down on this page,) you may keep in touch with it more easily ..............

---

