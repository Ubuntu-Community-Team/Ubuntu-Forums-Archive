---
title: "Emptying trash takes ages"
date: 2008-11-15
forum: General Help
---

### Post by isecore on 2008-11-15
I recently did some cleaning and threw away some 200+ gigabytes of data. It all ended up in the Trash, no problems there.

But when I go to empty trash, it takes eons to empty. So far I've waited two hours (!) for it to empty, and it's only gotten to something like 40% of all the stuff in it. Seemingly it's not doing anything either, since my disk is still. All it does is spin the CPU (currently using about 1½ cores on my quadcore).

Why? It just seems so... stupid.

---

### Post by -grubby on 2008-11-15
Perhaps try not using the GUI. 

Run this : 

```

rm -r ~/.local/share/Trash/*

```

---

