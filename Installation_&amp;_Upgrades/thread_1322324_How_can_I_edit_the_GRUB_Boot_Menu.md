---
title: "How can I edit the GRUB Boot Menu?"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Ichido on 2009-11-10
I've installed Karmic 9.10 and it is working.
How can I edit the GRUB Boot Menu's List which now has 9 different Kernels?
I can't find the menu.lst to edit.


grub-install (GNU GRUB 1.97~beta4)

---

### Post by mechro on 2009-11-10
Grub2 doesn't use menu.lst.

Since I'm still using old Grub the best I can do is give you a link...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Ichido on 2009-11-10
I'm using GRUB 1.97~beta4.

---

### Post by roadracer on 2009-11-10
I have the same question.  I want to change the default boot distribution because I multi-boot, but there is no menu.lst file in Karmic Koala 9.10.  A reply by anyone with the answer would be greatly appreciated.  Thanks!

---

### Post by witeshark17 on 2009-11-11
Are you able to F2 to the BIOS to interrupt boot up? There you can type 'e' or 'Ctrl e' to edit AFAIK.

---

### Post by Ichido on 2009-11-11
> **witeshark17 said:**
> Are you able to F2 to the BIOS to interrupt boot up? There you can type 'e' or 'Ctrl e' to edit AFAIK.

I can type "e" to stop grub from booting and I can enter the Edit Mode but I can't save my changes!?
"F2" puts me into the Edit BIOS.

---

### Post by paulb42 on 2009-11-11
Install StartUpManager from the repositories and run it. It allows you to set the default

---

### Post by mechro on 2009-11-11
> **Ichido said:**
> I'm using GRUB 1.97~beta4.

I know it's odd and illogical but that is Grub2 which doesn't have a menu.lst file. You have to run Grub scripts to edit the grub.cfg file which has replaced menu.lst

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by timos_m on 2009-11-11
mechro is right. See his/her link :)

---

### Post by Ichido on 2009-11-12
> **paulb42 said:**
> Install StartUpManager from the repositories and run it. It allows you to set the default

Startup Manager does nothing.
I set the "default" System and changed the 10 second timer to 2, but it did not change anything.

---

### Post by Ichido on 2009-11-12
> **mechro said:**
> I know it's odd and illogical but that is Grub2 which doesn't have a menu.lst file. You have to run Grub scripts to edit the grub.cfg file which has replaced menu.lst

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I tried the Edit Grub instructions but again, no change.
I guess I'll give up for now.
Thanks anyway.

---

### Post by mechro on 2009-11-12
Are you trying to reduce the number of kernels shown in the boot menu?
Start Up Manager can do that (if it's working!)...

[https://help.ubuntu.com/community/StartUpManager#Security](https://help.ubuntu.com/community/StartUpManager#Security) / Advanced

---

### Post by Ginsu543 on 2009-11-13
When I tried using Startup Manager with grub2, it totally messed up my grub2 so that it wouldn't function properly afterwards. I had to reinstall to get full grub2 functionality back.

---

### Post by ShadowMage on 2009-11-13
When I first installed Ubuntu 9.10, I had a similar problem where StartUp-Manager would not do anything. But then I realized that you need to install the grub2 package inside Ubuntu 9.10 to make it work with grub 2. (Otherwise, it seems to think you're using grub legacy and sends commands that don't work for grub 2, although I'm not actually 100% sure what happens behind the scenes)

Just type this command in terminal, and then StartUp-Manager should work with grub 2.
```
sudo apt-get install grub2
```

---

