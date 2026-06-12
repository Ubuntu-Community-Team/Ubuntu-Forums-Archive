---
title: "Clean up boot options"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Polyjuice on 2009-10-17
Ubuntu newbie here...  
 

 I have created a situation that is a concern, which perhaps I should ignore – I just like things tidy. Here's how I got where I'm at:
 

 
[LIST]
[*]Took a XP, Pentium 4, 2gb memory     and installed a secondary HD
[*]Installed Ubuntu 9.04 and duel     booted - Worked great
[/LIST]
 

 Ubuntu was everything I thought it would be so I decided to make this my dedicated Ubuntu machine. So I removed the secondary HD and installed Ubuntu on the primary drive. Everything still works great, expect;
 

 I don't need all the options offered at start-up (boot) time -  it still shows the other operating system on /dev/sdb1 which no longer exists.
 

 How do I clean up the boot procedure?

---

### Post by mikewhatever on 2009-10-17
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup && sudo update-grub
```

The above command should backup the current boot menu and then regenerate it according to the currently available boot options. If it doesn't solve the problem, you could edit it manually. If in doubt, please post the content of the menu.lst here.

---

### Post by mac9416 on 2009-10-17
A jolly good howto: [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

---

### Post by oldfred on 2009-10-17
From synaptic you can download startup manager.

Under advanced you can set the number of kernels to show to 2. You want two just in case a new download does not work.

You can also set all that in menu.lst but simple changes are easier in startup manager.

---

