---
title: "wrong audio device laptop hotkeys (Feisty beta)"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by -=Ghostlike=- on 2007-04-15
Hi, Ubuntu has always been the only distro where my audio hotkeys work (on a Fujitsu Amilo Pa1510 laptop).

But now I have installed the Feisty beta and the hotkeys are mapped to the wrong device (CD instead of PCM), I changed my gnome-applet to PCM and deleted every other item from the volume Control. but it still uses CD.

My soundcard is a ATi branded Realtek ALC861 snd-hda-intel device.

thanks in advance

---

### Post by schaumkeks on 2007-10-20
I know this is old, but I stumbled upon it while searching for a solution to the same problem. After upgrading to Feisty the keyboard hotkeys didn't control the volume of my soundcard. In fact they controlled the "Front" track, which only affected the headphone volume.

As Ghostlike already stated, setting the correct track in the preferences dialog of the Gnome Volume Applet only affects what volume is changed by the single slider of the Volume Applet (left click) and not the volume controlled by the hotkeys.

The Solution is pretty simple: There is the dialog System->Preferences->Sound, and on the first tab "Devices" you have to choose the "Default Mixer tracks", e.g., Device HDA-Intel and track PCM.

Don't know why I didn't found this earlier.
Bye, Sven

---

### Post by mcwizard on 2007-10-23
Thats great, I've been searching for a solution for a couple hours for Gutsy and it was looking pretty hopeless.  

Thanks for the nice find, the control/setting for this does need to be a little more intuitive.

Like schaumkeks  said, just go System->Preferences->Sound, and on the first tab "Devices" you have to choose the Default Mixer tracks, just highlight the mixer track you want your hotkeys to control and click ok.  Works great for me.

---

