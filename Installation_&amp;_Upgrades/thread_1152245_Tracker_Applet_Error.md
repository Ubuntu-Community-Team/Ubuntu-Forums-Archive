---
title: "Tracker Applet Error"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by vegas588 on 2009-05-07
Hi,

I recently upgraded to 9.04.

When I start the computer, an error message pops up with this info:

Tracker Applet...There was an error while performing indexing...Index corrupted.

I get three options: Reindex All Contents, Cancel, OK

I cannot get out of it no matter which option I choose. The message box just stays up and nothing seems to happen.

---

### Post by kentpend on 2009-05-08
I'm having the exact same problem.  Suggestions?

---

### Post by JimBuntu on 2009-05-08
I have the same thing after upgrade and when I click the "reindex" button a smaller window pops up behind that initial window and you have to click to that smaller window in order to chose "yes" to reindex. If that makes sense...Then after you chose "yes" you should be able to click "ok" on the initial window again...

---

### Post by alfonsoabas on 2009-05-08
This is a Known bug and it will be fixed as soon as possible. You can use this temporaly solution *(it worked to me)*:
sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset

More details about this bug in the official bug-tracker page for Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

---

