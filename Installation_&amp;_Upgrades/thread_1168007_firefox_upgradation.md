---
title: "firefox upgradation"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by orky7 on 2009-05-23
hi. i just now upgraded my firefox in ubuntu9.04 from the default one to the one we get from the mozilla website i have done it properly as stated in the ubuntu website ([https://help.ubuntu.com/community/FirefoxNewVersion).every](https://help.ubuntu.com/community/FirefoxNewVersion).every) thing is working fine except for the flash.In my previous browser flash was working fine.but in the new one if i look into the plugin tab it shows that flash player is installed.so what to do now install a new flash player(but i have it already) or some other way.

---

### Post by ALIENDUDE5300 on 2009-05-23
> **orky7 said:**
> hi. i just now upgraded my firefox in ubuntu9.04 from the default one to the one we get from the mozilla website i have done it properly as stated in the ubuntu website ([https://help.ubuntu.com/community/FirefoxNewVersion).every](https://help.ubuntu.com/community/FirefoxNewVersion).every) thing is working fine except for the flash.In my previous browser flash was working fine.but in the new one if i look into the plugin tab it shows that flash player is installed.so what to do now install a new flash player(but i have it already) or some other way.

Try the following:
```
sudo apt-get remove adobe-flashplugin
```
And then download and install flash from [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

---

