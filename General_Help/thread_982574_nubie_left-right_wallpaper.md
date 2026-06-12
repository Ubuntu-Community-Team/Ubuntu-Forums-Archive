---
title: "nubie left-right wallpaper"
date: 2008-11-14
forum: General Help
---

### Post by mac-i-bear on 2008-11-14
is there a way to have two different wall papers for the left and right desktop screens under 8.04 gnome plain vanilla w/o cosmetic apps ?

---

### Post by mssever on 2008-11-15
> **mac-i-bear said:**
> is there a way to have two different wall papers for the left and right desktop screens under 8.04 gnome plain vanilla w/o cosmetic apps ?

If you're running Compiz (which is the default for many systems), install compizconfig-settings-manager (ccsm) and check out the wallpaper plugin. Note that ccsm is optional. You could edit the gconf settings directly, but using ccsm is much easier.

If you aren't running Compiz, the answer is no--although I think if you search Synaptic you might find something.

---

### Post by mac-i-bear on 2008-11-15
mssever,
the more i ask the less i know - i have ZERO linux knowledge !
how do i know if Compiz is installed
if id not how do i install both - Compiz and ccsm
could you share a command line to do the above
thanks for your  help

---

### Post by komputergeek on 2008-11-15
for gnome use :
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra

for kde :
sudo apt-get install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra

This will install compiz and ccsm and plugins

---

### Post by mssever on 2008-11-15
> **mac-i-bear said:**
> mssever,
the more i ask the less i know - i have ZERO linux knowledge !
how do i know if Compiz is installed
if id not how do i install both - Compiz and ccsm
could you share a command line to do the above
thanks for your  help

Compiz is installed in Hardy unless you explicitly removed it, but it might or might not be enabled. Go to System > Preferences > Appearance > Visual Effects tab. If "None" is selected, you're using Metacity, not Compiz. Otherwise, you're using Compiz. It won't hurt anything to experiment with those options. If your hardware doesn't work with Compiz, then trying to select one of the Compiz options will fail and you'll be back where you started.

---

### Post by mac-i-bear on 2008-11-15
komputergeek & mssever,
i managed to install ccsm and moved to /usr/share/backgrounds the pictures i would like to have as left and right desk wallpapers but i cannot see where to set them up !
if i right click on desktop what ever i set is set for BOTH sides
?????

---

### Post by mssever on 2008-11-16
> **mac-i-bear said:**
> komputergeek & mssever,
i managed to install ccsm and moved to /usr/share/backgrounds the pictures i would like to have as left and right desk wallpapers but i cannot see where to set them up !
if i right click on desktop what ever i set is set for BOTH sides
?????
Run ccsm and click the "Wallpaper" button. Use the New button to add wallpapers, and be sure to check the box to enable the plugin.

---

### Post by mac-i-bear on 2008-11-16
mssever,
we may be on the same book but different page
i go to system->preferences->advance desktop effects settings and this gui CompizConfig Setting Manager comes on
it has 10 categories:all, general,accessibility, desktop,effects,extras,  imaage loading, utility, windows management and uncategorized

desktop has some plug ins on but i do not see wallpaper bottom
???

---

### Post by mssever on 2008-11-16
> **mac-i-bear said:**
> mssever,
we may be on the same book but different page
i go to system->preferences->advance desktop effects settings and this gui CompizConfig Setting Manager comes on
it has 10 categories:all, general,accessibility, desktop,effects,extras,  imaage loading, utility, windows management and uncategorized

desktop has some plug ins on but i do not see wallpaper bottom
???

D'oh. I see you're running Hardy, but my instructions were for Intrepid. The wallpaper plugin is new in Intrepid. In Hardy, there's also a way to set the wallpaper in ccsm, but since I no longer run Hardy, I can't tell you where in ccsm it is. You'll just have to go exploring. The good news is that in my experience Hardy's version of Compiz works a lot better than the version in Intrepid. In Intrepid, I now have to disable multiple wallpapers, which worked fine in Hardy. Probably the new version of Compiz doesn't like my hardware.

---

### Post by mac-i-bear on 2008-11-17
thank you anyway
i will keep looking....

---

