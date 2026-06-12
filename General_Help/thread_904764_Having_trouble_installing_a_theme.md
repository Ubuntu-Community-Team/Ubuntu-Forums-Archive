---
title: "Having trouble installing a theme"
date: 2008-08-29
forum: General Help
---

### Post by pedro3005 on 2008-08-29
Im trying to install a theme on ubuntu, and its really hard. The theme is Hardy-Mariux 2.0. I've managed to get the icons going, but thats about it. Cant install the theme. Ive done what it asks, wich is:
> 
	*GTk theme
Install this packages:
§ sudo aptitude install gtk2-engines-murrine
then copy "Hardy-Mariux 2.0" in your /home/.themes directory
Go in System -> Preferences -> Appearance->Customize then select "Hardy-Mariux 2.0" to choose this gtk theme.


But it does not appear the Hardy-Mariux 2.0 option on Customize.. what can i do?:confused:

---

### Post by finer recliner on 2008-08-29
when you open the appearance preferences window (with all your themes), there is an install button at the button. click that button, and locate your theme using that, then click ok.

---

### Post by pedro3005 on 2008-08-29
yes, the theme came with a whole lot bunch of files, and i've tried each one of them, and the only thing i got out of that is the icons working.. im thinking my problem is a little deeper than those common mistakes =/:(

---

### Post by pedro3005 on 2008-08-29
ok solved it.. i just had put the wrong folder in .themes, because theres two folders with the same name. The right folder is the one inside the GDK folder, for whoever got the same issue than me :)

---

