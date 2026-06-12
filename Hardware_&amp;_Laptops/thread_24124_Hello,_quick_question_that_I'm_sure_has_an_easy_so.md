---
title: "Hello, quick question that I'm sure has an easy solution"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by pinecone on 2005-04-05
I'd like to set it up so that on the mixer "External" is muted by default on start up.  I can't get sound to play unless it's muted.  Thanks in advance.

---

### Post by alastair on 2005-04-05
If you have a look at the ALSA sound start up script :

/etc/init.d/alsa

You will see it does various magic things to check/restore/save ALSA sound module state(s).

It references a file (for me) :

/var/lib/alsa/asound.state

Which probably allows you to mute a channel. See the ALSA docs as well.

---

### Post by skoal on 2005-04-05
You should be able to run alsamixer as user (or root), set your options, hit ESC, and then type 'alsactl store'.  That should preserve the settings on reboot for alsa.  There's probably a more elegant way of doing this but I haven't used Gnome in quite some time.

---

### Post by pinecone on 2005-04-06
thank ya'll that'll work fine.

---

