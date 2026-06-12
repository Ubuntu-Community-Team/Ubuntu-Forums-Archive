---
title: "Synaptic having locale installation issues"
date: 2008-08-23
forum: General Help
---

### Post by battlecat on 2008-08-23
Hi!

I am running XUbuntu 7.10.

I was installing openoffice.org, via Synaptic, with all of its recommended packages on my fresh XUbuntu setup and when it cam to installing the locale AF it froze. I was forced after waiting 30 minutes to xkill Synaptic. I then tried to open Synaptic and got this  message:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I closed out Synaptic since it would not let me open it all the way. I went to the CLI and tried sudo dpkg --configure -a Once more it freezes and I see the following:

Setting up language-pack-af-base (1:7.10+20080205) ...
Generating locales...
  af_ZA.UTF-8...

That is it. I am forced to reboot to try once more because it locks the database for apt-get, Synaptic, and Aptitude. 

Anyone tell me how to eliminate this issue? I don't know why it even wants to install the AF local since I speak only EN.

Thanks
Battlecat

---

