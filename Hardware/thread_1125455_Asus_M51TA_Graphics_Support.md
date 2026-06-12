---
title: "Asus M51TA Graphics Support"
date: 2009-04-14
forum: Hardware
---

### Post by prince_niceguy on 2009-04-14
I have the following graphics cards on my system. 

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

Recently I installed the fglrx from the repository (I am using jaunty). When the system boots up, X never comes up.

I had to revert back to open source radeonhd card.

Has any one else been successful in getting it working?

I am still hoping that will work some time...

---

### Post by soulsource on 2009-05-05
Got something four everyone who wants to help:
Installed the fglrx-driver from the Jaunty Repos, ran aticonfig --initial, booted up, attached is my Xorg.0.log here.

When disabling RandR 1.2 (see [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/347758/comments/14")), there are no errors in the Xorg.0.log, yet the screen just blanks when X is started (Xorg.0.log also attached).

I'll further try to get this working...

Edit: Seems it hangs when probing the Dev-ID 2:0:0 which corresponds to the HD3650 (when RandR 1.2 is disabled). Is there a way to tell X not to check a certain device-ID?

---

### Post by prince_niceguy on 2009-05-05
there is a bug in launchpad. you can put your inputs there. If there are no error in xorg.log then it should have worked... I have broken my head for more than a week or two over this, now have given up and using radeonhd for some time.

the bug is [there]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/360790")

---

### Post by b@sh_n3rd on 2009-05-05
> **prince_niceguy said:**
> I have the following graphics cards on my system. 

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

Recently I installed the fglrx from the repository (I am using jaunty). When the system boots up, X never comes up.

I had to revert back to open source radeonhd card.

Has any one else been successful in getting it working?

I am still hoping that will work some time...

Hi, you can try the proprietary drivers for Linux here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Just select the linux version on the first list on the left (x86 or x86-64, depends on your processor) and select Radeon on the next list ([If your 3200 is integrated, select "Integrated/Motherboard" and select Radeon HD 3200] Mobility Radeon for your other vid. card). Then select ATI Radeon HD 3xxx Series (OR, Mobility Radeon) and hit GO!...That oughta do it...

---

### Post by prince_niceguy on 2009-05-05
> **b@sh_n3rd said:**
> Hi, you can try the proprietary drivers for Linux here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Just select the linux version on the first list on the left (x86 or x86-64, depends on your processor) and select Radeon on the next list ([If your 3200 is integrated, select "Integrated/Motherboard" and select Radeon HD 3200] Mobility Radeon for your other vid. card). Then select ATI Radeon HD 3xxx Series (OR, Mobility Radeon) and hit GO!...That oughta do it...

thanks for the suggestion, but i have already tried this route. I have tried following ways to install fglrx.

1. from repository of ubuntu.
2. using ati driver from amd's site.

none of them work... ati seems to be doing very bad job when it comes to linux support. though it is improving the drivers still lag far behind when compared to their windows counter part..

---

