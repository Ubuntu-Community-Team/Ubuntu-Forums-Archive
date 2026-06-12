---
title: "(critical) fixing ubuntu installation"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by kahootbot on 2009-05-18
I was going to install an older version of WINE which I suspected may allow an application to work a little better. I uninstalled WINE and ran the .deb package for the older version and noticed not all dependinces were resolved.

I began to reexamine the package for WINE inside Synaptic package manager and clicked to completely remove it with all dependences. After it was removed I executed the package again and noticed one more library was unresolved.

I made the mistake of clickling "completely remove" because apparently there were some rather critical software componants in that list. I think the library started with the letter "d" but I can't be sure.

I noticed a lot of my games/apps were uninstalled. I had to apt-get "gksu" for the package manager to work after I closed it via ctrl-alt-f1 and reinstall even the terminal.

I rebooted and I now have this screen
> 
Boot from (hd0,0) ext3 ad85ed48-a10b-462a-8719-6fb19fc4aafe
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/5ad63a98-faac-4934-9b44-a19fe3ccb1c6) = dev(8,5)
kinit: trying to resumefrom /dev/disk/by-uuid/5ad63a98-faac-4934-9b44-a19fe3ccb1c6
kinit: No resumeimage, doing normal boot

Ubuntu 9.04 Stonewall login tty1

Stonewall login:

there may be minor inacurracies as I typed that by hand.

I tryed logging in and typing "startx" but that lead to a rather older looking window manager with no tabs of any kind and when I left-click I get a "built-in" menu.

So, to some it all up I have command-line and internet access.. I'm thinking if there is a way to reinstall/get all that Ubuntu comes with by default I can restore my installation back to normal. Other than that... maybe if Ubuntu keeps a recent uninstall log somewhere and I could manually view it in VI? :(

---

