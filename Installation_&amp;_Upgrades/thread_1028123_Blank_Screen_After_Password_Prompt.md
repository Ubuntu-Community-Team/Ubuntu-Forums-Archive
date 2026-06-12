---
title: "Blank Screen After Password Prompt"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by bigbaraboom on 2009-01-02
Hello everyone,
I finally decided to use a partition on my internal disk, as
the external one had problems loading GRUB. Anyway, i boot the
generic kernel and after a minute or two i am at the UBUNTU 
username prompt, with "Options" on the bottom left. I enter,
and get to the password prompt, i enter and i get a blank screen
with my mouse cursor able to move around, but no GUI. I've read
and read, but no one offers a step by step solution for an exact
fix. Any help will be greatly valued. Thank You.

---

### Post by bigbaraboom on 2009-01-02
I found a thread that had a line of code for "compiz"..
magic i'm in!! For anyone that has the same problem here is
the code..if it works please start your own thread with it
so we can keep this quick and dirty fix widely known. ;)
Code:
sudo apt-get purge compiz compiz-core
;;type it into the root of recovery mode if you cant access
the shell with Ctl-Alt-F1!

---

