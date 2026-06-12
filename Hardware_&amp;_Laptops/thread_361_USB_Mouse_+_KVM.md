---
title: "USB Mouse + KVM"
date: 2004-10-13
forum: Hardware &amp; Laptops
---

### Post by tambooki on 2004-10-13
Well, after finally managing to configure my Logitech mx700 properly, so that all the buttons work, I've run into a new problem. Previously, I ran with the "ExplorerPS/2" protocol in my XF86config, but changed that to "evdev" in order to get all the buttons functioning correctly. With the old config, the mouse worked w/o problems on my belkin kvm; having switched to the new config, however, means that my mouse stops responding whenever I switch away and back. The keyboard, also usb and also on the kvm, responds fine, just the mouse is dead. Well, in Gnome anyway. 'cat'ing the device shows activity as I move the mouse, it's just the pointer on screen doesn't move. Switching to a console and back fixes the problem, but I'm not sure what has caused this change. Any suggestions?

---

