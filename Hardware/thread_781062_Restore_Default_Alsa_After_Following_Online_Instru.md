---
title: "Restore Default Alsa After Following Online Instructions"
date: 2008-05-04
forum: Hardware
---

### Post by TopRamen on 2008-05-04
In an effort to fix my Ubuntu Hardy sound issues on my Dell 700m Laptop, I followed the directions on this page:
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

Unfortunately, after doing so, my audio is now very crackly and unbearable. I've looked through the module-assistant documentation and cannot figure out how to undo the following actions:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Any assistance in doing so would be immensely appreciated. Thank you!

---

### Post by TopRamen on 2008-05-06
Come on guys. Please, I just want sound out of this damn operating system!

---

### Post by TopRamen on 2008-05-11
No love here?! Latest update is that my sound works in other applications such as Rhythmbox but it doesn't work in flash within the web browser. I really just wanna undo the changes I made by following the guide I posted above. This will hopefully fix my problem. I just don't know how to go about undoing the changes.

---

### Post by jocko on 2008-05-11
If you really want to undo what module-assistant did, just uninstall the package alsa-modules-<*your kernel version here*>.
You'll find it in synaptic under "Installed packages (local or obsolete)".

---

### Post by TopRamen on 2008-05-11
> **jocko said:**
> If you really want to undo what module-assistant did, just uninstall the package alsa-modules-<*your kernel version here*>.
You'll find it in synaptic under "Installed packages (local or obsolete)".

After I uninstall it, how do I restore Ubuntu to what it had by default as far as sound modules go? Is there a package I'll need to re-install? Basically, what exactly does module-assistant do? I understand it re-compiles modules but does it replace and detach a package from aptitude? Thanks!

---

### Post by jocko on 2008-05-12
> **TopRamen said:**
> After I uninstall it, how do I restore Ubuntu to what it had by default as far as sound modules go? Is there a package I'll need to re-install? Basically, what exactly does module-assistant do? I understand it re-compiles modules but does it replace and detach a package from aptitude? Thanks!

I don't think it replaces anything, so uninstalling the package i told you about should get everything back to the way it was before.
If that didn't work, maybe reinstalling the kernel and all installed alsa packages will work.

---

