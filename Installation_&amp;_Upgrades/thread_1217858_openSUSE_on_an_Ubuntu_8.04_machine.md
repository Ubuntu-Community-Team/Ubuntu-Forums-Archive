---
title: "openSUSE on an Ubuntu 8.04 machine"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2009-07-20
I messed up and installed penSUSE 11 in a 12 gig partition and I am unable to fix my MBR with the live CD and I have tried 2 separate methods I found on the web using the Live CD.  In neither method could I find /boot/grub/stage1.  I have a single 80 gig hdd and I really want to go back on the ubuntu grub menu.

Any help?

---

### Post by mick222 on 2009-07-20
you'll need to fix grub in suse find thee entry for ubuntu and add it to menu 1st.

---

### Post by th1bill on 2009-07-20
> **mick222 said:**
> you'll need to fix grub in suse find thee entry for ubuntu and add it to menu 1st.

I have the SUSE menu and it lets me load ubuntu but my primary system is ubuntu and I only installed SUSE for testing purposes.  I really do regret having agreed to test it but that does nt ive me the grub menu I desire to bot from but thanks.

---

### Post by swerdna on 2009-07-20
> **th1bill said:**
> I have the SUSE menu and it lets me load ubuntu but my primary system is ubuntu and I only installed SUSE for testing purposes.  I really do regret having agreed to test it but that does nt ive me the grub menu I desire to bot from but thanks.
OK then load Ubuntu and reinstall Grub to the master Boot Record of the hard drive from there. That will knock out the booting to openSUSE but if you want to then edit an entry for openSUSE into the Ubuntu loader, here's how:

[HowTo Boot / Multiboot openSUSE from the Ubuntu GRUB bootloader]("http://ubuntu.swerdna.org/ububootsuse.html")

Now, about getting Grub from Ubu into the MBR once you've booted into Ubuntu:
Suppose the root partition for Ubuntu is on sda3 which in grub speak is (hd0,2)and that you don't have a specially made, separate root partition. I'll use that (hd0,2) as an example. Change what I say to match where your root partition really is.

Open a terminal and enter this: ```
sudo grub
```
you'll get the grub prompt: grub>
hen enter this: root (hd0,2)
then enter this: setup (hd0)

If you can't figure out your version of (hd0,2) then enter this at the grub prompt first: ```
find /boot/grub/menu.lst
```You should get two answers (one for Suse one for Ubuntu). Ubuntu should be the first of them because it was on the drive earlier.

---

