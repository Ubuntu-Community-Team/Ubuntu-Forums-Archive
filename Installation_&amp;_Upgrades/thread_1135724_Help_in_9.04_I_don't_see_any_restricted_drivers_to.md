---
title: "Help: in 9.04 I don't see any restricted drivers to activate"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by tjwolf on 2009-04-24
I was previously running Ubuntu 8.10 with the nvidia restricted drivers activated.

I decided to do a fresh install of 9.04 today, but I can't figure out how to activate the NVidia drivers.  In 8.10, when I went to System->Administration-Device Drivers, I would see the NVidia driver and I could enable it.  After installing 9.04, I don't see ANYTHING on this screen!  I went into the Synaptic package manager and searched for 'nvidia' I find a bunch of packages that are installed!

Does anyone know what I'm doing wrong?  I really need the nvidia driver because i want to make use of the second (and bigger) monitor (using twinview).

Thanks a bunch.

P.S. the machine is a Dell Latitude D820 - as I mentioned, graphics-wise, everything was running just fine in 8.10.

---

### Post by ScottBurnham on 2009-04-24
I am having the same problem. Fresh install of 9.04. I go to System>Admintation>Hardware Drivers and there is nothing listed to enable. In the past nvidia drivers have always shown up. any ideas?? this 800x600 view is not to my liking! Thanks!

---

### Post by tjwolf on 2009-04-24
Scott,
I just went into the "Software Sources" and picked a site near me (Columbia University) instead of relying "Main Server" (under the assumption that perhaps it was overworked).  Turns out that this was a good thing to do.  After I made this change and ran "Update Manager" again, I went back to "Hardware Drivers" and I now see the NVidia drivers!

I activated the latest one and am now waiting for the download to happen...it seems very slow - probably because of all the Jaunty downloaders :-)

Hope this helps you too.
tom

---

### Post by ScottBurnham on 2009-04-24
Thanks, I made sure the system was up to date and reset my computer and I came right up in the Hardware Drivers.

---

### Post by tjwolf on 2009-04-24
...I see the drivers, but whenever I try to activate, it tries to actually download the drivers and eventually fails with the message:

[I]Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend[/I]

When I reported it, I found that quite a few others have had this problem :-(

---

