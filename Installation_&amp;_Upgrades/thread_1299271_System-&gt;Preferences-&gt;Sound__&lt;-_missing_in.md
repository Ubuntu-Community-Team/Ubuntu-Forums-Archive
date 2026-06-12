---
title: "System-&gt;Preferences-&gt;Sound  &lt;- missing in 9.10?"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2009-10-23
Hi,
I get 68,000 Google hits on "ubuntu system preferences sound". I see many references to "System->Preferences->Sound". I seem to remember it on my 9.04 install. On 9.10, system -> preferences jumps from screensaver to startup_applications, skipping where sound should be. I also seem to recall a main_menu item somewhere where one could turn on and off stuff in the system level menus. I can't find it either. 

I am sure there was no option to hide_menu_items and I know I would not have opted for it. 

The sys -> pref -> volume_control pops up a window saying "waiting for sound system to respond" and it never does. 

Firefox plays bbc and kut-> npr fine and bbc and hulu videos also work perfectly so the sound system works. 

How do I find the missing menu items?

    BrianP

---

### Post by Cybie257 on 2009-10-23
My first thought is it could've been removed during your last update. Try performing another update and see if it returns. I have had a few things come and go between updates. If that doesn't resolve it, then (and maybe try first), right click on the system menu item and select Edit Menus. Scroll down to the preferences section and see if 'sound' is checked 9or even available). 

-Cybie

---

### Post by brianpatrick on 2009-10-23
Cybie,

I ran update_manager again, it found a few, I updated and now am fully current. No change in the menus. 

>>right click on the system menu item and select Edit Menus<<
On the upper left, Applications__Places__System, this System, I have prefs, admin, control_center, help and about ubu/gnome. Edit menus is gone in 9.10. 

But Wait! Under sys -> control_centRE (?), there is a "main_menu". Under system -> pref, there is a list of items that look suspiciously like the main menu items. Unfortunately, SOUND is missing (screensaver -> startup). The only item unchecked is 'multimedia_systems_selector'. What the heck is that? Why is it the only thing unchecked? Hmmm... 

I turned on the multimedia systems selector and started monkeying with the various options: OSS and autodetect work for default output. ALSA and pulse are silent. They all fail to open the device when I have Hulu in Firefox, even if it is not playing. In windoz, everything just screams over everything else. I actually prefer the cacophony to one-at-a-time order. At least if you can hear who is screaming over you, you know who to shut up. 

The bottom line is that some genious architect changed the name/location of the menu items, changed the functionality from sound to multimidia and then hid it from view so you had to alter the default install to have any access to either sound or video preferences.

This points to a 100% lack of testing because one could not even access the sound menu item without first performing system brain surgery. Talk about shooting from the hip! This is a FINAL RELEASE CANDIDATE, not a playpen or alpha build!

Another real bug, the multimedia system selector app suddenly disappears. Rerunning it shows a blank window with no controls. Nothing to work with and no crash data to report. Perhaps a reboot (think sindoz 3.1) will fix it. ;)

Even though it does not quite work right, at least we now know where they hid the new controls. There is progress. 

Growing pains (ouch!),

    BrianP

---

### Post by Cybie257 on 2009-10-23
> **brianpatrick said:**
> 

>>right click on the system menu item and select Edit Menus<<
On the upper left, Applications__Places__System, this System, I have prefs, admin, control_center, help and about ubu/gnome. Edit menus is gone in 9.10. 

But Wait! Under sys -> control_centRE (?), there is a "main_menu". Under system -> pref, there is a list of items that look suspiciously like the main menu items. Unfortunately, SOUND is missing (screensaver -> startup). The only item unchecked is 'multimedia_systems_selector'. What the heck is that? Why is it the only thing unchecked? Hmmm... 


    BrianP

I'm using 9.10 right now, and it's there. I think you forgot to "RIGHT-CLICK" over the menu items (Applications <> Places <> System). When you right-click over them, you get a menu with "Edit Menus"

Try that again and let me know if that's what you did because it doesn't sound like it. 

And, yes, growing pains, but that's what we pay for when we use Alpha/Beta/RC versions. :-)

-Cybie

---

### Post by brianpatrick on 2009-10-24
Cybie,
I did discover the menu editing features. Moving the "sound" controls to "multimedia" and then hiding the multimedia in the menu confused me. I made it visible and am attempting to get my usb headset going. 

Thanks 4 your help,

    BrianP

---

### Post by egabriel on 2009-10-30
Hi,

I've just upgraded to 9.10 from 9.04 and System->Preferences->Sound disappeared for me as well and  I can't find it in "Edit Menu" dialog.
Any idea?

BTW: what's the command behind this menu item?

---

### Post by jeff124578 on 2009-11-05
System > Preferences > Sound is also missing on my 9.10 after upgrading from 9.04.  Not listed in the "Edit Main Menu" dialog either.  How can I get this back?

I do notice, btw, there's a "Sound Preferences" option by right clicking on the volume control in my bottom-right panel.  I think this might be the same Sound Preferences I'm looking for (I forget what the dialog contained in previous Ubuntu versions).  But even this contains precious few options to customize the various sounds for Ubuntu, e.g. logging in, logging out.  It only gives an option for the "Alert" sound.

---

