---
title: "ubuntu missing from boot option,Please help me."
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by ravi_buz on 2009-05-30
I have ubuntu 9.04 installed in one HDD and tried to install opensuse in another ,But now i see only opensuse in the boot option.I want to remove it and have only ubuntu.So i formatted my HDD which has suse but still i see only suse in boot option 

grub> find /boot/grub/stage1
(hd0,3)

grub> root (hd0,3)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,3)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


its done but i am unable to see it boot yet 

:(:(:(:(:( Help me

---

### Post by ravi_buz on 2009-05-30
[http://lh3.ggpht.com/_4yjIsf_5Rew/SiC977TLY7I/AAAAAAAAAj8/UxGWHmXf_d4/s400/Screenshot.png](http://lh3.ggpht.com/_4yjIsf_5Rew/SiC977TLY7I/AAAAAAAAAj8/UxGWHmXf_d4/s400/Screenshot.png)

Thats the pic of my partions but i am unable to mount my partition which has ubuntu in it

---

### Post by ravi_buz on 2009-05-30
[attach]115687[/attach]

---

### Post by presence1960 on 2009-05-30
this is the 3rd post on this same subject I have come across on the forum. You have to be patient. This is not paid support. We all do this on our spare time and are not compensated. You may not have your problem solved as quickly as you would like, but that is a fair trade off for not having to pay for a service.

P.S. I already saw that a moderator alerted you to not make duplicate threads on a topic, but then I ran across this one.

---

