---
title: "[SOLVED] Reset Terminal to Default Profile"
date: 2008-10-26
forum: General Help
---

### Post by Matthileo on 2008-10-26
I changed a setting in my terminal profile, but now I can't open a terminal.
How do I open terminal using the default setting so I can fix this problem?

EDIT
It's not so much that terminal won't open, but instead it opens, starts a new terminal, and exits -- the new terminal repeats the process.
The setting I changed was that I checked Run a custom command instead of my shell, and the command was
gnome-terminal --geometry=100x30

---

### Post by sylvainrb on 2009-01-14
Your thread shows as solved and I have the same problem after I checked Run a Custom Command. How did you resolve it?

I tried reinstalling gnome-terminal with Synaptic Package Manager but still won't work.

Thank you!

---

### Post by Krydox on 2009-01-16
Open xterm and run for example the following command:

gnome-terminal -e top

You can use a different command then "top" too.. but anyways with this it'll stay open.

---

