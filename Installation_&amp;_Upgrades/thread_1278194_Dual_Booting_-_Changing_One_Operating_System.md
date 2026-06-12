---
title: "Dual Booting - Changing One Operating System"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by alindgr1 on 2009-09-29
I love Ubuntu, and I would like to stay with it, but I would also like to try other distros.  What I would like to do is install Ubuntu and then install another OS, OpenSUSE for example.  I know that this will work.  But, after that, I would like to be able to remove OpenSUSE, and install a different OS in place of it.  I know I can do it without removing Ubuntu, but will GRUB recognize the changes, or will that be wiped out and I lose the ability to start Ubuntu?

:confused:

---

### Post by presence1960 on 2009-09-29
> **alindgr1 said:**
> I love Ubuntu, and I would like to stay with it, but I would also like to try other distros.  What I would like to do is install Ubuntu and then install another OS, OpenSUSE for example.  I know that this will work.  But, after that, I would like to be able to remove OpenSUSE, and install a different OS in place of it.  I know I can do it without removing Ubuntu, but will GRUB recognize the changes, or will that be wiped out and I lose the ability to start Ubuntu?

:confused:

what you want to do when you install the other distro is install GRUB on the partition you are installing to. You may have to look at the installer to figure out how to do it, but that is what you want to do. You do not want to put GRUB on MBR as it will overwrite your Ubuntu GRUB.

Once that is accomplished you can chainload the new distro from Ubuntu's GRUB by editing Ubuntu's menu.lst by adding the new distro's entry like this:

```
title         <distro name>
rootnoverify  (hdx,y)
chainloader   +1


```

when you select that when Ubuntu's GRUB menu comes up it will point to the new distro's GRUB (which you installed on the new distro's partition) and bring up that distro's menu.

this has a decided advantage as when kernels are upgraded the new kernel entries are only added to that distro's menu.lst. You will not have to edit Ubuntu's menu.lst to include the other distro's new kernels since they will already be on that distro. Chainloading is the best & easiest way to go with multiple OSs on GRUB.

---

### Post by alindgr1 on 2009-09-29
Sweet, thanks!  I'll give it a shot.  Sounds easy, overall.

---

### Post by alindgr1 on 2009-10-13
Sorry it has taken a while, I was on leave, and did not get on here much.  But, I tried your suggestion, and it worked perfectly.  Thanks much. :P

---

### Post by presence1960 on 2009-10-13
> **alindgr1 said:**
> Sorry it has taken a while, I was on leave, and did not get on here much.  But, I tried your suggestion, and it worked perfectly.  Thanks much. :P

Glad to hear you got it working.

If no one else has told you I want you to know I appreciate your service to our country! Thank you.

---

### Post by alindgr1 on 2009-10-13
You are all welcome, and thanks for the thought.

---

