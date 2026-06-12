---
title: "ubuntu won't boot after upgrading kernel"
date: 2008-07-23
forum: General Help
---

### Post by buksnatata on 2008-07-23
after upgrading kernel to version 2.6.24.20-generic ubuntu won't boot on that version of kernel on version 2.6.24.19-generic boot it's normal what can be problem?

---

### Post by sports fan Matt on 2008-07-23
Its a known issue..just wait it out and it should be fixed evetually

---

### Post by drs305 on 2008-07-23
Matt is right that there are many users are having problems with booting 20 but some aren't. If you want to do a bit of troubleshooting instead of waiting for a fix:

Did you select 20 during boot from grub's menu.lst?  Otherwise you may have settings that use the last used kernel or a specific kernel designated for startup. If you have StartUp-Manager installed, run it and check the boot options to see which kernel is set as the default. You can change the default kernel to your choice.

If you don't have StartUp-Manager, install it with 'sudo aptitude install startupmanager' and then run it via System, Admin, Startup-Manager.

If you prefer to check menu.lst manually, you can look at the 'default' value and also check for a 'savedefault' setting. I'd recommend Startup-Manager though...

---

### Post by buksnatata on 2008-07-23
yes i had tryed that but also same computer just freeze notting i will just wait fix

---

### Post by buksnatata on 2008-07-29
after today patch all it's ok and i think that this new kernel it's a little bit faster than 2.6.24-19

---

