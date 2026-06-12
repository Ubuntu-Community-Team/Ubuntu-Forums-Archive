---
title: "Google Earth fault after install"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by rannable on 2009-07-28
Hey everyone, 

I have a Dell E5500 with 4gb ram and running Ubuntu 9.04 x64.

I installed Google Earth using the .bin file and it installed without any issues but when I open it I can't find our planet! I have it on no visual effects because when i have it on Normal or Extra the Google Earth application just flickers like mad.

The version is 4.3.7284.3916 (beta) and i have had no error messages and have rebooted several times and tried reinstalling it. 

I followed the setup guide at [http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/) and cant think what else to do?

Thanks!
Rob

---

### Post by oboedad55 on 2009-09-22
> **rannable said:**
> Hey everyone, 

I have a Dell E5500 with 4gb ram and running Ubuntu 9.04 x64.

I installed Google Earth using the .bin file and it installed without any issues but when I open it I can't find our planet! I have it on no visual effects because when i have it on Normal or Extra the Google Earth application just flickers like mad.

The version is 4.3.7284.3916 (beta) and i have had no error messages and have rebooted several times and tried reinstalling it. 

I followed the setup guide at [http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/) and cant think what else to do?

Thanks!
Rob

Whose planet did you find?!?

---

### Post by unsalmd on 2009-10-07
@oboedad55  hi ho ho too funny 
guy ask for help .. you are kidding ..
I have same problem . 
&#305; install google earth 5 from bin file .Black screen no other planet or star can be seen.
Any solution will be welcome

---

### Post by bhaverkamp on 2009-10-07
Did you start google-earth from the installer right after installing. If so this is the problem. The user directories for google-earth in .google-earth have root only access. There is a wiki on this somewhere. You need to remove the directory and then restart google-earth.

---

### Post by oboedad55 on 2009-10-07
> **unsalmd said:**
> @oboedad55  hi ho ho too funny 
guy ask for help .. you are kidding ..
I have same problem . 
&#305; install google earth 5 from bin file .Black screen no other planet or star can be seen.
Any solution will be welcome

I install the medibuntu repos and install google earth that way. Although I think it only includes planet Earth, as its title suggests so if you're from another planet I think you'd find this unfamiliar but educational nonetheless. Be open minded, we're not very advanced, as you'll soon learn, but we have potential, and if we don't destroy ourselves through bombs or destruction of the planet, earth that is, we may have a chance. Be merciful with us!

---

### Post by ijen on 2009-10-13
here maybe the soltuion

sudo chown -R username:username ~/.config/Google
sudo chown -R username:username ~/.googleearth/

---

