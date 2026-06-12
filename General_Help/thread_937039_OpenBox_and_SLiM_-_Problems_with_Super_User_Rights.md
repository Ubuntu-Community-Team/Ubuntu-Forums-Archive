---
title: "OpenBox and SLiM - Problems with Super User Rights"
date: 2008-10-03
forum: General Help
---

### Post by Tr0janV0dka on 2008-10-03
I'm running Arch Linux 2008.06 Core (doesn't really matter I spose since it's rolling release)

Well, the story goes I've setup my install to run OpenBox as the main GUI and SLiM as the login manager via daemons in /etc/rc.conf . I can boot up ArchL just fine, log in via SLiM with the user luke, but this is where the troubles start. I can't start any programs (firefox, ROX, xterm seems to start though) and my OpenBox theme defaults to Clearlooks.

I can quit out of X (Ctrl+Alt+Backspace), log into one of the VCs and start X via "sudo startx" and I'll be able to start firefox, ROX, etc now and my theme won't default to Clearlooks. I've tried editing the rc.xml file in /etc/xdg/openbox to have Artwiz-boxed as default but to no avail. I've also tried editing the rc.xml file inside /home/luke/.config/openbox/ also to no avail.

Doing the above with a root user logged into a VC results in OpenBox failing to load and I just get a black background with a white outlined X for a cursor.

Any ideas? Could it be that the user luke is missing some important permissions?

---

