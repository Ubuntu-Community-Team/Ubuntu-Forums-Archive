---
title: "ATI radeon 9000 issues with compiz on a user account"
date: 2008-09-03
forum: General Help
---

### Post by tstack77 on 2008-09-03
I created a seperate user-class account on my older laptop with an ati mobility 9000 card. The standard work around to get compiz up and running:

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

...did nothing, and I can only assume it's because it's a user account. How do I work around this?

---

### Post by tstack77 on 2008-09-03
Or, how can I gring up my administrator account in the terminal while in this separate user account (when I attempt to use sudo it asks for the user password).

EDIT: figured out how to switch to my account simply by using 'su <username>'

Unfortunately after I switched and ran the above command, compiz still could not be enabled.

help



EDIT2: Managed to get it working by simply logging out of my account (switched to user account without fully logging out), then restarting. My original assumption that it wasn't working because I was in the user account seems to be wrong. I cannot say for sure what made it work, but if you're in the same situation, log out and restart.

---

