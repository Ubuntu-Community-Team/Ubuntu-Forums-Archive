---
title: "Laptop with Geforce"
date: 2008-07-01
forum: Hardware
---

### Post by kaldor on 2008-07-01
I have a new laptop and it has a Geforce 8400 graphics card. I can't stand using vista, it doesn't seem to want to patch quake 4 for me. So the problem here on Ubuntu is that the Geforce card doesn't seem to want to activate. I can see it in my drivers, but it won't work.


How can I fix this? I know quake 3 and 4 are native on Linux, and I want to be able to play them on Linux instead of Windows.

---

### Post by jualin on 2008-07-01
Post the results of > lspci

---

### Post by kaldor on 2008-07-01
> **jualin said:**
> Post the results of

Sorry, kind of new to Linux. What do you mean?

---

### Post by jualin on 2008-07-01
Ok, I am sorry about that pal. Go to Accesories, Terminal and type > lspci whatever you get copy and paste it so we can see it. The "lspci" command will give a list (ls) of all the PCI (slots where most hardware is connected) devices that your computer has. You can also use > lshw to give you a more detailed list of your hardware (hw). Hope this helps!

---

### Post by phidia on 2008-07-01
There is a useful [guide here]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6") for installing nvidia. It does require using commandline but if other methods fail you can try that.

---

### Post by jualin on 2008-07-01
Also you can try a shorcut for installing most Nvidia Video Card Drivers. The name of the package that you need to get is "envy-ng". You can get the package from Synaptic Package Manager or by simply typing > sudo apt-get install envyng-gtk. Then just open up envy and let Envy do its job. If everything is successful the drivers should be working after a reboot.

---

