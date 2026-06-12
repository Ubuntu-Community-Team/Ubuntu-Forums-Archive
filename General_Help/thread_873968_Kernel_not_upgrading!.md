---
title: "Kernel not upgrading!"
date: 2008-07-29
forum: General Help
---

### Post by Zigi15 on 2008-07-29
Hello! I am using ubuntu Hardy with the 2.6.24-17 kernel. My update manager fetched me some new kernels and installed them, but i cannot get them on the grub boot menu. sudo update-grub claims to find the newer installations and update menu.lst, but nothing happens really.

---

### Post by mordak13 on 2008-07-29
Have you checked you menu.lst file directly? 

cat /boot/grub/menu.lst

or 

nano /boot/grub/menu.lst

to edit it. But if they are listed then they should come up as an option when you reboot the PC. Also maybe check that the meta packages for the kernels are checked in Synaptic so you get the upto date kernels for generic or i386 or what ever kernel you run.

---

### Post by drs305 on 2008-07-29
Open StartUp-Manager and see what the default kernel is. Depending on how it is set up, menu.lst may install the newer kernels but not use them until you manually make the change. In Boot Options you can select the default kernel/OS. The number of kernels may currently be set to 1, in which case you wouldn't even see the new kernels on the menu.

```
sudo aptitude install startupmanager
```

To run: System, Administration, StartUp-Manager.

Links to a StartUp-Manager tutorial are in my sig line and can answer most of your questions about setting the options of grub's menu.lst.

---

