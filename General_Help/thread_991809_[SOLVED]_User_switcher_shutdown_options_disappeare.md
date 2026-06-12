---
title: "[SOLVED] User switcher shutdown options disappeared"
date: 2008-11-24
forum: General Help
---

### Post by ianhaycox on 2008-11-24
After upgrading from Hardy to Intrepid the shutdown/suspend/hibernate options have disappeared from the User Switcher menu. See attached screenshot.

Originally after the upgrade all the options were there, even after selecting the option to combine the shutdown and user switcher menus. However selecting Logout left me with a black screen and an unresponsive system. The only alternative was to use ctrl-alt F1 to login to a command prompt and shutdown.

Surfing revealed that forcing a re-install of the fast-user-switch-applet might fix the problem. It didn't, it made it worse. Logout still doesn't work, switch user fails with an error 'Graphical System error' and the shutdown/hibernate/suspend options have disappeared. See report at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/288066](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/288066)

Under Hardy I trained the kids to use the user switcher to login to their own limited accounts to surf/play games etc. and it worked prefectly. Now I get constant calls of 'Dad... it's broke again'.

Anyone got any ideas on how to fix this ? It would be nice not to scare the kids to the dark side.

BTW - Gnome and NVidia 177

Thanks,

---

### Post by ajgreeny on 2008-11-24
I have a suspicion it's now in the **Deskbar** applet in your panel.  If you have that enabled have a look there, if not add it to your panel and have a look again.  If not you can certainly get it in one of the applets on the panel, as I have already done so.  I'm not on intrepid at the moment, so can't look for it or how I did it but it is possible, I know that for certain.

---

### Post by ianhaycox on 2008-11-24
I added the Deskbar applet, but still no change. Even going through preferences and adding 'Computer Actions' didn't help. Nothing extra showed up in the Deskbar applet and no change to the user switcher applet :-(

---

### Post by plucky on 2008-11-24
Try adding the **Logout** green running man applet from the "Add to Panel" menu.That has the "Switch User" button on my Intrepid.


Good Luck

---

### Post by ianhaycox on 2008-11-25
I added the Logout applet to the panel but it only gave me two options, Logout and Switch user. No Shutdown options.

I did notice that under the System menu there is a Shut Down... option, but that only gives me a Shutdown or Restart. No Suspend or Hibernate.

Any other ideas ?

It would also be nice to get the Switch User function to actually work like it did in Hardy.

---

### Post by CatKiller on 2008-11-25
If you open ```
gconf-editor
``` and look for the **/apps/gnome-power-manager/general/can_hibernate** key, is it ticked?

Similarly, with the **/apps/fast-user-switch-applet/show_session_commands** key.

---

### Post by ianhaycox on 2008-11-25
can_hibernate and can_suspend are ticked already

show_session_commands is ticked already

Rather bizarrely shutdown/hibernate/suspend were not there this morning after a reboot. I checked. After running gconf-editor the options appeared in the user-switcher without changing any settings.

Just running gconf-editor seems to have restored the missing options.

It would seem re-installing fast-user-switch-applet did not honour the gconf settings.

Thanks everyone.

---

### Post by CatKiller on 2008-11-25
Freaky, but I'm glad it's working for you now.

---

### Post by tsb47 on 2009-07-27
I had a similar problem. The shutdown, restart, hibernate and suspend options disappeared from my Intrepid release FUSA. 

The cause was that I had unticked "Power Management" from the list of my start-up options in the sessions dialog of the administration menu. Ticking this option, fixed the problem - my shutdown etc options came back into FUSA.

(Unticking unused auto-start programs had been suggested as a way of optimizing boot up in an Ubuntu book I'm reading),

---

