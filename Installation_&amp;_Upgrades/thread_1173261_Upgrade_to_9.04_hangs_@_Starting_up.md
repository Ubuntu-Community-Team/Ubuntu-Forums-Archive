---
title: "Upgrade to 9.04 hangs @ Starting up"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Pgohara on 2009-05-29
I just tried to upgrade a toshiba satellite (2003 vintage) to 9.04. I didn't update everything on the current system before I did. It is on a dual boot XP/Ubuntu drive. When I restarted to finish the upgrade it hangs at Starting Up. I have to unplug and pull the battery to recover.
 
When I start in recovery mode it does a bunch of stuff on screen and then stops. The last message on the screen says:
[0.723204] PCI 000:02:02:0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 
And then it hangs. I have to unplug and pull the battery to recover.
 
The XP runs fine. Boots with Grub.
 
Any suggestions would be appreciated.

---

### Post by ronparent on 2009-05-29
From your grub menu on boot, select ubuntu (probablt rhw defauld), hit e to edit, select the kernel line and press e again to edit. Insert **noapic nolapic** separated by a tab where the boot defaults are near the end of the line. Hit return and then b to boot. If you can now boot ubuntu, you need those additional defaults. You will have to **sudo gedit /boot/grub/menu.lst** to make the changes permanent (the changes you made to the boot menu were only tempoary for that boot). I hope this fixes it for you (it did for me).

---

### Post by Pgohara on 2009-06-04
Thanks for the suggestion but it still hangs at Starting Up.

---

### Post by roaftech on 2009-06-04
Newbie (to Ubuntu) with probs!
I too have a Toshiba Satellite which, until yesterday was running Ubuntu 8.10 as its sole OS. I really wanted to use OpenOffice Base (not included in 8.10) so yesterday I upgraded the OS to version 9.04 using the built-in upgrade process - no problem so I then upgraded Open Office to version 3 - again no apparent problem although it did report some 1,120 files being changed!
However, today the machine won't boot up past the log-in screen. I enter username and password, then the screen goes blank apart from the cursor arrow, which does respond to the mouse.  The only option is to shut down - nothing else has any effect.
I can access certain of the boot-up menus, and tried the recovery option, but no difference.  If I interrupt the boot I can dir from one of the prompts and see my files but cannot do anything with them.
Any ideas, short of reinstalling 8.10 from a bootable cd?
 
Thanks,

---

