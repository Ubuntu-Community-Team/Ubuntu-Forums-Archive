---
title: "Somehow managed to lose my trash folder..."
date: 2008-09-09
forum: General Help
---

### Post by devosion on 2008-09-09
Im sure this has much to do with the fact that ubuntu no longer auto-mounts my usbs, no big deal really but still searching for assistance on that problem. In any case whenever I load up nautilus and click on the link to trash on the left pane nautilus will sit and stall without doing anything. The box goes grey and im left to force quit out. When I attempt to find the folder within terminal, ~/.Trash, it simply isnt there. The same applies for my root account, the root folder does not have a trash folder. This brings to mind the question of just what happens to my deleted files then, and can I simply just make another .Trash folder in my home folder and root folders and expect things to work out. And if I can is it .trash or .Trash?

Thanks!

---

### Post by iaculallad on 2008-09-09
Actually, it's **Trash** (w/o the hidden attribute) in Hardy. It's located in:

> ~/.local/share/Trash

and in Gutsy (w the hidden attribute):

> ~/.Trash

---

