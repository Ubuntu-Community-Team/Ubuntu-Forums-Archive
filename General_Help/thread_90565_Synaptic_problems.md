---
title: "Synaptic problems"
date: 2005-11-15
forum: General Help
---

### Post by matpark01 on 2005-11-15
In Hoary once I had downloaded the repositories the information remained in Synaptic. I've just recently installed Breezy and find that I have to download the packages each time I use Synaptic in a new session. The repositories download fine and remain present throughout that session but after a reboot the package information has gone. Is it necessary to completely update sources each session? On a DNS connection this is time consuming and expensive and not something you had to do with 5.04.

---

### Post by KingBahamut on 2005-11-15
Just edit your /etc/apt/sources.list to put in the proper repos you want.

---

### Post by az on 2005-11-15
I think it checks to see if there are new packages first.  Perhaps there are frequent updates these days and that is neccessitating that synaptic refresh itself often.

I do not think this was on by default in Hoary, nor were there that many updates in the past few months.

---

