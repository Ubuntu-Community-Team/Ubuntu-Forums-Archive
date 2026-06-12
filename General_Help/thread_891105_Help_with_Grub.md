---
title: "Help with Grub"
date: 2008-08-15
forum: General Help
---

### Post by Halcyon31415 on 2008-08-15
Hello,
   I'm a new user. I was wondering if someone could help explain some things about Grub. It seems that I/Ubuntu periodically adds new operating systems to the boot screen.

1) Is it possible to permanently delete some of the options so I don't have such a big list. I have found the Delete option but it doesn't seem to do anything. Hopefully thats not a symptom of a larger problem.

2) Is it possible to rearrange the order. It's a small problem but I would like to be able to power the computer on and come out of the shower in the morning and have it all booted up into the right system.


    Thank you so much for your help.

Cheers.

---

### Post by mikewhatever on 2008-08-15
Those aren't operating systems, but kernels. You can easily uninstall (search for linux-image) the unneeded ones from synaptic package manager. Grub's menu will get updated in the process.
Do make sure to leave the latest kernel installed.

---

