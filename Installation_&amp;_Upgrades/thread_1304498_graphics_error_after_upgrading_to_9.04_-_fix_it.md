---
title: "graphics error after upgrading to 9.04 - fix it?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by eskararriba on 2009-10-29
hi everyone, 

I just upgraded from 8.10 to 9.04, and will upgrade to 9.10 today. there's been problems with the upgrade to 9.04, and I'm not sure if I should fix them before upgrading to the new release, or just upgrade and fix everything afterwards. 
thing is: when booting into 9.04, I get an error message: "there already seems to be a X server running on display :0. Should another display number be tried?"

in ubuntu, I then installed the 180 NVIDIA driver (thought it might help), but now I got a lot of error messages when booting

(EE)NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE)NVIDIA(0): that there is a supported NVIDIA GPU in this system and
(EE)NVIDIA(0): that the NVIDIA device files have been created properly
(EE)NVIDIA(0): +++Aborting+++
EE Screen(s) found, but none with viable configuration

as I said: should I fix it or just upgrade to 9.10 and see what happens? and, if I should fix it: HOW?

thanks for your help

---

### Post by lemming465 on 2009-10-30
I'd say fix things a bit first, then do the next upgrade.  I'd revert from the binary Nvidia driver back to the "nv" open source driver, and then run: ```

sudo apt-get update
sudo apt-get upgrade --fix-broken
```
and reboot before trying to upgrade further.

---

### Post by florus on 2009-10-30
If you have existing problems, a clean install is safer than an upgrade.

---

