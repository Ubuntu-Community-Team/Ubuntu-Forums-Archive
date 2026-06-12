---
title: "Effects settings not stored between sessions"
date: 2008-11-29
forum: General Help
---

### Post by richardq on 2008-11-29
I've just installed an Nvidia 7300gs card in my machine after 2 years of using the onboard Intel video (boy this is nice). And of course I immediately turned on a bunch more bling which works great. HOWEVER... 

I am finding that when I logout or shut down the system (using the normal System->Quit) and then restart or log back in, it doesn't hold my Compiz settings at all. So when I restart, No desktop effects are enabled and then when I enable them, any customizations I made to the compiz effects are not saved either.

Any ideas why it isn't holding my settings?

Also, (and this started happening a week *before* I installed the Nvidia card), it takes about 45sec for the shutdown menu to come up from the time I select System->Quit. It never used to take nearly that long. The system monitor shows little if any cpu usage during that 45 sec. I just thought I'd post it in case the two items were related in any way.

Thanks.

---

### Post by richardq on 2008-11-29
I've been able to solve both problems. 

To fix the delay in reaching the logout screen, I had to enable Power Manager in the Preferences->Sessions dialog. I'm not sure why it wasn't enabled.

This got me to thinking about compiz and after a bit more research I found that the compiz.desktop file was missing from my /etc/xdg/autostart directory. I had moved it to a temporary folder about a year ago when I moved to using Openbox. Putting that back in it's place then allowed the CompizFusion entry to show up in the Preferences->Sessions dialog once again. I've checked that and now it seems to hold the settings between sessions.

---

