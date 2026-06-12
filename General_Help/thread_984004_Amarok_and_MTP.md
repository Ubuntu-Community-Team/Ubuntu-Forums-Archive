---
title: "Amarok and MTP"
date: 2008-11-16
forum: General Help
---

### Post by Lex-Man on 2008-11-16
I have an Creavte ZEN V plus and want to sync it with Amorak I have already been able to detect the player with Gnomad2 and have installed LIBMTP8.

How do I get Amorak to recognise LIBMTP8?

---

### Post by Lex-Man on 2008-11-16
Can anyone help me with this problem?

---

### Post by ggodfrey on 2008-12-07
I found out that I needed to add myself to the 'audio' group:

sudo usermod -G audio <myusername>

Note that you'll need to restart amarok.

G

---

