---
title: "Can't open firefox, terminal, or shutdown dialog box"
date: 2008-10-05
forum: General Help
---

### Post by pockie on 2008-10-05
I have tried looking for this issue, because both myself and my friend have the same exact problem. I thought maybe it was a common thing but I don't see any thread with the symptoms I have.

Occasionally, I find that I can't open firefox. I can click it as many times as I want to and nothing happens. So, I think, I'll run it in a terminal... but alas, the terminal window tries to open, but never completely loads. It is just blank and greyed out. So I try to shut down. I press the blue arrow... but the dialog box doesn't ever open. I have to do a hard shutdown. 

My friend and I both have Ubuntu 8.04 on our laptops, but they are very different. Mine is an AMD-based Acer, and his is an Intel-based Gateway. If any further information would be useful let me know.

---

### Post by cariboo on 2008-10-05
It sounds like you both have something running that is eating all your cpu cycles. Can you Press Ctrl-ALt-F1 to enter the console. Login using your username and password, then run **top**. Check to see which program is using all your cpu cycles. It is probably something that both of you are runniong on your latops.

Jim

---

### Post by pockie on 2008-10-08
Compiz and Xorg are the only things I have running (aside from pidgin, which I doubt is the culprit.) Would Compiz cause this? I know it can cause some weird problems.

---

