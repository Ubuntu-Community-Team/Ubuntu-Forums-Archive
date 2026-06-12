---
title: "need some help"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by andyman222 on 2007-08-09
ok so, ive been using ubuntu on my hp laptop for a while now and theres not been too many major issues till now. i decided to upgrade the kernel to 2.6.22 last night and now things have gotten messy. first of all, i have no control over the volume anymore. its permanently at max volume, and i cant change it. also lirc gpio isnt working which is a known bug, but i dont know if that has anything to do with the volume issue. also, i dont know if this could be something to worry about or not, but whenever i turn the computer on to the login screen the screen goes teal for a second before letting me type in my username. the box that appears after typing in your username and password (the one thats displayed when the start up music plays) is no longer there for some reason. and one last thing, which isnt so much a big deal to me, whenever the computer is restarted in order to get the internet to work (set to a static ip)  i have to go into the network tools  and switch to dhcp and then back to the static ip (dhcp doesnt work). and im a little clueless as to how to go about downgrading the kernel if it comes to that. thanks in advance.

---

### Post by crhumber on 2007-08-09
How did you configure the kernel before you compiled it?  I just compiled kernel 2.6.22 and what I did was to save the configuration of my old kernel and load it into the configuration editor...that way almost everything is exactly as it was before.  All I do from there is to make some tweaks that I want/need and then do the rest.  I don't know if that helps but these are the instructions I followed:

[http://www.howtoforge.com/kernel_compilation_ubuntu_p2?]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2?")

Hope this helps.

---

### Post by andyman222 on 2007-08-10
when i compiled the kernel i used this site [http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html](http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html)
right now im back on 2.6.20-16 and everything seems normal again, but im not really sure what went wrong when i tried upgrading.

---

