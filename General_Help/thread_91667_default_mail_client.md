---
title: "default mail client"
date: 2005-11-17
forum: General Help
---

### Post by cavaughan on 2005-11-17
I am using Thunderbird as my mail client. I have even removed Evolution from my system. But I've noticed that when I click on an email address to mail to in Firefox nothing would happen. So, logically I went to:
System > Preferences > Preferred Applications
Under Mail Reader I could selected either:
1: Select: Thunderbird
2. Custom: command: mozilla-thunderbird -mail %s

Regardless of which I choose, however, when I click on an email address now it tried to open an additional profile of Thunderbird (as Thunderbird is already open). There must be a way to get it just to create a new message under Thunderbird, though. Can anyone help?

Curtis

---

### Post by cavaughan on 2005-11-17
Well, about as soon as I posted that I figured out the answer myself. What I needed to put in the Custom line was:

mozilla-thunderbird -compose %s

---

### Post by suoko on 2005-11-19
make this solution a bit more "findable" :-)

---

### Post by cavaughan on 2005-11-19
If you mean by "findable" what in fact did I do to get it to work, then more pecisely:

In order to get Thunderbird to open a new email message from an email hyperlink go to:
System > Preferences > Preferred Applications
Under Mail Reader select the custom setting and enter on the command line: mozilla-thunderbird -compose %s

---

### Post by suoko on 2005-11-19
No, I meant it's not easy to find your solution with the post title you used.

---

