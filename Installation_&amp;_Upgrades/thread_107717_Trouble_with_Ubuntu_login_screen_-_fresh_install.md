---
title: "Trouble with Ubuntu login screen - fresh install"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by moollar on 2005-12-23
Hey everyone,

I've tried this with Breezy and Hoary and get the same result. Done a fresh install on my bro-in-law's computer and when the login screen comes up the screen goes pretty whacky (funny coloured patterns) and the system locks up. I've got a feeling that it's something to do with his cheap graphics card. It's an AGP GeCube ATI 9200 SE 128MB.

Thanks in advance...

---

### Post by moollar on 2005-12-26
Has ANYONE seen or heard of this before???

---

### Post by christhemonkey on 2006-01-08
I had this problem as well,
to sort it i went into a console by typing Ctrl+Alt+F1
and then ran the command:
sudo xorgconfig
it will then prompt you for the su password.
It then proceeds to ask about various things and the 1 that was wrong for me were the vertical and horizontal sync rates.
Hope that helps.

---

