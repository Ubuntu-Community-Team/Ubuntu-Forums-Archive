---
title: "Update manager not downloading nor installing"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by garet jax on 2008-12-24
Hi,

I updated from Hardy to Intrepid, and update-manager stopped working properly.

At first I noticed that update-notifier did not work, and it turned out it was because the /etc/cron.daily/apt script was not set as executable.
Fixed now.

However, update-manager is still not working. Now it correctly displays that there are updates, but when I press the "Install Updates" button nothing happens: no downloads, no installation. It just reloads (a dialog "Reading State Information" appears) and displays the updates as if I did not push the "Install Updates" button. The button is not grayed out.

I started update-manager from a console, but no error messages are printed.

I know I can workaround the issue by using apt-get, but I would rather have update-manager working again.

I tried to uninstall it, but Synaptic says I have to uninstall also ubuntu-desktop, so I did not do it.

Has anybody encountered this problem ?
Is there a way to log or debug or understand why the "Install Updates" button is not working ?

Thanks !

---

### Post by pouk-ledden on 2008-12-24
I had a similar problem, though once I got the manager to see updates it could install them, too. In my case, it seemed to stem from having switched the server to a mirror. I had done that to get better download speeds on that first day of Intrepid's release (main servers were slooooooow :) ). For whatever reason, though, the mirror never gave any further updates. Switching back to the main US server revealed dozens of updates. In my case, as I said, that did it -- I was able to download and install them, too.

---

