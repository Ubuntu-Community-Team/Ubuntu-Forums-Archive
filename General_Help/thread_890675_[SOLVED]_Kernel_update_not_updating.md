---
title: "[SOLVED] Kernel update not updating"
date: 2008-08-15
forum: General Help
---

### Post by Riffer on 2008-08-15
Just had a kernel update and did the reboot and Grub only shows the older one.  I'm now behind 2 kernel updates, how come?

---

### Post by rbmorse on 2008-08-15
When the update was running, you should have been presented with a dialog asking you what to do about a package that wants to "update a user setting" or something to that effect message. It's talking about GRUB here, although I can't remember if it actually mentions GRUB.

The default is to keep the existing user setting...which is why you still only have the old GRUB menu. If you pull down the selection menu the top option is to "Use developers version" and that is the one that updates grub.  

Not all is lost. Open a terminal window and enter:

sudo update-grub

supply your user password when asked. 

Enjoy!

---

### Post by drs305 on 2008-08-15
If you need to investigate the menu.lst, StartUp-Manager is a great gui app to tweak the settings. Menu.lst has settings for how many kernels to view, which one to use as the default, etc. 

View the tutorial listed in my signature line to read about the advantages of using StartUp-Manager and how to run it.

---

### Post by Riffer on 2008-08-15
> **rbmorse said:**
> When the update was running, you should have been presented with a dialog asking you what to do about a package that wants to "update a user setting" or something to that effect message. It's talking about GRUB here, although I can't remember if it actually mentions GRUB.

The default is to keep the existing user setting...which is why you still only have the old GRUB menu. If you pull down the selection menu the top option is to "Use developers version" and that is the one that updates grub.  

Not all is lost. Open a terminal window and enter:

sudo update-grub

supply your user password when asked. 

Enjoy!

Did that and nothing updated, weird.

---

### Post by Riffer on 2008-08-15
> **drs305 said:**
> If you need to investigate the menu.lst, StartUp-Manager is a great gui app to tweak the settings. Menu.lst has settings for how many kernels to view, which one to use as the default, etc. 

View the tutorial listed in my signature line to read about the advantages of using StartUp-Manager and how to run it.

Did that and the only OS it shows is the old Kernel.

Noticed that in the terminal window it says that Grub2 is not present?

---

### Post by drs305 on 2008-08-15
> **Riffer said:**
> Did that and the only OS it shows is the old Kernel.

Noticed that in the terminal window it says that Grub2 is not present?

There was another thread yesterday with pretty much the same issue. Just so I understand, the menu.lst option is howmany=all (or at least more than 1), and it is set up to automatically update the default boot option, and the new kernel is not being added to menu.lst? 

If you open StartUp-Manager and set/reset the Advanced/Automatically update default boot option to yes (ticked) it still doesn't add the new kernel?

Maybe time to file or search for a bug report...

---

### Post by Riffer on 2008-08-15
Well I fixed it by adding to my grub list manually a bit of a pain.  I'll look into a bug report.

Thanks for both your help.

---

