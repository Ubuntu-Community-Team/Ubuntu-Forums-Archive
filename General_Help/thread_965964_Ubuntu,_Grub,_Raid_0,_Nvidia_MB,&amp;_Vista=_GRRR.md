---
title: "Ubuntu, Grub, Raid 0, Nvidia MB,&amp; Vista= GRRR"
date: 2008-10-31
forum: General Help
---

### Post by spen25 on 2008-10-31
Hi all,

I have been trying to figure this out for the longest. I have three 500GB Sata Hard Drives in Raid 0 using the Nforce MB bios. I have Vista installed already. So I install Ubuntu (Intrepid) using DMRAID to access my Striped Partition, but after install it just reboots back into Vista. No Grub. What is the trick to get Grub working?? Thanks for any help.

---

### Post by cariboo on 2008-11-01
Have a look at this, It goes through every thing from creating the array to installing on it, including setting up grub.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Jim

---

### Post by spen25 on 2008-11-01
Of course it couldn't be easy. Still doesn't work, GRub cant find stage 1 :( I wonder why there can't be an easier way. Is Raid  that unnormal in Ubuntu?

---

### Post by fjgaude on 2008-11-01
Well, the raid that is on your motherboard is not designed to even work with anything other than Windows. So the **dmraid** program was created.

You will likely have to understand how grub works and then place the MDR on the drive that has grub on it. One way is to use these commands:

```
#sudo grub
grub> find /boot/grub/stage1
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
```

Then if necessary, out of grub and onto another command line:

```
sudo grub-install /dev/sda
```

You will have to determine what the drive names are. Much to learn here. What you are doing is not that popular for the Linux developers to have made it put buttom, but everything is here to learn how to do it.

Let us know how you are doing.

---

