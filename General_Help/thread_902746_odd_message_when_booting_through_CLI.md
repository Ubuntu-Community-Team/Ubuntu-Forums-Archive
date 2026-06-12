---
title: "odd message when booting through CLI"
date: 2008-08-27
forum: General Help
---

### Post by malachi1990 on 2008-08-27
So I had some troubles with my NVIDIA Geforce 7150 graphics card (even created a custom module to get my dual screen working, but that failed after a reboot :(  ).  When I disabled gdm in order to install the driver, and I see this:

kinit: name_to_dev_t(/dev/disk/by-uuid/6a0c9de9-cb98-9fca-b293-07fd5a05daa4) = sda5(8,5)

kinit: trying to resume from /dev/disk/by-uuid/6a0c9de9-cb98-9fca-b293-07fd5a05daa4

While I can ignore this by diabling my NVIDIA driver in the linux-restricted-commons conf file (I think it's this one at least), this cant be a permanent solution as I need 2 displays.

I have zero idea what this means.  Any help would be greatly appreciated

---

### Post by phidia on 2008-08-27
I didn't google the terminal output but if you delete the uuid#'s I'm sure you'll get hits.
The guide [here]("http://ubuntuforums.org/showthread.php?t=885015&highlight=TV+monitor") may help you in setting up dual displays.

---

