---
title: "Vostro 1400 nvidia nightmare in latest Kubuntu x64"
date: 2008-07-03
forum: Hardware
---

### Post by kublewie on 2008-07-03
Hi,

My first foray into Kubuntu is a disaster.  Other linux distros (suse/arch) can install the nvidia drivers fine, so I know my card (8400) does work in linux.  I tried the hardware > enable acceleration option within KDE and restarted and then X refused to start.  I also tried 'envy' which resulted in the same thing.  Then when I tried to use envy to remove nvidia-glx-new apt gives an error and says it can't remove it.  Trying manually to remove it also gives an error.  So now I can't remove the old nvidia driver or try to reinstall it.  So goes my first experience with apt.

Does anyone have any ideas short of re-installing Fedora?

cheers,

kilolima

---

### Post by kublewie on 2008-07-04
solved. followed the not recommended advice of creating a fake symlink to /lib32

---

