---
title: "[SOLVED] firefox broken"
date: 2008-07-30
forum: General Help
---

### Post by SpikeyMike on 2008-07-30
Hi,

I installed vmware yesterday and I noticed it updated firefox at the same time, the thing is now firefox doesn't work properly any more, all my bookmarks are gone, it doesn't open my homepage when i start it but just a blank page and the previous and next buttons are grayed out all the time. I tried uninstalling and reinstalling it but that didn't work either, I still have the same problem, any help appreciated

Spikey

---

### Post by aysiu on 2008-07-30
Can you close all instances of Firefox, paste this into [the terminal](http://www.psychocats.net/ubuntu/terminal) and see if you get the same problem? ```
firefox -safe-mode
```

---

### Post by SpikeyMike on 2008-07-30
> **aysiu said:**
> Can you close all instances of Firefox, paste this into [the terminal](http://www.psychocats.net/ubuntu/terminal) and see if you get the same problem? ```
firefox -safe-mode
```

Hi, thanks for your reply, I tried that but it makes no difference, Is there a way to completely remove firefox and then reinstalling? I believe removing it using synaptic doesn't remove everything...

Spike

---

### Post by SpikeyMike on 2008-07-31
its fixed, what I did was delete xyz.default (where xyz is a series of letters and numbers) and profiles.ini from the .mozilla/firefox folder, I then completely removed firefox 3 and reinstalled it again and it works. I think it was a problem with an update for firefox as I see other people are having similar problems.

Spikey

---

