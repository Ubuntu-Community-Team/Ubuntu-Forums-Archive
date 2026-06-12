---
title: "I created a GUI to change laptop-mode settings"
date: 2008-10-07
forum: Hardware
---

### Post by lokster on 2008-10-07
Hi everybody!
This is one of my first attempts in writing GTK application in C (I am still new to the linux programming), but I think the result is very good.
I created a GUI to set up most of the settings found in /etc/laptop-mode/laptop-mode.conf and /etc/default/acpi-support

Screenshots:
[[IMG]http://img73.imageshack.us/img73/6667/screenshotlaptopmodesetwx6.th.png[/IMG]](http://img73.imageshack.us/my.php?image=screenshotlaptopmodesetwx6.png)

[[IMG]http://img300.imageshack.us/img300/1941/screenshotlaptopmodesetgu3.th.png[/IMG]](http://img300.imageshack.us/my.php?image=screenshotlaptopmodesetgu3.png)

You need administrative privileges to change the settings.
When you apply the new settings, a backups of the two files are made, in /root/.laptop-mode-setup/. You can restore these backups later, from the small "undo" buttons on the two tabs.

The button "Apply" saves the settings and runs /etc/init.d/laptop-mode restart

You can get the package from [laptop-mode-setup-0.1.deb]("ftp://guest%40learnfree%2Eeu:guest@learnfree.eu/ubuntu-packages/laptop-mode-setup-0.1.deb") (22 KB). It is compiled under Ubuntu 8.10, but should work on others too.

You can get the source from [laptop-mode-setup-0.1.tar.gz]("ftp://guest%40learnfree%2Eeu:guest@learnfree.eu/ubuntu-packages/src/laptop-mode-setup-0.1.tar.gz") (39 KB)

You will need Code::Blocks IDE to compile it (sorry - no Makefile - it's still too painful to me, and I don't like using the console, if I can do the same thing from GUI :) )

Good luck!

---

### Post by sergiom99 on 2008-10-07
seems nice, thanks dude!

---

### Post by lokster on 2008-10-21
bump :)

---

### Post by hardyn on 2008-10-21
I was actully thinking about doing the exact same thing... hehe...

maybe you should see about inclusion into the offical repos?

---

### Post by kabaiz on 2008-12-29
Yes, you should :) Nice idea :)

---

### Post by PaulHomer on 2010-06-15
Wow, I just wanted to thank you for this, it enabled a relative newbie like myself to set up laptop mode tools in a matter of seconds. It should definitely be included in the official repository.

Thank You

---

