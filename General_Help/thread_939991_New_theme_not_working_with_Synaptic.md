---
title: "New theme not working with Synaptic"
date: 2008-10-06
forum: General Help
---

### Post by belovedmonster on 2008-10-06
I installed a new theme from gnome look and I love it, but for some reason synaptic and other sudo apps are not themed. Do I need to do an additional step to theme these apps the same as the rest of my desktop?

Thanks.

---

### Post by Perfect Storm on 2008-10-06
The good thing is that you can see which apps runs with superuser (less chance to make mistakes).

But if you really insist;

```
sudo ln -s /home/USERNAME/.themes /root/.themes
sudo ln -s /home/USERNAME/.icons /root/.icons
sudo ln -s /home/USERNAME/.fonts /root/.fonts
```

This only works if you have installed a custom themes in $home

---

### Post by belovedmonster on 2008-10-06
Thanks!

---

