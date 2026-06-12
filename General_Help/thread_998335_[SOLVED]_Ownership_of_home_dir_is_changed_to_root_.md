---
title: "[SOLVED] Ownership of home dir is changed to root every boot"
date: 2008-11-30
forum: General Help
---

### Post by buttertoad on 2008-11-30
It started with a .dmrc error when I logged on, so I tried changing permissions on .dmrc and I couldn't. Upon further investigation I found that root had ownership of my home directory.

I changed everything back to the way it should be and it was fine. I could logout and in ok but when I reboot root has taken ownership of my home directory again.

I noticed that 3 directories appear in my home directory every time I boot also. They are drwxr-xr-x root:root for permissions.

So my question is: can I trace what program is creating these directories? I imagine it's the same thing that is screwing with my home ownership.

I've checked /etc/init.d for suspects but haven't found anything yet. It's driving me nuts and I'm at the point where I might reinstall, but I hate to do that because I know there is a solution.

Thanks for any help that can be provided.

---

### Post by buttertoad on 2008-12-12
After going in circles I remembered I had installed TimeVault to try out. I uninstalled it and everything is fine now. 

I have no idea why it was trying to do the things it was but I guess I'll chalk it up to live and learn.

---

