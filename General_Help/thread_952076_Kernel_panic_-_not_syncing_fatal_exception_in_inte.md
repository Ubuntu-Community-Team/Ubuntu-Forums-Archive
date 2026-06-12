---
title: "Kernel panic - not syncing: fatal exception in interrupt"
date: 2008-10-18
forum: General Help
---

### Post by evrkusd on 2008-10-18
Hi,
I'm trying to figure out how to fix my ubuntu install. i'm dual booting vista and ubuntu with grub. It has been working fine but during the last restart it halted on the splash screen and wouldn't go any further. I booted without the splash and it was stopping at 
44.059321  Kernel Panic - not syncing: fatal exception in interrupt

I'm not sure what caused this. I have fairly recently installed awn, conky, gnome-do and probably most recently: emerald.
I was able to go into recover mode/ the command line and uninstall emerald, gnome-do and awn but this didn't help. 

maybe there are related installs that came with these that are interfering? or maybe it was an update or something?

not sure if this is related but initially i had wireless working after a bit of work but then that randomly stopped working. not sure why or if that has anything to do with it.

any help / suggestions anyone could have / how to reinstall or uninstall a minimum amount of programs would be really appreciated.

thanks

---

### Post by Sef on 2008-10-18
Go into grub and install into safe mode.  I would remove what you have added one by one.  Remove what you have added last first.

---

### Post by evrkusd on 2008-10-18
I'm pretty sure i've done that. especially the things that were installed after the last successful restart.
I'll go try to remember/ do some more but any additional suggestions would be great.
thanks

also... i can access my ubuntu files from my windows partition but i'm not sure if there is a helpful system log or something of the sort which would point me in the direciton of what to uninstall.

---

### Post by evrkusd on 2008-10-18
it may be my madwifi install for my card but i'm not sure how to uninstall it... none of the apt-get remove madwifi.... seem to work. maybe i just don't know the right version number or something?

---

