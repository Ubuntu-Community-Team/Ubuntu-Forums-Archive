---
title: "Can't print from the command line - Please help!"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by jbulcher on 2007-02-17
Hey all,

I'm new to Ubuntu and Linux ;), and have been spending my spare time learning the ropes. Currently I'm trying to set up a LAMP server. It's been fun.

I've set up an HP5850 via USB, and it prints fine from the GUI, but it won't print whenever I try to print from a program run from the command line. So far I've tried printing from Vim and gVim. gVim prints fine if I start it from the GUI, and it doesn't when I start it from the command line. Can anyone help?

I have Ubuntu set up on VMWare Player, and the printer is connected via USB.

---

### Post by abovett on 2007-02-20
Not sure if this is the answer to your problem,. but I had a similar problem printing from Emacs or via lpr. Turned out that the default printer wasn't set up in CUPS (this is not the same as the Kde or Gnome default, it seems).

To check/fix this, access the CUPS server at  [http://localhost:631](http://localhost:631) with a web browser, click the printers tab, and set a printer as default - worked for me, anyway.

HTH

Andy

---

### Post by jbulcher on 2007-02-20
abovett,

Thanks for the reply. I set the default printer in CUPS like you said, and it worked! Thanks a lot.

I'd like to look into CUPS a bit now, to see why the Ubuntu GUI interface didn't do the trick. Do you have any suggestions on where to look?

Thanks again.

---

