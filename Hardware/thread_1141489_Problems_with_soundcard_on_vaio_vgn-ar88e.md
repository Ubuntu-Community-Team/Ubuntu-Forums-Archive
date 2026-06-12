---
title: "Problems with soundcard on vaio vgn-ar88e"
date: 2009-04-28
forum: Hardware
---

### Post by revolution3d on 2009-04-28
Hi everyone!!

   I have a problems to find correct drivers for my sound card. I'm using sony vaio vgn-ar88e and ubuntu 9.04. Does anybody know where I could look for the drivers?

   Many thanks

  Michal

---

### Post by shatterblast on 2009-04-28
The [Medibuntu]("http://www.medibuntu.org") non-free repository is suppose to have firmware drivers available that may help.

Also if that doesn't help, I'm not sure if switching all your settings to OSS might help.  You might check the following to see if it even recognizes something compatible:

System -> Preferences -> Sound

---

### Post by revolution3d on 2009-04-28
thank you for help but it seems that in my case it is more a problem with drivers for the sounds card because the sound from laptop's build in speakers works. It is only problem to plug in phones or outside speakers through speakers in-put. I checked on windows everything works fine so it must be drivers.

---

### Post by shatterblast on 2009-04-28
I think I understand.  Your issue might be which device is the default output.  If that is the case, you might need to still go to the Sound window under Preferences.  Some computers for some reason have the "headset" portion selected as the primary.  If true in your case, you will need to test the different options available under Sound until you can properly hear noise from your computer's built-in speakers.

You will also need to adjust the Volume control.  Coincidentally if you click on its icon, you should see a button that says just that:  Volume Control.  If you do that, you should notice a window come up with various volume controls pop up.  Notice the Device item listed at its top.  This too will need adjusting to match what you select in the Sound window.

---

