---
title: "disable network monitor"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by cneil on 2006-06-14
Hello!
I am really happy today because I was finally able to get all of my hardware working on my 7510GX computer on Dapper Drake.  The wireless was a pain in the rear, but I worked with a few of the how to's and it just started working all of a sudden.

I used Network Manager to get it to work, but Network Monitor is still on my system.  It has never worked and it always gives me some SIOCGIFFLAGS error.  I want to just get rid of this troublesome program if it is possible.  

Does anyone have any suggestions?

---

### Post by c-prompt on 2006-06-14
Right click the applet and select "remove from panel"... or am I missing something in your question?

---

### Post by cneil on 2006-06-14
I wasn't specific enough.  I know that you can remove that thing from the panel, but I was wondering if it was possible to completely uninstall whatever package that it came with.  In order to get Network Manager to work, I had to completely disable Network Monitor, including the config file. When I go Administration>Networking it shows ever piece of hardware as being disabled.  Yet, in reality everything works better than ever.  I thought that I might as well completely remove Network Monitor.

Thanks for your reply.  I really appreciate it.

---

### Post by c-prompt on 2006-06-14
I believe there's 2 packages associated with that: gnome-nettool and gnome-netstatus-applet. However, removing either one also remove ubuntu-desktop.  You might be able to get away with removing them, then installing ubuntu-desktop back.  Then again, there's a good change they'll get pulled right back on to the system.

---

