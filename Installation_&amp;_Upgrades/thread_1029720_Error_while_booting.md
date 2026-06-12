---
title: "Error while booting"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Tykin on 2009-01-03
I'm having a very strange problem while booting xubuntu. When at the GRUB boot menu, I simply press enter to start xubuntu. However, if the timeout in the GRUB menu finishes, xubuntu will not start properly. 

Instead, the startup splash freezes and, after a bit, the machine will go into xubuntu but will be unresponsive (can't even move the mouse).

I tried changing the timeout to zero, but the same thing happened.

So, to restate: xubuntu will load perfectly fine if I press enter before the timeout completes. However, once the timeout finishes, xubuntu will not load properly.

Does anyone know why this is and how I can fix it? I'm installing this on a friend's computer, so I want her to be able to just turn on the computer and have it load into xubuntu without running into problems like these. I also don't want her to be bothered by the GRUB menu.

---

### Post by caljohnsmith on 2009-01-03
That does indeed sound like a really strange problem. In order to get a clearer picture of your setup, how about opening a terminal and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

