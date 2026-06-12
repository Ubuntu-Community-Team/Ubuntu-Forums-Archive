---
title: "USB mouse not working in Jaunty"
date: 2009-06-25
forum: Hardware
---

### Post by brainsonfire on 2009-06-25
Model is a Targus AMU2601EUK.

It only works for a split second everytime i plug it in. I tried it on 2 different laptops, both with fresh installs of jaunty, but on a gutsy desktop it works just fine.

When i plug it in i see 2 input devices being added in /var/log/messages and /var/log/Xorg.0.log, the first one being recognized as a mouse, second one as a keyboard by xinput. Is that normal?

lsusb also shows the device, but a cat on the corresponding events, mouse* or mice files gives me nothing.

any ideas?

---

### Post by brainsonfire on 2009-07-16
its a kernel issue, its been fixed in 2.6.30.1.


i downloaded the 2.6.30.1 kernel from kernel.org then followed this guide from step 3 [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

that solved it for me.

(note to nvidia ppl: if dpkg complains about nvidia-common during postinstall, ignore it. after reboot just reinstall the driver)

may the ubuntu be with you

---

