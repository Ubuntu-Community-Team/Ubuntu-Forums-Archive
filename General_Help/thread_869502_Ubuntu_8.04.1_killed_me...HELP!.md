---
title: "Ubuntu 8.04.1 killed me...HELP!"
date: 2008-07-24
forum: General Help
---

### Post by reponzo01 on 2008-07-24
I just installed my latest updated in the update manager and it seemed to have completely killed me! After rebooting, I realized that it updated from 8.04 to 8.04.1. Then my system got pwned. 

Immediately after rebooting, there was an error message saying that "The default configuration parameters for GNOME Power Manager has not been installed correctly. Please contact your system administrator." All good and dandy...except that I AM the system administrator and I don't know what to do.

Not only that, Every single one of my menu icons has vanished. All my menu items are there such as Accessories->Calculator blah blah blah...but all of the icons have vanished.

Ubuntu is now permanently stuck on a weird-looking theme. No matter what I change my theme to, nothing like my window borders or folder icons change. I have no idea what theme this is that it's stuck on but it seems to be some sort of low-power low-graphics theme.

Originally, my Visual Effects in my Appearance Preferences were set to None. After rebooting, every single Minimize|Maximize|Close buttons in every window vanished. They came back only after I set my Visual Effects to Normal.

Clicking the Logout button on the top-right corner used to bring up my little screen with the logout/restart/shutdown etc. options. Now, upon immediately clicking the logout button, it immediately logs me out. No more options. 

I have no idea what these "upgrades" did, but whatever they did, they took out my whole Ubuntu installation. Is there any way at all to go back to 8.04 without reinstalling the whole thing?

Thanks!!!

---

### Post by buntunub on 2008-07-24
I would check my logs out to see what is causing the issue. Look in System > Administration > System Log, or via Terminal

```
$tail /var/log/messages
```

Until you figure out exactly whats going wrong, there really is not much you can do to fix it.

---

