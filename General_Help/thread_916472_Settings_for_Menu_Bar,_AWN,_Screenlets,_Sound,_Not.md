---
title: "Settings for Menu Bar, AWN, Screenlets, Sound, Not Saving"
date: 2008-09-10
forum: General Help
---

### Post by boolean2 on 2008-09-10
After customizing my desktop, I reboot and all of my settings are all gone.

1- I set the main menu bar to not expand and to be transparent.  After reboot, it stays not expanded and transparent, but goes to the bottom of my screen.  When I try to set it to the top, it doesn't allow it.  I first have to click expand, then top.  Then I can uncheck expand.

2- After adding icons to AWN Avant Window Navigator, I reboot and everything I added disappears.  Looking at the preferences, it shows the gear logo for each launcher, but the details when clicking edit are blank.  If I click on each to remove, they don't remove.

3- I customize my screenlets, I reboot and for some reason, one of the screenlets, the clock shows up in the upper-left of my screen, not the screenlets I select.

4- I turn off the Sound for login/logout and disable system sounds and they play on reboot.

Am I missing something or are these issues all known?  Re-install of 8.04?

Anyone have any clue?

Thank you!

---

### Post by boolean2 on 2008-09-13
bump   --   anyone?

---

### Post by kokkus on 2008-09-13
Seams like ther eare some location problems to your home directory.

TRy these codes in terminal (change "username" to your own)

sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

Now reboot, login and change your settings.
Login again (CTRL+ALT+Backspace), and see if your new settings are taking place now.

Good luck:)

---

### Post by boolean2 on 2008-09-13
kokkus,
I ran those and verified the settings after.

1-Permissions on .drmc are correct.  I own .drmc.
2-My home dir. is 755. I own my home dir.

Still...no luck!  :-(

Any more thoughts?  I would rather not re-install.  This is a pretty fresh install with all the latest updates.

---

