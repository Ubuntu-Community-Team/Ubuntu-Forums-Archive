---
title: "upgraded to 9.10 from 9.04,now it won't boot"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by beawareofman on 2009-11-03
Hi. I am very new to ubuntu linux,so if a solution is possible,please put it in laymans terms.

Now to the case.

I had ubuntu 9.04 installed on my laptop (no dual boot, just ubuntu) and it worked fine. I had the possibility to upgrade to 9.10, so I clicked the "Upgrade" button and all went fine until the system needed to reboot.
  
This is what it says now: "Boot from (hd0,0) ext3" and the systems hangs kinda. 

I can now only access GRUB, but I am clueless....any ideas?

[edit] I dont have a startup disk, since I upgraded from within the system.

---

### Post by beawareofman on 2009-11-03
bump, I really need help on this one, I cant figure it out.

---

### Post by beawareofman on 2009-11-03
bump,how do I know which type of ext I have? See above posts, but ubuntu 9.10 is trying to start with ext3, is the problem that I have ext4? If so how do I change that? I can only acesss GRUB...

---

### Post by akelsall on 2009-11-03
I never attempted an upgrade the way you did. I never felt comfortable doing it that way (I always booted to a LiveCD and upgrade from there). 

If you can at least get some type of console going, take a look at boot/grub/menu.lst and look towards the bottom. It should have what appears to be menus (one will tell it to boot to the main kernel, another into recovery mode, etc). You might verify that the kernel mentioned in this section matches the kernel you're upgrading to. I'm not sure if 9.04 and 9.10 use different kernels or not (I know there was a change from 8.10 to 9.04). 

I don't know how to tell what file system you're using without running gparted (which I know you can't get to at this time). Maybe others will have some ideas.

Andy

---

### Post by beawareofman on 2009-11-03
I found a way to get into recovery mode,from here i can access root menu, but then what do I do? I stilldont know whats wrong or how to boot my system.

---

