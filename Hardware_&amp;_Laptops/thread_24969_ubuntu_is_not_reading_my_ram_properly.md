---
title: "ubuntu is not reading my ram properly?"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by spade_ on 2005-04-08
I currently have 1.5gb of ram in this system , all other distros read everything, even memtest on ubuntu sees all of it. Yet when i'm in ubuntu, I go to console I type top...it gives me arond 900660k , looked at gnome's system monitor and it tells me the total amount is 866mb.

Whats the problem? I've re-installed it over and over with different file systems i even added linux mem=1536M last time I installed and still it didnt recognize all of it.

is there an actual solution? is trying out kubuntu to see if the bug or whatever it is resides there? I hope you guys can help me on this as soon as possible.
thanks

---

### Post by bored2k on 2005-04-08
[QUOTE=spade_]I currently have 1.5gb of ram in this system , all other distros read everything, even memtest on ubuntu sees all of it. Yet when i'm in ubuntu, I go to console I type top...it gives me arond 900660k , looked at gnome's system monitor and it tells me the total amount is 866mb.

Whats the problem? I've re-installed it over and over with different file systems i even added linux mem=1536M last time I installed and still it didnt recognize all of it.

is there an actual solution? is trying out kubuntu to see if the bug or whatever it is resides there? I hope you guys can help me on this as soon as possible.
thanks[/QUOTE]
 Default kernel [386] supports up to 900mb. In a terminal do
sudo apt-get install linux-686 or in Synaptic search and install that.

---

### Post by spade_ on 2005-04-08
are you kidding? Why not just release a 686 version instead of 386?

---

### Post by spade_ on 2005-04-08
oops double post sorry

---

### Post by bored2k on 2005-04-08
[QUOTE=spade_]are you kidding? Why not just release a 686 version instead of 386?[/QUOTE]
 Because not everyone has a 686 processor. Those are for pentium3 and higher sir.

---

### Post by spade_ on 2005-04-08
I see...well thanks for the tip i'll try that.

---

