---
title: "Bluetooth disabled at startup"
date: 2009-12-27
forum: Hardware
---

### Post by reesje on 2009-12-27
Hi guys,

My brother has a IBM T42 laptop and when it starts up, bluetooth is always disabled. This is annoying for him, since he uses BT for his mouse.

On my HP DV5100 it is enabled at boot. Is there any particular reason that it is disabled on the T42 at boot? Is there a way to make it enabled at boot? We are both running Karmic, with the only difference being that he installed it freshly while I upgraded from Jaunty.

BR,
René

---

### Post by sgosnell on 2009-12-27
Is the bluetooth manager running at startup?  Open System/Preferences/Startup Applications and make sure Bluetooth Manager is checked.

---

### Post by mathuna on 2009-12-27
You'll find it labeled as "Bluetooth Support Service" or something to that matter in the list. Right click and go to properties, and change the Startup type to "disabled," which will prevent it from starting up upon login.

Hope this helps, have a nice day
=====================================
[yoostar](http://www.newsday.com/business/review-yoostar-is-a-movie-studio-in-a-box-1.1401673)
[wildlife paintings](http://www.davidshepherd.com)

---

