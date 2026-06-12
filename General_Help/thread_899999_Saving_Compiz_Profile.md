---
title: "Saving Compiz Profile?"
date: 2008-08-24
forum: General Help
---

### Post by Titan8990 on 2008-08-24
What I am trying to accomplish is being able to turn compiz off/on without losing my settings. I sometimes like to game on my Linux box (even though I keep Windows around for gaming) but I have issues with games losing full screen or crashing out when compiz is running.

So, does anyone know of a way I can:

a) save a profile of compiz setting so I can quickly restore my settings when I want to turn compiz back on

b) a way to have two desktop configurations (possibly different kernels or desktop types), one for gaming and another for development and general use

I appreciate any suggestions.

---

### Post by rainwalker on 2008-08-25
I've heard of something called fusion-icon that you can install via Synaptic that adds a little icon to your panel or something that gives you quick access to a lot of Compiz's controls, including turning it on or off; you could try that

---

### Post by ft23002 on 2008-09-27
> **Titan8990 said:**
> What I am trying to accomplish is being able to turn compiz off/on without losing my settings. I sometimes like to game on my Linux box (even though I keep Windows around for gaming) but I have issues with games losing full screen or crashing out when compiz is running.

So, does anyone know of a way I can:

a) save a profile of compiz setting so I can quickly restore my settings when I want to turn compiz back on

b) a way to have two desktop configurations (possibly different kernels or desktop types), one for gaming and another for development and general use

I appreciate any suggestions.

I too am having this problem, even though I have the icon in the notificationa area.
The icon is helpful though... open synaptic package manager (system/administration/synaptic package manager). click search, type- fusion-icon, when it comes up, put a check mark in the box next to it and then click apply (green check mark). The icon does not load into the notification area after restart...have to go to applications/system tools/compiz fusion icon. When one clicks on that, it will load the icon into the notification area.

Even with this icon, compiz will not save current settings, nor will the icon restore them. Anytime the system is restarted I lose the settings. Also having trouble saving profiles that work. I can save them, but when using them to restore, they don't work. Have emerald installed as well and it too will not load when starting ubuntu. Have put a command into sessions preferences as follows: command: emerald--replace
But does not seem to have worked. Might have to add something to sessions preferences for fusion as well.
Been looking and haven't found any help with this, many people with same problem, but can't find anything that works.

R U a Nissan Titan Owner?
R U on titantalk ?
-------------------------
Added/Update:

Forget the emerald command in sessions preferences...

After you install the fusion icon, open sessions preferences and add:

Name: Compiz Fusion
Command: fusion-icon
...(no spaces with dash)

This will start both compiz fusion & emerald (if you have emerald too) when starting ubuntu, while also adding the icon to the taskbar notification area.

See next post about fix for saving compiz profiles...

---

### Post by ft23002 on 2008-09-27
**Update:**
Changed the "backend" to "Flat-file Configuration Backend" and I now can at least save profiles & have them restore properly. Suggest trying the same:
Open Compiz settings manager, click on "preferences" change backend to above. (this will result in all settings being lost and reverting to defualt.) Now with the new backend, create a new profile, make all the custom settings you want, then go back to preferences and click "export" and save your profile. If you'd like to make different profiles to save, make sure you create a new profile before making the changes. Create new profile, make changes, then save. Do this for every profile that you wish to have different custom settings for. Hope this helps.

---

### Post by hbk710 on 2010-11-08
hi, i was looking for the same thing and eventually found this website.

[http://forlong.blogage.de/en/entries/pages/Compiz-Switch#comments](http://forlong.blogage.de/en/entries/pages/Compiz-Switch#comments) 

it will allow for a switch to turn compiz on and off, and if you want any screenlets as well, you need to run a extra easy code on 10.04 lucid lynx or newer but works fairly well. it takes a second or two to switch but works fine so far. hope this helps.

---

