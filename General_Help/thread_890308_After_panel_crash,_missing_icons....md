---
title: "After panel crash, missing icons..."
date: 2008-08-14
forum: General Help
---

### Post by Stratis on 2008-08-14
The panel just crashed on my last login attempt and now I'm missing icons and other items on the panel. 

My speaker icon is missing as well as system monitor and temp displays.

Keeping in mind I've tried to log in/reboot:

Is there a way to **recover** those items (without having to re-add them). 

If there is no other way then surely I will end up re-adding them, but I have them all configured a great deal.

Is there some sort of lock file I can delete to fix this issue? : )

Does anyone here have any idea what the issue could be? 

I can't see how a crash could mess the panel up so much (Although I used to use Xfce and it happened quite frequently). 

Thanks for any help. : )

---

### Post by iaculallad on 2008-08-14
On your terminal:

```
sudo apt-get install --reinstall gnome-applets
```

---

