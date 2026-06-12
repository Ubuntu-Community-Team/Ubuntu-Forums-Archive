---
title: "Uninstall Dependencies??"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by Rami_961 on 2009-08-09
hi..i'm very new to linux, is there's a way to remove dependencies?
I want to install vlc-nox_0.9.9a-2ubuntu1_i386.deb but when i try to do that they tell me that a later version is alredy installed (that's because i installed when i was mewssing arround with ubuntu), any ways is there's a way like to list all dependencies installed and remove the one i want?
//sorry for my bad english!

---

### Post by slakkie on 2009-08-09
you can look at dependencies by doing:

aptitude -D show package_name
or
apt-cache depends package_name

---

### Post by Rami_961 on 2009-08-09
thx for the help man, now i find the way to remove package too:
sudo apt-get remove {[COLOR=#996633]package-name[/COLOR]}

---

